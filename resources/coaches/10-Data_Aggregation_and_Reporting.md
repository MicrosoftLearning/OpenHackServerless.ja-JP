---
ms.openlocfilehash: 5109c8ffa5df36a921e6c02108b2b3a59c877914
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813674"
---
# <a name="putting-it-all-together"></a>まとめ

## <a name="progress-diagram"></a>進行状況ダイアグラム

![最終的な進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/final-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

* 変更フィードと関数を使用して新しいイベント ハブに転送するか、Event Hub への新しい 2 番目の出力バインドを使用して CreateRating 関数を変更します
* 元の POS Event Hubs と新しいイベント ハブを入力として使用して、Stream Analytics ソリューションを作成します
* 1 つ以上の Stream Insight クエリを記述し、Cosmos または PowerBI に出力します。 例:

```sql
WITH
Products AS (
    Select *
    from testdata as t
    CROSS APPLY GetArrayElements(t.items) AS flat
)

SELECT System.TimeStamp AS WindowEnd,
        T.header.locationname,
        flat.ArrayValue.productname,
        sum(flat.ArrayValue.totalcost) as totalCost,
        count(1) as countUnits
INTO prodPowerBi
FROM Products
GROUP BY flat.ArrayValue.productname, T.header.locationname, TumblingWindow(minute, 5)
```

## <a name="why-azure-functions-and-stream-analytics"></a>Azure Functions と Stream Analytics を使用する理由

### <a name="azure-functions"></a>Azure Functions

* Azure 関数を使用すると、チームで記述するコードと保守するインフラストラクチャが少なくなり、コストを節約できます。
* Azure 関数は、軽量でスタンドアロンです。  関数を使用すると、モノリシック アプリケーションを簡単に分割し、リード時間またはサイクル時間を短縮できます。これにより、チームは、コードをより迅速かつ効率的に運用環境に移行できます。

### <a name="azure-stream-analytics"></a>Azure Stream Analytics

* データを変換およびフィルター処理するクエリを使用して、エンドツーエンドの分析パイプラインを簡単に構築できます
* 組み込みの機械学習機能により、高度なソリューションが提供されます
