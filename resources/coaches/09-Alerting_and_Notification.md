---
ms.openlocfilehash: c6694e2c6cf365c501015b03c02036be37ce1e1d
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813696"
---
# <a name="alerting-and-notification"></a>アラートと通知

## <a name="progress-diagram"></a>進行状況ダイアグラム

![アラートと通知の進行状況ダイアグラム](https://serverlessoh.azureedge.net/public/alerting-and-notification-progress-diagram.jpg)

## <a name="happy-path"></a>ハッピー パス

* 既存の CreateRating 関数を編集し、次のいずれかの方法で userNotes を配置します。
    * Text Analytics Cognitive Services API 呼び出し
    * Python 関数を使用した [TextBlob](https://textblob.readthedocs.io/en/dev/index.html#) ライブラリ
* 悪いレビューがあるたびに関数と同じ App Insights インスタンスに書き込むためのカスタム テレメトリを作成します
* Application Insights のログ アラート機能を使用して、しきい値に達したときにアラートと電子メールを生成します

[方法 - 感情分析](https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-sentiment-analysis?tabs=version-3)  

## <a name="why-cognitive-services-azure-functions-azure-logic-apps-and-application-insights"></a>Cognitive Services、Azure Functions、Azure Logic Apps、および Application Insights を使用する理由

### <a name="cognitive-services---text-analyticssentiment-analysis"></a>Cognitive Services - Text Analytics、感情分析

* 自然言語処理 (NLP) を使用して非構造化テキストを解析し、顧客の評価をより深く理解します
* キー フレーズを識別し、用語を分類し、複数の言語を横断して評価します

### <a name="azure-functions"></a>Azure Functions

* Azure 関数を使用すると、チームで記述するコードと保守するインフラストラクチャが少なくなり、コストを節約できます。
* Azure 関数は、軽量でスタンドアロンです。  関数を使用すると、モノリシック アプリケーションを簡単に分割し、リード時間またはサイクル時間を短縮できます。これにより、チームは、コードをより迅速かつ効率的に運用環境に移行できます。

### <a name="azure-logic-apps"></a>Azure Logic Apps

* ロジック アプリは、200 個を超えるコネクタを使用して、ほとんど何にでも接続できます。ロジック アプリは、任意のタイミングで、スケジュールに従って、またはイベントへの応答としてトリガーできます
* ロジック アプリは簡単に使用できます。ロジック アプリのワークフローは強力なドラッグ アンド ドロップ エディター アプローチを使用してごくわずかの構成で作成できるため、チームは複雑なロジックをすばやく簡単に調整できます

### <a name="application-insights"></a>Application Insights  

* アラートを使用すると、関係者にイベントや潜在的なサービスのダウンタイムを迅速に通知できます
* ライブ アプリケーションの監視に使用される拡張可能なアプリケーション パフォーマンス管理 (APM) サービス
* パフォーマンスの異常を自動的に検出し、強力な分析ツールを活用して、パフォーマンスと使いやすさを継続的に改善します
