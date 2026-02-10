# Codebook

## Systematic Review Coding Scheme

This codebook documents the systematic coding scheme used for data extraction in the review "Large Language Models for Financial Sentiment Analysis."

---

## 1. Study Selection Process

### 1.1 Screening Phase

**Title/Abstract Screening Decision Tree:**

```
START
  │
  ├─ Does it involve financial markets?
  │    NO → EXCLUDE (Reason: Not financial)
  │    YES → Continue
  │
  ├─ Does it use LLM methods?
  │    NO → EXCLUDE (Reason: No LLM)
  │    YES → Continue
  │
  ├─ Does it perform sentiment analysis?
  │    NO → EXCLUDE (Reason: Not sentiment analysis)
  │    YES → Continue
  │
  ├─ Is it empirical research?
  │    NO → EXCLUDE (Reason: Not empirical)
  │    YES → INCLUDE for full-text assessment
```

**Exclusion Reasons Codebook:**

| Code | Reason | Definition | Example |
|------|--------|------------|---------|
| E1 | Not financial | Study does not analyze financial markets | General sentiment analysis on product reviews |
| E2 | No LLM | Does not employ large language models | Traditional ML only (SVM, Random Forest) |
| E3 | No sentiment | No sentiment analysis performed | Price prediction without sentiment |
| E4 | Not empirical | Theoretical or conceptual only | Survey papers, opinion pieces |
| E5 | No metrics | No quantitative results reported | Qualitative analysis only |
| E6 | Language | Not in English | Study published in non-English language |
| E7 | Duplicate | Duplicate publication | Same study in different venues |
| E8 | Inaccessible | Full text not available | Paywalled without institutional access |

### 1.2 Full-Text Assessment

**Eligibility Criteria (All must be TRUE):**

1. **Markets**: Analyzed stocks, cryptocurrency, forex, commodities, or bonds
2. **LLM Methods**: Employed BERT, GPT, or other transformer-based LLMs
3. **Metrics**: Reported at least one quantitative performance metric
4. **Empirical**: Presented original empirical research with data analysis

---

## 2. Data Extraction Coding

### 2.1 LLM Architecture Types

| Code | Type | Definition | Examples |
|------|------|------------|----------|
| BERT | BERT variants | Bidirectional encoder models | BERT, RoBERTa, ALBERT, DistilBERT |
| GPT | GPT variants | Generative pre-trained transformers | GPT-2, GPT-3, GPT-3.5, GPT-4 |
| DOMAIN | Domain-specific | Finance-specific pre-trained models | FinBERT, FinGPT, BloombergGPT |
| HYBRID | Hybrid architecture | LLM combined with other models | BERT + LSTM, GPT + Attention |
| OTHER | Other LLMs | Other transformer architectures | T5, XLNet, ELECTRA |

### 2.2 Model Size Categories

| Code | Category | Parameter Count | Memory Footprint |
|------|----------|-----------------|------------------|
| SMALL | Small | < 100M parameters | < 1 GB |
| MEDIUM | Medium | 100M - 1B parameters | 1-4 GB |
| LARGE | Large | 1B - 10B parameters | 4-40 GB |
| XLARGE | Extra Large | > 10B parameters | > 40 GB |

### 2.3 Pretraining Approaches

| Code | Approach | Definition |
|------|----------|------------|
| GENERAL | General domain | Pretrained on general text (Wikipedia, books, web) |
| FINANCIAL | Financial domain | Pretrained on financial text (news, reports, filings) |
| MIXED | Mixed domain | Combination of general and financial pretraining |
| SCRATCH | From scratch | Trained from random initialization |

### 2.4 Fine-Tuning Strategies

| Code | Strategy | Definition |
|------|----------|------------|
| NONE | No fine-tuning | Used pre-trained model as-is |
| FULL | Full fine-tuning | Updated all model parameters |
| PARTIAL | Partial fine-tuning | Updated only final layers or specific components |
| ADAPTER | Adapter-based | Added trainable adapter modules |
| LORA | LoRA | Low-rank adaptation |
| PROMPT | Prompt tuning | Learned continuous prompt embeddings |

