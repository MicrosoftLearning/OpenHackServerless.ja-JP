---
ms.openlocfilehash: 57d978f77fe641da42b91c80c1a365085e522427
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813699"
---
# <a name="batch-file-processing-solution"></a>バッチ ファイル処理ソリューション

このサンプルでは、次の方法でバッチ ファイル処理の課題を解決する方法を示します。

## <a name="event-grid-subscription"></a>Event Grid サブスクリプション

Event Grid サブスクリプションは、ストレージ アカウントの BLOB 作成イベントで "GridTrigger.java" 関数をトリガーするために使用されます。 この関数は、ファイルのパスを解析し、この情報を使用して 2 つの処理を実行します。

1. パーティション キーがパスの最初の部分と等しく、行キーがパスの 2 番目の部分と等しいストレージ テーブル レコードを作成します。
2. テーブルに格納されているのと同じデータを使用して、同じストレージ アカウントの "受信" キュー内にストレージ キュー メッセージを作成します。

## <a name="received-queue-message"></a>受信されたキュー メッセージ

ReceivedQueueTrigger.java は、前に作成したキュー メッセージからトリガーされます。 この関数は、前の関数で使用されたテーブルに対してクエリを実行して、受信したメッセージと同じパーティション キーのファイルが 3 つあるかどうかを確認します。 ある場合は、3 つのファイルの詳細を含むメッセージが、"バッチ" キューに作成されます。

## <a name="batched-queue-message"></a>バッチ キュー メッセージ

BatchQueueTrigger.java 関数は、前に作成したメッセージからトリガーされます。 BLOB 入力バインディングを使用して、3 つの BLOB ファイルからデータを読み取り、コンテンツを json 形式に変換します。
