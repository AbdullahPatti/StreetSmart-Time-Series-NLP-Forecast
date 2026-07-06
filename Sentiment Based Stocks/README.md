# 📈 Bitcoin Price Prediction with Regime-Aware Multi-Modal Learning

This repository contains the research project, analysis pipeline, experimental notebooks, and paper source for a study on predicting Bitcoin price direction using a regime-aware multi-modal learning framework. The work combines technical market features with social sentiment signals to forecast whether Bitcoin will move upward or downward in the next 3–6 hours.

The project is centered around the idea that Bitcoin is not driven by price data alone. Market behavior is influenced by technical structure, volatility, investor psychology, social media discourse, and broader macro-financial events. This research investigates whether a model can learn to use these signals more effectively by adapting its behavior depending on the current market regime.

---

## 🎯 Research Goal

The main objective of this project is to build and validate a regime-aware multi-modal learning system that predicts Bitcoin price direction for short horizons by adaptively fusing:

- social sentiment signals from Reddit discussions,
- technical OHLCV features from Bitcoin price history,
- and a regime signal derived from recent market volatility.

The study focuses on the question of whether such an approach can outperform simpler static fusion strategies for short-horizon directional prediction.

---

## 🔍 Research Questions

This research is guided by four core questions:

1. Does social sentiment lead Bitcoin price movements in time?
2. Does regime-aware fusion outperform simple feature concatenation?
3. Which signal matters more in stable versus volatile market conditions?
4. Can Bitcoin price direction be predicted reliably 3–6 hours ahead?

These questions form the foundation of the methodology and the experimental design.

---

## 🧠 Project Overview

Bitcoin is one of the most actively watched and heavily traded digital assets in the world. It has attracted significant retail and institutional attention because of its volatility, high trading activity, and strong sensitivity to market sentiment. However, predicting Bitcoin price movements remains extremely difficult because the market is influenced by a mixture of:

- price dynamics,
- liquidity conditions,
- news and regulatory developments,
- investor psychology,
- social media narratives,
- and sudden regime shifts.

Traditional approaches often rely only on historical price data and technical features such as Open, High, Low, Close, and Volume. While these features remain useful, they do not capture the full behavioural structure of the market. This project explores whether sentiment data from online discussion platforms can improve forecasting when combined with technical features in a more intelligent way.

---

## 🧪 Core Idea

The proposed approach is called a regime-aware multi-modal learning framework. Instead of treating all market conditions in the same way, the model adjusts how strongly it relies on sentiment versus price information depending on whether the market is currently in a stable or volatile state.

The rationale is simple:

- during calm periods, technical price patterns may be more informative;
- during volatile or stressful periods, social sentiment may become more useful because crowd behaviour can amplify price movements.

This makes the fusion process more adaptive and closer to how real markets behave.

---

## 🏗️ Methodology

### 1. Data Sources

The project uses three major data sources:

- Bitcoin OHLCV data from Yahoo Finance via the yfinance package,
- Reddit sentiment data from the /r/Bitcoin community,
- and additional daily sentiment data related to cryptocurrency and macro-financial context.

These sources are aligned at an hourly resolution and combined into a unified dataset for model training and evaluation.

### 2. Feature Engineering

The pipeline extracts and prepares a rich set of input features, including:

- OHLCV-based technical features,
- rolling volatility measures,
- sentiment polarity scores,
- bullish and bearish sentiment probabilities,
- and discussion intensity signals.

### 3. Model Design

The study compares multiple model configurations:

- a price-only BiLSTM model,
- a sentiment-only classifier,
- a static concatenation model,
- and the proposed regime-aware multi-modal model.

The proposed architecture uses a BiLSTM backbone for sequential price features and a separate sentiment branch for social signal processing. A regime gate then regulates how the two branches are fused.

### 4. Regime Detection

Market state is inferred using rolling volatility. The model conditions its fusion weights on whether the market is in a more stable or more volatile regime. This is a key innovation because it allows the model to trust sentiment differently under different market conditions.

### 5. Ablation Study

A systematic ablation study is included to test the importance of each model component:

- the sentiment branch,
- the regime-detection module,
- and the adaptive fusion mechanism.

The results confirm that removing any of these components degrades performance.

---

## 📊 Main Findings

The reported results show that the proposed regime-aware approach improves over simpler baselines in several respects.

