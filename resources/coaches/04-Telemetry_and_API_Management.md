---
ms.openlocfilehash: 50b7e0a11a146df5e15ded07704b5120de5b9caa
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813693"
---
# <a name="system-telemetry-and-api-management"></a>システム テレメトリと API Management

## <a name="progress-diagram"></a>進行状況ダイアグラム

![システム テレメトリと API Management の進行状況ダイヤグラム](https://serverlessoh.azureedge.net/public/system-telemetry-and-api-management-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

### <a name="for-telemetry"></a>テレメトリの場合

App Insights を有効にし、App Insights の分析のソリューション ディレクトリに用意されているクエリの作成を実行します。

### <a name="for-api-management"></a>API Management の場合

* API Management のパスに沿って指導するようにします。 活用する必要がある機能は次のとおりです
    * リバース プロキシ
    * Product Groups (製品グループ)
    * レート制限ポリシー
    > チームは、手動テストの制約にレート制限を設定できます。 課題の数値に従っていることを確認します。 当初は制限を加える必要があります。
* チームは、最初に API Management に関数全体をインポートできます。 これは学習目的では問題ありませんが、課題の成功基準をクリアすることはできなくなります。 関数 API を個別にインポートし、適切な製品グループに配置できるよう、チームを指導する必要があります。

## <a name="coaches-notes"></a>コーチ向けメモ

* API Management とプロキシの違いをチームに説明します。
* APIM は、管理者のメールについては、"onmicrosoft.com" ドメインを含むメール アドレスを受け入れません。 チームは、このフィールドで有効なメール アドレスを使用する必要があります。
* 非従量課金ベースの SKU のデプロイにかかる時間を確認させ、デプロイする場合はできるだけ早急にアカウントを作成するように促します。 そうしないと、従量課金 SKU の方がはるかに迅速にデプロイを行うことができ、課題を達成するために必要な機能も含まれている可能性があります。
* インフラストラクチャ参加者の場合は、APIM のすべての設定と構成を IaC に移動することが望ましくない可能性があることを認識します。 IaC が終了し、構成管理が開始される行があいまいになり、組織内のプロセスに大きく依存する可能性があるため、このような意見は制限する必要がある場合があります。 基本的な APIM をデプロイし、さらに詳細に構成してもらうためにアプリケーション チームにデリバリーすることは、許容されるソリューションです。  

## <a name="why-api-management-and-azure-monitor"></a>API Management と Azure Monitor を使用する理由

* API Management は、API 呼び出しをインターセプトし、それらを操作してさまざまなタスク (エンドポイントのセキュリティ保護、調整、監視など) を実現できるファサードまたはインターフェイスです
* Azure Monitor を使用すると、Azure リソースの状態や正常性を視覚化できます
