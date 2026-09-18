# kaichang / kt-git-1

**日々の困りごとを、使えるアプリケーションに。**

毎日薬を飲む人と、その服薬を見守る家族をつなぐアプリ「お薬見守り」を個人開発しています。薬を飲む人がスマートフォンで「飲んだ」と記録すると、離れて暮らす家族も服薬状況を確認できます。

iOSアプリの画面からAPI・データベースまで、使いやすさとデータの整合性を考えながら設計・実装しています。

## 代表作 — お薬見守り

**「今日の薬は飲めたかな？」「薬はまだ足りるかな？」を、家族で確認できるアプリです。**

- **薬を飲む人**：今日飲む薬と時間を確認し、飲んだら記録します。
- **見守る家族**：薬や飲む時間を登録し、服薬状況と薬の残りの量を確認します。

SwiftUI / TypeScript / Next.js / Prisma / PostgreSQL / Supabase

<p>
  <a href="https://www.okusuri-mimamori.com/"><strong>サービス紹介 →</strong></a>&nbsp; · &nbsp;
  <a href="https://github.com/kt-git-1/kt-git-1/blob/main/projects/med-manager.md">設計と実装の見どころ</a>&nbsp; · &nbsp;
  <a href="https://apps.apple.com/jp/app/id6787427428">App Store</a>
</p>

<table>
  <tr><th>薬を飲む人の画面</th><th>見守る家族の画面</th><th>薬の残りの量を確認</th></tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/kt-git-1/main/assets/med-manager/patient-today.png" width="220" alt="薬を飲む人が今日の薬を確認して記録する画面" /></td>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/kt-git-1/main/assets/med-manager/caregiver-today.png" width="220" alt="家族モードの服薬状況画面" /></td>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/kt-git-1/main/assets/med-manager/caregiver-inventory.png" width="220" alt="家族モードの残薬管理画面" /></td>
  </tr>
</table>

<sub>合成データを使用した開発版の画面です。App Store配信版とは表示が異なる場合があります。</sub>

### このプロジェクトで取り組んでいること

- **利用者に合わせた設計**：薬を飲む人と見守る家族、それぞれの役割に合わせて画面・操作・アクセス権限を分ける。
- **データの整合性**：服薬記録の取消と残薬の復元をトランザクションで扱う。
- **プライバシーへの配慮**：利用状況の分析に同意管理を設ける。
- **品質確認**：APIの単体・結合・契約・E2Eテストと、iOSのテストを用意する。

ソースコード本体は非公開です。公開資料では、画面と設計上の工夫を紹介しています。

## Pythonでのデータ処理・自動化 — analyze-fastq-app

**DNAの配列データを取得し、複数の解析ツールを順番に実行して、品質確認とレポート作成までつなぐパイプラインです。** 馬ゲノム解析を主に想定しています。

専門的な解析手順をPythonでつなぎ、繰り返し実行できる処理として実装しています。

- **処理の自動化**：データ取得・前処理・解析・品質確認・PDF/HTMLレポート出力を連携。
- **再実行と並列処理**：完了済み処理のスキップ、既存の中間結果の再利用、サンプル単位の並列実行。
- **データ品質と検証**：欠損率などに基づくフィルタリング、PCA/MDSによる可視化、失敗時や再開時の動作を確認するテスト。

Python / NumPy / pandas / pytest / 外部解析ツール連携

[コード・実行手順](https://github.com/kt-git-1/analyze-fastq-app) · [設計と実装の見どころ](https://github.com/kt-git-1/kt-git-1/blob/main/projects/analyze-fastq.md) · [テスト](https://github.com/kt-git-1/analyze-fastq-app/tree/main/tests)

## 使用技術

| 領域 | 技術 | 取り組み |
| --- | --- | --- |
| モバイル | Swift / SwiftUI | お薬見守り iOS |
| API・Web | TypeScript / Next.js / React | API・Web |
| データ設計 | PostgreSQL / Prisma / Supabase | DBスキーマ |
| データ処理・解析 | Python / NumPy / pandas | [解析パイプライン](https://github.com/kt-git-1/analyze-fastq-app) |
| テスト | Vitest / Playwright / XCTest / GitHub Actions | APIテスト |
