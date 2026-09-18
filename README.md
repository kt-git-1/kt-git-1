# kaichang / kt-git-1

**日々の困りごとを、使えるアプリケーションに。**

本人と家族のための服薬管理アプリ「お薬見守り」を個人開発しています。iOSの画面からAPI・データベースまで、利用者の操作と業務ルールをつなぐ設計・実装に取り組んでいます。

## 代表作 — お薬見守り

**本人は今日のお薬を確認して記録。家族は服薬状況と残薬を確認。**

SwiftUI / TypeScript / Next.js / Prisma / PostgreSQL / Supabase

<p>
  <a href="https://github.com/kt-git-1/med-manager_v3"><strong>コード・プロジェクト紹介 →</strong></a>&nbsp; · &nbsp;
  <a href="https://github.com/kt-git-1/med-manager_v3/blob/main/docs/portfolio.md">設計と実装の見どころ</a>&nbsp; · &nbsp;
  <a href="https://apps.apple.com/jp/app/id6787427428">App Store</a>
</p>

<table>
  <tr><th>本人の服薬記録</th><th>家族の見守り</th><th>残薬と補充の確認</th></tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/med-manager_v3/main/api/public/screenshots/patient-today.png" width="220" alt="本人モードの今日のお薬画面" /></td>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/med-manager_v3/main/api/public/screenshots/caregiver-today.png" width="220" alt="家族モードの服薬状況画面" /></td>
    <td><img src="https://raw.githubusercontent.com/kt-git-1/med-manager_v3/main/api/public/screenshots/caregiver-inventory.png" width="220" alt="家族モードの残薬管理画面" /></td>
  </tr>
</table>

<sub>合成データを使用した開発版の画面です。App Store配信版とは表示が異なる場合があります。</sub>

### このプロジェクトで取り組んでいること

- **利用者に合わせた設計**：本人と家族の画面・操作・アクセス権限を分ける。
- **データの整合性**：服薬記録の取消と残薬の復元をトランザクションで扱う。
- **プライバシーへの配慮**：利用状況の分析に同意管理を設ける。
- **品質確認**：APIの単体・結合・契約・E2Eテストと、iOSのテストを用意する。

## その他の取り組み

| プロジェクト | 内容 | 技術 |
| --- | --- | --- |
| [nurse-scheduling](https://github.com/kt-git-1/nurse-scheduling) | 希望休や勤務条件を制約として扱う、看護師のシフト作成の試作 | Python / OR-Tools / pandas / openpyxl |

## 使用技術と実装例

| 領域 | 技術 | 実装例 |
| --- | --- | --- |
| モバイル | Swift / SwiftUI | [お薬見守り iOS](https://github.com/kt-git-1/med-manager_v3/tree/main/ios/MedicationApp) |
| API・Web | TypeScript / Next.js / React | [API・Web](https://github.com/kt-git-1/med-manager_v3/tree/main/api) |
| データ設計 | PostgreSQL / Prisma / Supabase | [DBスキーマ](https://github.com/kt-git-1/med-manager_v3/blob/main/api/prisma/schema.prisma) |
| 業務の自動化 | Python / OR-Tools | [シフト作成](https://github.com/kt-git-1/nurse-scheduling) |
| テスト | Vitest / Playwright / XCTest / GitHub Actions | [APIテスト](https://github.com/kt-git-1/med-manager_v3/tree/main/api/tests) |
