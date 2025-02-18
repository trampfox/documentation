---
description: クエリされたログをトランザクションにグループ化します。
further_reading:
- link: logs/explorer/
  tag: Documentation
  text: ログエクスプローラーについて
- link: logs/explorer/analytics
  tag: Documentation
  text: ログの分析方法
title: ログをトランザクションにグループ化する
---

## 概要

トランザクションは、ユーザーセッションや複数のマイクロサービス間で処理されるリクエストなど、一連のイベントのインスタンスに従ってインデックス化されたログを集計します。

トランザクションの集計は、クエリに一致するログだけでなく、関連するトランザクションに属するすべてのログも含まれるという意味で、自然なグループの集計とは異なります。

トランザクションに関する以下の情報を利用して、検索クエリーをカスタマイズすることができます。

期間
: トランザクションの最後のログと最初のログのタイムスタンプの差。_このメジャーは自動的に追加されます_。

最大重大度
: トランザクションのログで見つかります。_このメジャーは自動的に追加されます_。

重要な項目の検索
: 文字列値を持つ任意の `facet` について、`count unique`、`latest`、`earliest`、`most frequent` の操作を使用して、特定のログ情報を計算します。

統計の取得
: 任意の `measure` について、`min`、`max`、`avg`、`sum`、`median`、`pc75`、`pc90`、`pc95`、`pc99` の操作を使用して統計情報を計算します。

開始条件と終了条件の設定
: トランザクションの開始と終了を個別のクエリで指定し、トランザクションの境界をカスタマイズできます。

例えば、e コマースサイトでは、カタログ検索、カートに入れる、チェックアウトなどの様々なユーザーアクションのログをグループ化し、`requestId` や `orderId` などの共通の属性を使用して **Transactions** ビューを構築します。

{{< img src="logs/explorer/aggregations_transactions.jpg" alt="ログをトランザクション別に分類して表示するログエクスプローラー" style="width:100%;" >}}

トランザクションは、[リスト集計][1]の視覚化をサポートします。リスト内のトランザクションをクリックすると、トランザクションのサイドパネルが開き、次のことができます。

- そのトランザクション内のすべてのログにアクセスする
- そのトランザクション内の特定のログを検索する

{{< img src="logs/explorer/transactions_side_panel.png" alt="選択したトランザクション内のログを表示するトランザクションログパネル" style="width:80%;" >}}

開始条件または終了条件を使用してトランザクションを定義する場合、リスト内のトランザクショングループをクリックすると、トランザクショングループのサイドパネルが表示され、以下の操作が可能です。

- そのトランザクショングループ内のトランザクションに順番にアクセスする
- 各トランザクション内のすべてのログにアクセスする
- 各トランザクションの統計情報とトランザクショングループ全体の統計情報のサマリーを表示する

{{< img src="logs/explorer/transaction_group_side_panel.png" alt="選択されたグループ内のトランザクションを順番に表示するトランザクショングループパネル" style="width:80%;" >}}

## その他の参考資料

{{< partial name="whats-next/whats-next.html" >}}

[1]: /ja/logs/explorer/visualize/#list-aggregates-of-logs
