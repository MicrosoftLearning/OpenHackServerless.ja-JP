---
ms.openlocfilehash: 878b8fc0072cee4d28adca8898cf38c90ba06b90
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813697"
---
# <a name="finish-the-ice-cream-ratings-api"></a>Ice Cream Ratings API を完成させる

## <a name="progress-diagram"></a>進行状況ダイアグラム

![Ratings API の進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/ratings-api-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

* GitHub、Azure DevOps、またはその他の Git ソースにコードを配置します
* 作成して Azure 関数アプリに継続的にデプロイします
* Azure Functions を Cosmos DB と共に使用し、関数の入力バインディングと出力バインディングを使用します
* バインディングに関連付けられていない CosmosDB クライアント SDK も使用できます
* 特に Node の場合、CosmosDB Mongo API + Mongoose が良好に動作します

## <a name="coaches-notes"></a>コーチ向けメモ

* この課題の終わりまでに、チームが共同作業のための準備と連携のための計画を完了していることを確認してください。 つまり、"どのように共同作業を行い、すべてのコードをどこに配置するか" ということです
* Visual Studio Live Share を有効にしてみてください
* チームに、チームを分ける方法と再度合流する方法について話し合ってもらいます
* 課題で提供されているサンプル Web サイトを使用して CreateRating 関数をテストしてください。これにより、後の課題で使用する適切な JSON 形式を受け取ることを確認できます
* 従量課金プランを使用するよう案内します (実際のサーバーレス)
* 拡張機能をインストールするときに "cannot find dotnet-add (dotnet-add が見つかりません)" エラーが発生する場合は、.NET Core のバージョンが古いことに原因があります。 .NET の最新バージョンをインストールすると、問題は解決します。
* GetRatings で userId をルートに配置し、これを SQLQuery パラメーターで使用する場合 (クエリ文字列で使用すると機能しません)
* Cosmos DB では、コンテナーの作成時にパーティション キーを設定する必要があります。 コーチとして、パーティション キーの[選択](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview#choose-partitionkey)と、パーティション キーがクエリに与える影響についてチームと話し合います。 たとえば、この課題の潜在的なパーティション キーは ```userId``` または ```productId``` です。
* レビューの送信に使用するユーザー:

ユーザー ID | [ユーザー名] | [名前]
--------| --------- | ---------
cc5581ff-6be1-4418-a8d8-55a29c24b995 | garry.thornburg | Garry Thornburg
6dd3bb49-a5be-41ca-9dac-3b995450f2db | kayla.cobb | Kayla Cobb
ed414804-ed3d-4ec3-a283-f94ee86f3e23 | edna.waters | Edna Waters
d1f80b77-040f-4ec8-a833-90b18da70337 | chester.furlong | Chester Furlong
cc20a6fb-a91f-4192-874d-132493685376 | doreen.riddle | Doreen Riddle

### <a name="storage-notes"></a>ストレージに関するメモ

* CosmosDb
    * チームがコレクションのパーティション キー要件について話し合っていることを確認します。
    * バインディングの id プロパティの使用は、パーティション キー プロパティを使用しないと機能しません。 GetRating 関数では、SQL クエリを使用する必要があります

### <a name="node-notes"></a>Node に関するメモ

* WEBSITE_NODE_DEFAULT_VERSION アプリの設定を確認してください。 使用している関数アプリのバージョンによっては、ポータルの Node バージョンを更新する必要がある場合があります。 サポートされている言語ランタイムについては、[言語の表](https://docs.microsoft.com/azure/azure-functions/functions-versions#languages)を参照してください。
* Visual Studio でデバッグを有効にするには、ローカル設定ファイルに "NODE_OPTIONS": "--inspect=5858" を追加する必要があります

### <a name="devops-notes"></a>DevOps に関するメモ

* チームは、Opgility ポータルで提供された資格情報を使用して AzDo アカウントを作成できます
* ソース コードに Azure DevOps を使用していて Functions デプロイ オプションからそれに接続する場合は、自分のログインがその所有者となっている組織から構成する必要があります。 デプロイ構成は、これを行うために[こちらの手順](https://docs.microsoft.com/azure/devops/organizations/accounts/create-organization?view=azure-devops)を参照します。
    * Linux アプリ サービス プランでは Kudu サービスを利用できないため、このオプションをデプロイ構成に使用することはできません
* App Service プランの選択に基づいて使用可能なデプロイ オプションについては、「[デプロイ テクノロジの可用性](https://docs.microsoft.com/azure/azure-functions/functions-deployment-technologies#deployment-technology-availability)」を参照してください。
* Mac および Linux ユーザーは、Azure にストレージ アカウントを作成してローカル開発環境を接続するか、Azurite v2 をインストールする必要があります。 [Azurite v3 は機能しません](https://github.com/mydiemho/blob-trigger-sample)。Windows ユーザーは、ストレージ エミュレーターを使用できます。

## <a name="why-devops-and-azure-functions"></a>DevOps と Azure Functions を使用する理由

* DevOps は、手動によるコードのデプロイとリリースを自動化して、人為的なミスを最小限に抑えるために使用されます
* Azure Functions を使用すると、ホスティング環境全体をプロビジョニングすることなくコードを実行できます

## <a name="infrastruture-notes"></a>インフラストラクチャに関するメモ

* 多くの Azure クイックスタート テンプレートでは、GitHub リポジトリに Bicep バージョンが含まれています。
