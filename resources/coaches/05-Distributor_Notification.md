---
ms.openlocfilehash: 0f878ef1c7fc3cce02a829993ac3204ba0c498e2
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813666"
---
# <a name="notify-all-distributors-of-the-new-ice-cream-line"></a>新しいアイス クリーム ラインについてすべてのディストリビューターに通知する

## <a name="progress-diagram"></a>進行状況ダイアグラム

![ディストリビューター通知の進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/distributor-notification-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

これらのオプションの 1 つ

* Logic Apps と Common Data Service および Office 365 電子メール コネクタ、および HTML テーブルの作成アクションまたは変数アクションを使用します  

* Logic Apps を Azure Functions と共に使用します (Common Data Service および Office 365 電子メール コネクタ用の LA、および製品の一覧を取得して HTML を生成するための Functions)  

## <a name="coaches-notes"></a>コーチ向けメモ

* CRM 連絡先では、そのメール アドレスを 2 つのメール アドレスに設定しています。あなたは、これを使用して、電子メールが送信されたことを検証することができます。 検証するには、[Office.com](https://outlook.office.com) に次のアカウントを使用してログインします: OHCoach1@microsoftopenhack.onmicrosoft.com、パス: OpenHackCoach1、ユーザー: OHCoach2@microsoftopenhack.onmicrosoft.com、パス: OpenHackCoach2。

* ロジック アプリを使用する場合、電子メールを処理するためのコネクタは `Microsoft Dataverse Connector` です。これにより、アクションが (legacy) として一覧表示されます: `List rows (legacy)`。  

* Dataverse コネクタにサインインするときに Logic Apps で "新しい接続を追加" し、課題に従って資格情報を入力することを忘れないでください。  正しく入力すると、オプションの一覧が表示されます。  foreach コントロールを使用して、その一覧を中心にロジック アプリを構築します。

* dataverse コネクタと Office 365 Outlook 接続の両方に同じ接続を使用します

* Postman を使用して、通常のワークフローの外部で接続とデータをテストするロジック アプリをトリガーします。   コンテンツ タイプのヘッダーを必ず `'Content-Type' : 'application/json'` に設定してください  

* 完全なソリューションを使用せずにロジック アプリを実行し、各アクションの入出力を確認して、Common Data Service コネクタの応答から電子メールを抽出する方法を理解できるようにサポートします。  ロジック アプリ コネクタを使用して foreach ループを簡単に作成し、各連絡先の `Email` プロパティを選択します。

   >注: ソリューションは ~/solutions/codeless/Distributor_Notification/logicapp.json で入手できます

* [電子メールの送信 (v2) アクション](https://docs.microsoft.com/en-us/connectors/office365connector/#send-an-email-(v2))についてのサポートをチームが必要としている場合は、Office 365 Outlook コネクタを使用して電子メールを送信するようにチームに指示します  

* 参加者は、ロジック アプリ変数を使用して電子メールのコンテンツを作成し、その変数を電子メールの本文に挿入する必要があります。  簡単にするために、電子メール本文の全体を構成された変数にすることもできます。

* Logic Apps で Azure Functions アクションを使用しているときに "Swagger をフェッチできませんでした" と表示された場合は、関数アプリに戻って CORS 設定に移動し、すべてのエントリを削除した後、`*` のエントリを追加します。  

* Logic Apps と API Management コネクタには既知のバグがあります。これは、API Management の **Consumption** レベルを使用している場合に、コネクタでアクションの一覧を取得できないというものです。  詳細については、[こちら](https://stackoverflow.microsoft.com/questions/169694/support-for-consumption-tier-apim-instances-in-the-logic-app-connector )と[こちら](https://social.msdn.microsoft.com/Forums/890b2235-ff66-4186-9aa3-b16909dc81a1/logic-apps-no-showing-azure-api-management-apis?forum=azureapimgmt)を参照してください。

* Microsoft.EventGrid リソース プロバイダーが参加者サブスクリプションに登録されていないことを示すエラーが発生した場合は、[Event Grid をリソース プロバイダーとして登録する](https://docs.microsoft.com/en-us/azure/event-grid/custom-event-quickstart-portal)方法に関する記事の手順に従って EventGrid リソース プロバイダーを登録してください

## <a name="why-azure-logic-apps"></a>Azure Logic Apps を使用する理由

* ロジック アプリは簡単に使用できます。ロジック アプリのワークフローは強力なドラッグ アンド ドロップ エディター アプローチを使用してごくわずかの構成で作成できるため、チームは複雑なロジックをすばやく簡単に調整できます
* ロジック アプリは、保存にかかるコストが非常に少なく、非常にコスト効率に優れた消費ベースのアプローチで何百回も実行できます  

## <a name="infrastructure-as-code"></a>コードとしてのインフラストラクチャ

* この課題に関する IaC の具体的な目標や要件はありません。ただし、チームで調査していれば、ロジック アプリ コネクタをコードで簡単にできないことがわかります。 コネクタを作成する Terraform リソースはありません。ただし、Bicep と ARM の例が Microsoft ドキュメントの外部にあり、これがソリューションにつながる可能性があります。

[ロジック ワークフロー用の ARM](https://docs.microsoft.com/en-us/azure/templates/microsoft.logic/workflows?tabs=bicep)
[ARM テンプレートでロジック アプリ コネクタを作成する方法](https://vincentlauzon.com/2017/10/28/how-to-create-a-logic-app-connector-in-an-arm-template/)
[ARM および CI/CD でロジック アプリ カスタム コネクタを使用する方法 ](https://mikaelsand.se/2020/11/how-to-use-logic-apps-custom-connectors-with-arm-and-ci-cd/)
[ARM テンプレート内でロジック アプリと o365 コネクタをデプロイする方法](https://stackoverflow.com/questions/60703570/how-to-deploy-logic-app-with-o365-connector-within-arm-template)
