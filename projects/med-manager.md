# お薬見守り — プロジェクト紹介

[プロフィールへ戻る](https://github.com/kt-git-1) · [App Store](https://apps.apple.com/jp/app/id6787427428)

本人の服薬記録と、家族による服薬状況・残薬の確認を支援する個人開発アプリです。iOSアプリ・API・データベースを実装しています。ソースコード本体は非公開です。

## 利用者に合わせた役割と操作

本人にはその日の服薬に必要な操作を、家族には薬・スケジュール・在庫の管理を提供します。画面を分けるだけでなく、APIでも役割と患者単位のアクセス範囲を検証しています。家族の認証と本人端末のセッションを分け、連携コードで接続する構成です。

## 服薬記録と残薬の整合性

誤った服薬記録を取り消す場合、記録だけを消すと残薬が少ないままになります。記録の取消と在庫復元をDBトランザクション内で扱い、取消済みの記録を再度処理しないための更新条件を設けています。

## 利用状況の分析と同意管理

分析処理をサービスに集約し、収集の有効・無効を管理しています。オプトアウト時には分析データをリセットします。画面や操作結果を列挙型で定義し、送信するイベントを管理しています。

## 品質確認

APIの単体・結合・契約・E2Eテストと、iOSのテストを用意しています。CIにはLint・型検査・テスト・ビルドの手順を定義しています。

| 領域 | 使用技術 |
| --- | --- |
| iOS | Swift / SwiftUI |
| API・Web | TypeScript / Next.js / React |
| データ | PostgreSQL / Prisma / Supabase |
| 通知・分析 | APNs / Firebase |
| テスト | Vitest / Playwright / XCTest / GitHub Actions |

## 画面

画面は合成データを使用した開発版です。App Store配信版とは表示が異なる場合があります。

<table>
<tr><th>本人の服薬記録</th><th>家族の見守り</th><th>残薬管理</th></tr>
<tr>
<td><img src="../assets/med-manager/patient-today.png" width="220" alt="本人の服薬記録画面" /></td>
<td><img src="../assets/med-manager/caregiver-today.png" width="220" alt="家族の服薬確認画面" /></td>
<td><img src="../assets/med-manager/caregiver-inventory.png" width="220" alt="残薬管理画面" /></td>
</tr>
</table>
