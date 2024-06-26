本フォルダは以下の2つのCSVファイルと4つのipynbファイルで構成されている
CSVファイル
1. annotated_playdata.csv : 選手名とチーム名をテキスト速報内での表記に変更後、プレーデータに無加工のテキスト速報とPlaceholder付きのテキスト速報をアノテーションし、
コメントが対応されていない攻撃履歴は削除したデータ
2. rulebase_dataset.csv : ルールベース手法用に加工されたデータ。input(コメントが対応された攻撃履歴ごとのテンプレート文)、output(無加工のテキスト速報)
3. NN_dataset.csv : annotated_playdataのラベルエンコーディングされたコラムをワンホットエンコーディングし、'F_タッチ=1'のイベントを省いたデータ。

ipynbファイル
「NN-base」
1. NN-base_MLP.ipynb : アテンション計算にMLPを用いてLSTM+Attention_Seq2Seqを学習し、テキスト速報を生成するコード
2. NN-base_MHA.ipynb : アテンション計算にMHAを用いてLSTM+Attention_Seq2Seqを学習し、テキスト速報を生成するコード
「ルールベース」
1. Making_Rulebase_dataset.ipynb : annotated_playdata.csvをルールベース用に加工するためのコード。最終的にrulebase_dataset.csvファイルを出力する
2. t5_main.ipynb : rulebase_dataset.csvファイルを入力データとしてpl.lightningを介してT5をファインチューニングを行い、テキスト速報を出力するコード