The paper reports:

- macro-F1 of 0.5474 for the 3-hour prediction task,
- macro-F1 of 0.5513 for the 6-hour prediction task,
- and the highest AUC among the compared models on the 3-hour horizon.

These values are not presented as perfect predictive performance, but as evidence that the regime-aware fusion strategy offers a meaningful improvement over static fusion and simpler modelling approaches.

The findings support the claim that adaptive fusion is a valuable design principle for cryptocurrency forecasting, especially when markets are noisy, non-stationary, and strongly influenced by social behaviour.

---

## 📁 Repository Structure

The workspace contains the following main components:

- [main.tex](main.tex) — the LaTeX source for the research paper.
- [Bitcoin_Research_Proposal.pdf](Bitcoin_Research_Proposal.pdf) — the research proposal document.
- [data/](data/) — input datasets and processed CSV files.
- [results/](results/) — generated results, feature tables, and labeled datasets.
- [processing/](processing/) — notebooks for data preprocessing and feature engineering.
- [predictions/](predictions/) — notebooks for modeling, forecasting, and ablation experiments.
- [visulaizations/](visulaizations/) — notebooks used for plotting and visual analysis.
- [figures/](figures/) — image assets used in the paper and presentation materials.

---

## 🧾 Research Proposal Summary

The proposal focuses on the idea that Bitcoin direction prediction should not be treated as a purely technical forecasting problem. Instead, it should be framed as a multi-modal problem where social sentiment and price-based features jointly inform the prediction.

The proposed system is designed to answer practical questions for investors and researchers:

- whether social signals provide useful predictive information,
- whether market regime information improves predictive performance,
- and whether adaptive fusion is a better design than fixed concatenation.

---

## 🛠️ Tools and Technologies

This project uses a modern data science and machine learning workflow, including:

- Python,
- Jupyter notebooks,
- pandas and NumPy for preprocessing,
- yfinance for market data retrieval,
- FinBERT-based sentiment analysis,
- deep learning with BiLSTM,
- and evaluation metrics such as F1-score and AUC.

The implementation is designed to be reproducible and modular, with separate notebooks for preprocessing, feature generation, modeling, and visualization.

---

## 📌 Notes on Interpretation

The results should be interpreted carefully. Bitcoin forecasting is a difficult task because the market is highly volatile, noisy, and influenced by many external factors. For that reason, this project does not claim perfect prediction. Instead, it shows that:

- social sentiment has value,
- regime-aware fusion is a meaningful improvement over naive fusion,
- and short-horizon forecasting can benefit from more adaptive modelling strategies.

This makes the work relevant both as a research contribution and as a practical exploration of financial forecasting methods.

---

## 🚀 How to Use This Repository

To explore the project:

1. Open the notebooks in the [processing/](processing/) folder for data preparation.
2. Use the notebooks in [predictions/](predictions/) to train and evaluate models.
3. Review the generated outputs in [results/](results/).
4. Read the paper source in [main.tex](main.tex) for the formal research write-up.

If you are interested in reproducing the workflow, start with the preprocessing notebooks and then move to the prediction notebooks in the order they are organized.

---

## 🧩 Strengths of the Work

- Uses both technical and sentiment-based features.
- Introduces a regime-aware fusion mechanism.
- Includes ablation studies to test the value of each component.
- Focuses on short-horizon Bitcoin prediction, which is a challenging and practical setting.
- Provides a reproducible notebook-based workflow.

---

## ⚠️ Limitations and Future Work

The project also has clear limitations that are worth acknowledging:

- the dataset size is limited for deep learning training,
- short-horizon prediction remains inherently noisy,
- and Bitcoin markets are strongly affected by external shocks that may not be fully captured by the current feature set.

Future work could include:

- longer historical coverage,
- more advanced regime detection methods,
- hyperparameter tuning,
- larger sequence windows,
- and possibly more expressive architectures for temporal fusion.

---

## ✅ Summary

This repository presents a serious and practical investigation into short-horizon Bitcoin price prediction using multi-modal learning. The work combines social sentiment analysis, technical market features, and regime-aware fusion to study whether Bitcoin movement can be forecast more effectively when the model adjusts to the current market state.

The project is valuable because it focuses on a realistic problem setting, uses a thoughtful modelling strategy, and provides a clear empirical foundation for future research in cryptocurrency forecasting.
