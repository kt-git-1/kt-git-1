# analyze-fastq-app — データ解析パイプラインの自動化

[プロフィールへ戻る](https://github.com/kt-git-1) · [ソースコード・実行手順](https://github.com/kt-git-1/analyze-fastq-app)

## 何をするプロジェクトか

DNAの配列を格納したFASTQファイルを取得し、前処理、参照ゲノムへの位置合わせ、品質確認、変異情報の出力、サンプル間の比較、レポート作成までをつなぐPythonプログラムです。主に馬ゲノム解析を想定しています。

## 設計上の工夫

| 課題 | 実装 | コード・テスト |
| --- | --- | --- |
| 複数の解析ツールを手作業で順番に実行する必要がある | 処理をモジュールに分け、Pythonから呼び出す | [main.py](https://github.com/kt-git-1/analyze-fastq-app/blob/main/main.py) / [modules](https://github.com/kt-git-1/analyze-fastq-app/tree/main/modules) |
| 長い処理を最初からやり直したくない | 完了フラグと既存出力の確認により処理をスキップ・再利用する | [再開・失敗時のテスト](https://github.com/kt-git-1/analyze-fastq-app/blob/main/tests/test_main_flow.py) |
| 複数サンプルを処理し、失敗した工程を把握したい | ThreadPoolExecutorによる並列実行と、サンプル単位の成否・失敗工程の集計 | [実行制御](https://github.com/kt-git-1/analyze-fastq-app/blob/main/main.py) |
| 欠損の多いデータが解析結果に影響する | 欠損率などの条件でフィルタリングし、除外したサンプルも出力する | [PCA処理](https://github.com/kt-git-1/analyze-fastq-app/blob/main/modules/cohort_pca.py) / [テスト](https://github.com/kt-git-1/analyze-fastq-app/blob/main/tests/test_cohort_pca.py) |
| 結果の確認に複数の出力を読む必要がある | 品質指標・図・追加確認事項をHTML/PDF・表へまとめる | [レポート生成](https://github.com/kt-git-1/analyze-fastq-app/blob/main/modules/publication_report.py) / [テスト](https://github.com/kt-git-1/analyze-fastq-app/blob/main/tests/test_publication_report.py) |

## 他の業務にも応用できる点

扱うデータはゲノムですが、異なる形式の入力を整理し、複数のツールを連携させ、途中結果を保存し、出力の品質を確認する構成です。業務システムのデータ前処理やバッチ処理にもつながる実装例として紹介しています。

## 実装と評価の範囲

PCA/MDSはサンプル間の関係を調べる統計解析です。この作品をLLM・RAGの実装実績としては扱っていません。

公開テストには外部解析ツールを置き換えた処理フローの検証も含まれます。実データで解析全体を実行するには、参照ゲノムと外部ツールのセットアップが必要です。実行時間の削減率や解析精度の数値は、この紹介では主張していません。
