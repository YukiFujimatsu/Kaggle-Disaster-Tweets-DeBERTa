# NLP Disaster Tweets Classification with DeBERTa

Kaggleコンペティション「Natural Language Processing with Disaster Tweets」に向けた、DeBERTa-v3-largeを用いた高精度なテキスト分類モデルの実装です。

## 🌟 プロジェクト概要
SNS上のテキストは、緊急事態（例: "The sky is on fire"）と日常会話（例: "My new mixtape is on fire"）で同じ単語が使われるなど、文脈の理解が非常に困難です。本プロジェクトでは、最新のTransformerアーキテクチャである **DeBERTa-v3-large** を用いて、Twitter上のテキストが「実際の災害報」なのか「日常的な比喩表現」なのかを高精度に自動判定するモデルを構築しました。

## 🚀 特徴
- **SOTAモデルの採用**: 従来のBERTやRoBERTaを改良した `microsoft/deberta-v3-large` を採用し、Disentangled Attentionにより短文の文脈理解度を大幅に向上させています。
- **Hugging Face エコシステムの活用**: `Transformers` と `Datasets` ライブラリを組み合わせることで、高速で再現性の高いデータパイプラインを構築しています。
- **リソース最適化**: Kaggle環境の限られたGPUメモリで大規模モデルを学習・推論させるためのバッチ処理やパラメータチューニングを実施しています。

## 📂 ディレクトリ構成
```text
├── notebooks/
│   └── disastertweets-debertalarge.ipynb  # データの前処理・モデルの学習・推論パイプライン
└── README.md
```

## 🛠 技術スタック
- **Language**: Python 3.x
- **Deep Learning**: PyTorch, Hugging Face Transformers
- **Model**: `microsoft/deberta-v3-large`
- **Data Pipeline**: Hugging Face Datasets
- **Data Analysis**: Pandas, NumPy, Scikit-learn
- **Environment**: Kaggle Notebook / Google Colab (GPU 環境)

## 📈 実績
- **Kaggle Public Score: 0.83236 を達成**
  - ベースラインとなる標準的なBERTモデルを大きく上回る高スコア（F1 Score）を記録しました。
- **短文分類の最適化**: 
  - DeBERTa-v3の表現力を最大限に引き出すため、ハイパーパラメータのチューニングや適切な学習率スケジューリングを実施し、ノイズの多いTwitterデータに対して堅牢な分類器を実現しました。

## 📖 使い方

### モデルの学習と推論の実行
本リポジトリのノートブックを実行し、Kaggleに提出する予測結果を作成する手順です。
1. Kaggleのコンペティションページより[データセット](https://www.kaggle.com/c/nlp-getting-started/data)（`train.csv` と `test.csv`）をダウンロードし、`data/` ディレクトリに配置します。
2. `notebooks/disastertweets-debertalarge.ipynb` をJupyter環境で開きます。
3. セルを上から順に実行することで、データの前処理、DeBERTaモデルのファインチューニング、およびテストデータに対する推論が行われます。
4. 実行完了後、Kaggle提出用の予測結果である `submission.csv` が自動生成されます。

## 📊 データセットについて
本プロジェクトでは、モデルの学習および検証に以下の公開データセットを利用しています。

- **Dataset**: [Natural Language Processing with Disaster Tweets](https://www.kaggle.com/competitions/nlp-getting-started)
- **概要**: Twitter上の投稿が、実際の災害を報告しているものか、あるいは比喩や日常的な表現であるかを分類するためのデータセットです。

本プロジェクトでは、このデータセットを用いて DeBERTa-v3-large をファインチューニングし、単語の表面的な意味だけでなく、文脈を考慮した高度な災害検知モデルの構築に活用しています。
※ライセンス遵守およびリポジトリ軽量化のため、データセット自体は同梱していません。上記リンクより取得し、data/ ディレクトリに配置してください。