### 2.5 Advanced Techniques

**Prompt Engineering:**
- PE_ZERO: Zero-shot prompting
- PE_FEW: Few-shot prompting (examples in prompt)
- PE_COT: Chain-of-thought prompting
- PE_NONE: No prompt engineering

**Retrieval Methods:**
- RAG_YES: Retrieval-augmented generation used
- RAG_NO: No retrieval mechanism
- RAG_HYBRID: Hybrid retrieval approach

### 2.6 Dataset Characteristics

**Data Source Categories:**

| Code | Source | Description |
|------|--------|-------------|
| TWITTER | Twitter/X | Social media posts |
| NEWS | News articles | Financial news, press releases |
| REDDIT | Reddit | Forum discussions |
| FILINGS | Financial reports | 10-K, 10-Q, earnings calls |
| BLOGS | Blogs | Financial blogs, analyst opinions |
| MIXED | Multiple sources | Combination of multiple sources |

**Labeling Methods:**

| Code | Method | Definition |
|------|--------|------------|
| MANUAL | Manual annotation | Human annotators labeled data |
| AUTO | Automatic | Labels derived automatically (price movements) |
| SEMI | Semi-automatic | Combination of manual and automatic |
| CROWD | Crowdsourced | Labels from crowdsourcing platforms |

**Sentiment Classes:**

| Code | Classes | Definition |
|------|---------|------------|
| BINARY | 2 classes | Positive/Negative |
| TERNARY | 3 classes | Positive/Neutral/Negative |
| FINE | 5+ classes | Fine-grained sentiment scale |

### 2.7 Financial Markets

**Asset Class Taxonomy:**

| Code | Asset Class | Sub-categories |
|------|-------------|----------------|
| STOCK | Stocks/Equities | Individual stocks, indices, ETFs |
| CRYPTO | Cryptocurrency | Bitcoin, Ethereum, altcoins |
| FOREX | Foreign Exchange | Currency pairs |
| COMMODITY | Commodities | Oil, gold, agricultural products |
| BOND | Fixed Income | Government bonds, corporate bonds |
| DERIVATIVE | Derivatives | Options, futures |

**Prediction Targets:**

| Code | Target | Definition |
|------|--------|------------|
| PRICE_DIR | Price direction | Up/Down classification |
| PRICE_MOVE | Price movement | Continuous price change |
| VOLATILITY | Volatility | Price volatility prediction |
| RETURNS | Returns | Percentage returns |
| RISK | Risk metrics | VaR, CVaR, Sharpe ratio |

**Prediction Horizons:**

| Code | Horizon | Timeframe |
|------|---------|-----------|
| INTRADAY | Intraday | Minutes to hours |
| DAILY | Daily | 1 day ahead |
| WEEKLY | Weekly | 1 week ahead |
| MONTHLY | Monthly | 1 month ahead |
| LONG | Long-term | > 1 month |

### 2.8 Performance Metrics

**Classification Metrics:**
- ACC: Accuracy
- PREC: Precision
- REC: Recall
- F1: F1 score
- AUC: Area Under ROC Curve
- MCC: Matthews Correlation Coefficient

**Trading Metrics:**
- SHARPE: Sharpe ratio
- SORTINO: Sortino ratio
- RET: Annualized return
- MDD: Maximum drawdown
- WINRATE: Win rate
- PROFIT: Cumulative profit

### 2.9 Validation Approaches

**Data Splitting:**

| Code | Method | Description |
|------|--------|-------------|
| TEMPORAL | Temporal split | Train on past, test on future |
| RANDOM | Random split | Random train/test split |
| KFOLD | K-fold CV | K-fold cross-validation |
| WALK | Walk-forward | Rolling window validation |

**Statistical Testing:**

| Code | Test | When Used |
|------|------|-----------|
| TTEST | t-test | Comparing two means |
| ANOVA | ANOVA | Comparing multiple groups |
| WILCOX | Wilcoxon | Non-parametric comparison |
| DM | Diebold-Mariano | Forecast comparison |
| NONE | No test | No significance testing |

---

## 3. Quality Assessment Coding

