# Automatic generation of soccer commentary from playdata by rule-base
### 学部研究で書いたコード
本フォルダは以下の2つのipynbファイルで構成されており、以下のCSVファイルを用いて結果の出力を行っている（CSVファイルは配布していません）
（t5_mainではテストの出力結果は閲覧可能です）

CSVファイル
1. annotated_playdata.csv : 選手名とチーム名をテキスト速報内での表記に変更後、プレーデータに無加工のテキスト速報とPlaceholder付きのテキスト速報をアノテーションし、
コメントが対応されていない攻撃履歴は削除したデータ
2. rulebase_dataset.csv : ルールベース手法用に加工されたデータ。input(コメントが対応された攻撃履歴ごとのテンプレート文)、output(無加工のテキスト速報)

ipynbファイル
「ルールベース手法」
プレーデータ → 各イベントをルールベーステキストに変換 → まとめてT5に入力しテキスト速報に変換
1. Making_Rulebase_dataset.ipynb : annotated_playdata.csvをルールベース用に加工するためのコード。最終的にrulebase_dataset.csvファイルを出力する
2. t5_main.ipynb : rulebase_dataset.csvファイルを入力データとしてpl.lightningを介してT5をファインチューニングを行い、テキスト速報を出力するコード
