---
ms.openlocfilehash: 4b47af864a11eb709d6bc2971cc25e0c804666bc
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813675"
---
# <a name="process-pos-sales-events"></a>POS 販売イベントを処理する

## <a name="progress-diagram"></a>進行状況ダイアグラム

![POS 販売イベント処理の進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/process-pos-sales-event-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

* Azure 関数のイベント ハブ トリガー
* バッチを受信するように変更された関数トリガー (C# の string[])
* 要件に一致するように変更された Host.json
* 1 分あたりのロール インスタンス数に関するアプリ分析情報クエリ

## <a name="coaches-notes"></a>コーチ向けメモ

* JavaScript Azure Functions でバッチ受信を有効にするには、"カーディナリティ" を "多" に設定する必要があります

* イベント ハブを登録するために送信する場合、チームは一意のテーブル番号を使用する必要があります。  送信用の API については、[こちら](https://serverlessohmanagementapi.trafficmanager.net/api/definition)を参照してください。  重要なのは、チームのテーブル番号が seattle-table-1 や london-table-8 のように一意の番号であるということです。  これは、チームが前の課題で使用したものと同じテーブル番号である必要があり、テーブルまたはチームごとに一意である必要があります。  さらに、チームがストレージ アカウントの登録に失敗した場合は、イベント ハブが登録されない可能性があります。  ストレージ アカウントが登録されている必要があることを必ず知らせてください。  ストレージ アカウントに対して生成されるトラフィックの量のために、そのステップをスキップまたは延期する人もいるかもしれません (または、ストレージ アカウントを切断することでテーブルの登録が解除され、この Open Hack のフローが中断される場合があります)。

* 関数アプリの ```maxBatchSize``` を 64 に設定し、```prefetchCount``` を 256 に設定した場合の影響について話し合う準備をしてください。  これらの数字について何も特別なことはありません。  これらは出発点です。  参加者は、これらを使用し、パフォーマンスとスケーラビリティを確認する必要があります。 コーチは、エラーや例外の処理など、バッチ内のメッセージを処理する方法について説明する必要があります。  

    関数に関する関連情報:

    * [サンプル host.json ファイル](https://docs.microsoft.com/en-us/azure/azure-functions/functions-host-json)

    * [Host.json - Functions での Event Hubs へのバインド](https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-event-hubs-trigger?tabs=csharp#hostjson-properties)  

        >注: Functions のバージョン 1 で使用される構成は異なります。ただし、これは新しい開発では動作しません

    * [Functions での Event Hubs へのバインド](https://docs.microsoft.com/azure/azure-functions/functions-bindings-event-hubs)

    * [Azure Functions のベスト プラクティス](https://docs.microsoft.com/en-us/azure/azure-functions/functions-best-practices)  

    * [Azure Functions と Event Hubs: スループットの最適化](https://medium.com/@iizotov/azure-functions-and-event-hubs-optimising-for-throughput-549c7acd2b75)  

    * [Azure Event Hubs のイベント プロセッサ ホストについて](https://channel9.msdn.com/Shows/On-NET/Understanding-the-Event-Processor-Host-in-Azure-Event-Hubs)

* 関数アプリを App Service プランではなく従量課金プランで使用することを提案してください (自動スケールを紹介しやすくなります)。 そのような設定になっていない場合は、低スケールアップ単位 (10% CPU など) で App Service プランの自動スケールを設定するよう案内します。

* ブースト モードを有効にする **前に** サーバー数を確認するように参加者に案内します (既定値と関数のスケーリングを確認できます)。

* 特定の関数のアクティブなサーバーの数を取得するには、Application Insights の Live Metrics ビューか、次のような Log Analytics クエリを使用します。

    ```sql
    requests
    | where name == "ProcessSalesEventBatch"
    | summarize count() by cloud_RoleInstance  
    | summarize count()
    ```

* Python 関数アプリを使用している場合、Live Metrics では、関数アプリによってスケールアウトされたサーバーの正しい数が表示 **されません** (常に 1 が表示されます)。 これは[既知の問題](https://github.com/Azure/azure-functions-python-worker/issues/35)です。 代わりに、次のような Log Analytics クエリを使用して、アクティブなインスタンスの数を取得します。

    ```sql
    requests
    | where operation_Name  == ""
    | distinct cloud_RoleInstance
    | count
    ```

* host.json 内の構成を表示して、バッチ数とプリフェッチ数を検証します。

* Cosmos DB を使用する場合は、スループットを処理するのに十分な大きさに RU が設定されていることを確認します (そうでないと、要求が調整される可能性があります)。
    * [Azure Cosmos DB の要求ユニット](https://docs.microsoft.com/azure/cosmos-db/request-units)
    * [Azure Cosmos DB Capacity Planner を使用して RU/秒を見積もる](https://docs.microsoft.com/azure/cosmos-db/estimate-ru-with-capacity-planner)

## <a name="why-event-hub-azure-functions-and-azure-application-insights"></a>Event Hubs、Azure Functions、および Azure Application Insights を使用する理由

### <a name="event-hub"></a>イベント ハブ

* 1 秒あたり数百万件のイベントを受信して処理します
* リアルタイム分析またはバッチ処理またはストレージ アダプターを使用してストアを変換します

### <a name="azure-functions"></a>Azure Functions

* Azure 関数を使用すると、チームで記述するコードと保守するインフラストラクチャを減らすことができるため、コストを節約できます
* Azure 関数は、軽量でスタンドアロンです。  関数を使用すると、モノリシックなアプリケーションを簡単に分割し、リード時間またはサイクル時間を短縮できます。これにより、チームはより迅速かつ効率的にコードを運用環境に移行できます

### <a name="azure-application-insights"></a>Azure Application Insights

* ライブ アプリケーションの監視に使用される拡張可能なアプリケーション パフォーマンス管理 (APM) サービス
* パフォーマンスの異常を自動的に検出し、強力な分析ツールを活用して、パフォーマンスと使いやすさを継続的に改善します