### 3.1 Research Design (0-2 points)

**Scoring Rubric:**

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Poor | Unclear objectives, missing methodology description |
| 1 | Adequate | Clear objectives, basic methodology described |
| 2 | Excellent | Well-defined research questions, detailed methodology, justified design choices |

### 3.2 Data Quality (0-2 points)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Poor | Small dataset (<1,000 samples), no documentation |
| 1 | Adequate | Moderate size (1,000-10,000), basic documentation |
| 2 | Excellent | Large dataset (>10,000), comprehensive documentation, publicly available |

### 3.3 Model Description (0-1 point)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Insufficient | Missing architecture details, hyperparameters not reported |
| 1 | Clear | Complete architecture description, hyperparameters specified |

### 3.4 Evaluation Rigor (0-2 points)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Weak | Single metric, no baselines, no validation strategy |
| 1 | Adequate | Multiple metrics, baseline comparison, basic validation |
| 2 | Rigorous | Comprehensive metrics, strong baselines, proper temporal validation, ablation studies |

### 3.5 Statistical Testing (0-1 point)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Missing | No significance tests reported |
| 1 | Reported | Statistical tests with p-values or confidence intervals |

### 3.6 Reproducibility (0-1 point)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Not reproducible | Code and data not available |
| 1 | Reproducible | Code or data publicly available with documentation |

### 3.7 Limitations (0-1 point)

| Score | Criteria | Indicators |
|-------|----------|------------|
| 0 | Not discussed | No limitations acknowledged |
| 1 | Acknowledged | Limitations explicitly discussed |

---

## 4. Inter-Rater Reliability

### 4.1 Agreement Calculation

**Cohen's Kappa Interpretation:**
- κ < 0.20: Poor agreement
- κ 0.21-0.40: Fair agreement
- κ 0.41-0.60: Moderate agreement
- κ 0.61-0.80: Substantial agreement
- κ 0.81-1.00: Almost perfect agreement

**This Study Results:**
- Screening phase: κ = 0.85 (almost perfect)
- Quality assessment: Agreement = 0.89 (almost perfect)

### 4.2 Disagreement Resolution

**Procedure:**
1. Initial independent coding by two reviewers
2. Compare coding decisions
3. Discuss disagreements
4. Reach consensus through discussion
5. If no consensus, consult third reviewer

---

## 5. Special Coding Rules

### 5.1 Multiple Values

When a study reports multiple values (e.g., multiple models, multiple markets):
- **Primary extraction**: Code the main/primary value
- **Secondary extraction**: Note additional values in notes field
- **Multiple entries**: Create separate entries only if clearly distinct experiments

### 5.2 Missing or Unclear Information

**Coding convention:**
- **NA**: Not applicable to this study type
- **NR**: Information not reported in paper
- **NK**: Information unclear or ambiguous
- **Estimated**: Value estimated from figures/text (note in comments)

### 5.3 Conflicting Information

If paper contains conflicting values:
1. Prioritize information from tables over text
2. Prioritize information from results over abstract
3. Note discrepancy in extraction notes
4. Contact authors if critical value is unclear

---

## 6. Data Extraction Workflow

### 6.1 Standard Procedure

1. **Initial reading**: Read full paper for general understanding
2. **Systematic extraction**: Extract data using template
3. **Quality check**: Verify all required fields completed
4. **Cross-check**: Second reviewer independently extracts
5. **Comparison**: Compare extractions, resolve disagreements
6. **Finalization**: Consensus coding finalized

### 6.2 Time Investment

Average time per paper:
- Screening (title/abstract): 3-5 minutes
- Full-text assessment: 10-15 minutes
- Data extraction: 30-45 minutes
- Quality assessment: 15-20 minutes

---

## Version History

- **v1.0.0** (2026-02-10): Initial codebook release

---

## References

This codebook follows guidelines from:
- PRISMA 2020 Statement
- Cochrane Handbook for Systematic Reviews
- Campbell Collaboration coding standards

---

## Contact

For questions about coding procedures:
- **Author**: Ing. Samuel Seidel
- **Institution**: University of Hradec Králové
