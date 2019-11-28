# The Machine Learning Canvas

## 1. Decisions 
- How are predictionsused to make decisions that provide the proposed value to the end-user?   
`予測はエンドユーザーの意思決定にどのような価値を提供するか？`

## 2. Making Predictions   
- When do we make predictions on new inputs? How long do we have to featurize a new input and make prediction?   
`新しいインプットの予測はいつから可能か？　新しい入力を特徴付けして予測を行うにはどのくらいの期間が必要か？`

## 3. ML task
- Input, output to predict, type of problem.   
`入力、予測の出力、課題の種類`

## 4. Offline Evaluation
- Methods and metrics to evaluate the system before deployment.   
`デプロイ前にシステムを評価するための方法と評価基準`

## 5. Value Propositions
- What are we trying to do for the end-user(s) of the predictive system? What objectives are we serving?   
`予測システムはエンドユーザーに対してなにを提供できるか？　私たちが果たす目的は何か？`

## 6. Data Sources
- Which raw data sources can we use(internal and external)?   
`どの生データ(内部もしくは外部)を扱うことができるか？`

## 7. Features
- Input representations extracted from raw data sources.   
`生データによって抽出された入力表現`

## 8. Collecting Data
- How do we get new data to learn from (inputs and outputs)?   
`どのように新しい学習データを取得するか(入力と出力)`

## 9. Buliding Models
- When do we create/update models with new training data? How long do we have to featurize training inputs and create a model?   
`新しい学習データでモデルをいつ作成/更新するか？　学習入力を特徴付けてモデルを作成するにはどのくらいの時間が必要か？`

## 10. Live Evaluation and Monitoring
- Methods and metrics to evaluate the system after deployment and to quantity value creation.
`デプロイ後の創造価値に対するシステムの評価方法と基準`

# 解決したい課題
多くの組織では予測モデルを構築する人々と組織の目的に応える方法を知っている人との間に大きな壁があります。
彼らがチームとしてタスクを調整し、価値を生み出すための方法を提供したい。　　　

# 基本的な使い方
初めは`Value Proposition`から始まる。   
_What + Why + Who_: 何をしようとしているのか、なぜ重要なのか、誰がシステムを使うのか、それによってどのような影響があるのかを考える。   
_How_: 左側の`PREDICT`と右側の`LEARN`に分けることができる。

- `PREDICT`: 予測についてのブロック
    1. ML task
    2. Decisions
    3. Masking predictions
    4. Offline evaluation

    `LEARN`: 学習についてのブロック
    1. Data sources
    2. Collecting data
    3. Features
    4. Building models

最後に`Live Evaluation and Monitoring`について   
デプロイ後にシステムを評価し、価値を定量化するための方法と評価基準について。