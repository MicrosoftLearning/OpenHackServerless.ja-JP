---
ms.openlocfilehash: 902d75e6c4dc819c0bcfbbbbb5b5acbcf1d8d488
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813707"
---
# <a name="high-availability"></a>高可用性

## <a name="progress-diagram"></a>進行状況ダイアグラム

![最終的な進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/final-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

* マルチ マスター、または少なくとも 2 番目のリージョンへのセカンダリ読み取りを含む geo レプリケーションを使用して CosmosDB を編集します
* 同じ関数コードを 2 番目のリージョンにデプロイします
* その前面に Traffic Manager を追加します

## <a name="why-cosmos-db"></a>Cosmos DB を使用する理由

### <a name="cosmos-db"></a>Cosmos DB

* 拡張性が高くグローバルに分散されるため、高可用性、スループット、冗長性が実現されます
* 応答時間がミリ秒単位と短いため、アプリケーションですばやく情報を取得して応答し、正確な結果を維持しながらユーザーの満足度を高めることができます
