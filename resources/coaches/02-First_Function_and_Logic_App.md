---
ms.openlocfilehash: 4e45123a01531ded30f70c3a32249b252149cab4
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813691"
---
# <a name="create-your-first-serverless-function--workflow"></a>初めてのサーバーレス関数とワークフローを作成する

## <a name="happy-path"></a>ハッピー パス

これらの 3 つの指示のいずれか 1 つを使用します。

* 最新の Visual Studio と最新の Functions および Webjobs 拡張機能を使用して関数アプリと関数を作成し、ローカルでテストし、Azure に発行します

* 最新の Visual Studio Code と最新の Azure Functions 拡張機能を使用して関数アプリと関数を作成し、ローカルでテストし、Azure に発行します

* (Java または Python の) 好みの IDE と最新の Azure Functions Core Tools および Azure CLI を使用して関数アプリと関数を作成し、ローカルでテストし、Azure に発行します

## <a name="python-developer-notes"></a>Python 開発者向けメモ

* VS Code ユーザーは [Functions 拡張機能](https://docs.microsoft.com/azure/python/tutorial-vs-code-serverless-python-05)を使用して関数アプリをデプロイできますが、そうするとデプロイ中に行われていることを開発者が把握できなくなります。 開発者には、[Azure Functions Core Tools](https://docs.microsoft.com/azure/azure-functions/functions-reference-python#publishing-to-azure) を使用してデプロイするように促してください。 これにより、クラウドで実行されているリモート ビルドの可視性が向上します。

## <a name="coaches-notes"></a>コーチ向けメモ

* これは、個人で行う必要がある唯一の課題です。他の課題では、すべて共同作業を行うか、サブチームに分割してレッスンを共有し、後で作業をマージする必要があります

* チームにインフラストラクチャ フォーカス メンバーが含まれている場合は、この間、IaC ツールと Azure 関数およびロジック アプリのデプロイに集中する必要があります。 これにより、後の課題でチームのアプリ開発者とインフラストラクチャ フォーカス メンバーの両方を連携させるのに役立つ道筋ができます。

* 設定プロセス (Visual Studio、VS Code、依存関係など) 全般、および Functions アプリおよび Logic Apps に関する質問について、各チーム メンバーをサポートおよびガイドします

* ある程度の時間をかけて、この課題が主にレベル設定 (基本的には課題 0) に関するものであることを説明します。さらに、Functions および Logic Apps の概要と、残りの課題をとおしてサーバーレスのビジネスと技術のより良いアイデアが得られることを説明します

* 結果が適切であること、GET を使用して関数を呼び出し、POST を使用してロジック アプリを呼び出していることを確認します

* 関数をローカルで作成するためのさまざまなオプションについて自由に説明し、C# や Node 以外 (Java や Python など) を実際に試す要望がない場合は、可能であれば VS Code および VS を紹介します

* 最新バージョンの VS と拡張機能を使用していることを確認します

* VS Code で関数ランタイムまたは .NET Core の適切なバージョンを使用していない場合は注意が必要です (すべての .NET コアをアンインストールしてから最新の SDK 修正プログラムをインストールすると問題は解決します。さらに、最新のランタイムもインストールします)
* VS Code で Logic Apps 拡張機能を使用する場合は、デザイナーが _読み取り専用_ であることに注意してください。  VS Code の[拡張機能のページ](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-logicapps)に、デザイナーが読み取り専用であることが示されています (アニメーション GIF)。  完全なグラフィカル編集エクスペリエンスを得るには、Visual Studio または Azure portal を使用します。

* chocolatey を使用して関数コア ツールをインストールする場合は注意が必要です。バグのある 32 ビット バージョンがインストールされるようです

* Functions で Node を使用する場合は、関数のアプリ設定で Node バージョンが 8.4.0 以上に設定されていることを確認してください。  これが現在の Node バージョン (v12 など) と一致することが理想的です。

* 良好に動作するランタイム パッケージと Nuget パッケージ:

    製品 | バージョン
    ------- | -------
    Visual Studio | 16.3.2
    Functions および VS 用 WebJobs 拡張機能 | V15.0.40502
    .Net Core SDK | [.Net Core](https://dotnet.microsoft.com/download/visual-studio-sdks)
    Functions Core Tools | 2.7.1633
    その他の NuGet ライブラリ | ...
    Microsoft.ApplicationInsights | 2.11.0
    Microsoft.NET.Sdk.Functions | 1.0.28
    CsvHelper | 12.1.2
    Microsoft.Azure.WebJobs.Extension.CosmosDB | 3.0.3
    Microsoft.Azure.WebJobs.Extensions.DurableTask | 1.8.2
    Microsoft.Azure.WebJobs.Extensions.EventHubs | 3.0.3

## <a name="why-azure-functions-and-logic-apps"></a>Azure Functions と Logic Apps を使用する理由

### <a name="azure-functions"></a>Azure Functions

* Azure 関数を使用すると、チームで記述するコードと保守するインフラストラクチャが少なくなり、コストを節約できます。
* Azure 関数は、軽量でスタンドアロンです。  関数を使用すると、モノリシック アプリケーションを簡単に分割し、リード時間またはサイクル時間を短縮できます。これにより、チームは、コードをより迅速かつ効率的に運用環境に移行できます。
* Azure 関数では、[カスタム Docker コンテナー](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-function-linux-custom-image)を利用して、組み込みイメージでは提供されない特定の言語バージョンまたは依存関係の要件を満たすことができます。

    > **追加情報**: Azure Functions サービスは 2 つの主要コンポーネントで構成されています。ランタイムとスケール コントローラーです。 Functions ランタイムでは、ご自分のコードを実行します。 ランタイムには、関数の実行をトリガー、ログ、および管理する方法のロジックが含まれています。 Azure Functions ランタイムは、どこでも実行できます。 もう 1 つのコンポーネントは、スケール コントローラーです。 スケール コントローラーによって、関数をターゲットにしているイベントの割合が監視され、アプリを実行しているインスタンスの数がプロアクティブにスケーリングされます。

* どのような関数アプリも [KEDA を実行している Kubernetes クラスター](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)にデプロイできます

### <a name="azure-logic-apps"></a>Azure Logic Apps

* ロジック アプリは、200 個を超えるコネクタを使用して、ほとんど何にでも接続できます。ロジック アプリは、任意のタイミングで、スケジュールに従って、またはイベントへの応答としてトリガーできます
* ロジック アプリは簡単に使用できます。ロジック アプリのワークフローは強力なドラッグ アンド ドロップ エディター アプローチを使用してごくわずかの構成で作成できるため、チームは複雑なロジックをすばやく簡単に調整できます

## <a name="infrastruture-notes"></a>インフラストラクチャに関するメモ

* 多くの Azure クイックスタート テンプレートでは、GitHub リポジトリに Bicep バージョンが含まれています。
* この作業は、主要な課題コンテンツを達成するための開発作業と並列に行うことを強くお勧めします。 ボーナス コンテンツを順番に実行すると、チームが最小限の課題を完了できなくなる可能性があります。
