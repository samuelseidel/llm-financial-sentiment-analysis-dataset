# Data Dictionary

## Overview

This document provides detailed variable definitions for all datasets in the systematic review.

---

## 1. Screening Data

### `title_abstract_screening.csv`

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| study_id | String | Unique identifier for each study | Format: AUTHOR_YEAR_XXX |
| title | String | Article title | Free text |
| authors | String | Author names | Comma-separated list |
| year | Integer | Publication year | 2015-2026 |
| source | String | Database source | Scopus, WoS, arXiv, Google Scholar |
| abstract | String | Article abstract | Free text |
| include_exclude | String | Screening decision | "Include", "Exclude" |
| exclusion_reason | String | Reason for exclusion | See exclusion criteria |
| screener_1 | String | First screener initials | Reviewer ID |
| screener_2 | String | Second screener initials | Reviewer ID |
| agreement | Boolean | Screener agreement | TRUE/FALSE |

### `full_text_assessment_results.csv`

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| study_id | String | Unique identifier | Format: AUTHOR_YEAR_XXX |
| criterion_1_markets | Boolean | Analyzed financial markets | TRUE/FALSE |
| criterion_2_llm | Boolean | Employed LLM methods | TRUE/FALSE |
| criterion_3_metrics | Boolean | Reported quantitative metrics | TRUE/FALSE |
| criterion_4_empirical | Boolean | Empirical research | TRUE/FALSE |
| final_decision | String | Eligibility decision | "Include", "Exclude" |
| notes | String | Assessment notes | Free text |

---

## 2. Extraction Data

### `SYNTHESIS_DATA_READY.csv` (Main Dataset)

#### Study Metadata

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| study_id | String | Unique identifier | Format: AUTHOR_YEAR_XXX |
| authors | String | Author names | Comma-separated |
| year | Integer | Publication year | 2015-2026 |
| title | String | Article title | Free text |
| publication_type | String | Publication venue type | Journal, Conference, Preprint |
| venue | String | Journal/conference name | Free text |
| doi | String | Digital Object Identifier | DOI format |
| country | String | First author affiliation country | ISO country code |
| study_design | String | Research design type | Experimental, Observational, Case Study |

#### LLM Architecture

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| llm_type | String | Main LLM architecture | BERT, GPT, Domain-specific, Other |
| llm_model | String | Specific model name | FinBERT, GPT-3, BERT-base, etc. |
| model_size | String | Model parameter count | Small (<100M), Medium (100M-1B), Large (>1B) |
| pretraining | String | Pretraining approach | General, Financial domain, Mixed |
| fine_tuning | Boolean | Model fine-tuned | TRUE/FALSE |
| fine_tuning_data | String | Fine-tuning dataset | Dataset name or description |
| hybrid_architecture | Boolean | Combined with other models | TRUE/FALSE |
| hybrid_components | String | Additional model components | LSTM, GRU, Attention, etc. |
| prompt_engineering | Boolean | Used prompt engineering | TRUE/FALSE |
| few_shot_learning | Boolean | Applied few-shot learning | TRUE/FALSE |
| rag_used | Boolean | Retrieval-augmented generation | TRUE/FALSE |
| chain_of_thought | Boolean | Chain-of-thought prompting | TRUE/FALSE |

#### Dataset Characteristics

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| dataset_name | String | Primary dataset used | Free text |
| dataset_source | String | Data source | Twitter, News, Reddit, Financial reports |
| dataset_size | Integer | Number of samples | Numeric |
| time_period | String | Data collection period | Date range |
| languages | String | Languages in dataset | ISO language codes |
| labeling_method | String | Label creation approach | Manual, Automatic, Hybrid |
| sentiment_classes | Integer | Number of sentiment classes | 2 (binary), 3 (ternary), 5+ (fine-grained) |

#### Financial Markets

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| asset_class | String | Primary asset class | Stocks, Cryptocurrency, Forex, Commodities, Bonds |
| market_focus | String | Specific market | NYSE, NASDAQ, Bitcoin, etc. |
| prediction_target | String | Target variable | Price movement, Returns, Volatility |
| prediction_horizon | String | Forecast timeframe | Intraday, Daily, Weekly, Monthly |

#### Performance Metrics

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| accuracy | Float | Classification accuracy | 0.0-1.0 or percentage |
| precision | Float | Precision score | 0.0-1.0 |
| recall | Float | Recall score | 0.0-1.0 |
| f1_score | Float | F1 score | 0.0-1.0 |
| auc_roc | Float | Area under ROC curve | 0.0-1.0 |
| sharpe_ratio | Float | Risk-adjusted returns | Numeric |
| annual_return | Float | Annualized return | Percentage |
| max_drawdown | Float | Maximum drawdown | Percentage |
| baseline_model | String | Comparison baseline | Model name |
| baseline_performance | Float | Baseline metric value | Numeric |
| performance_gain | Float | Improvement over baseline | Percentage or absolute |

#### Validation & Reproducibility

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| train_test_split | String | Data split approach | Temporal, Random, K-fold |
| validation_method | String | Validation strategy | Holdout, Cross-validation, Walk-forward |
| test_size_pct | Float | Test set percentage | 0.0-1.0 |
| statistical_testing | Boolean | Significance tests reported | TRUE/FALSE |
| test_type | String | Statistical test used | t-test, Wilcoxon, etc. |
| p_value | Float | Statistical significance | 0.0-1.0 |
| confidence_intervals | Boolean | CIs reported | TRUE/FALSE |
| code_available | Boolean | Code publicly available | TRUE/FALSE |
| data_available | Boolean | Data publicly available | TRUE/FALSE |
| reproducibility_score | Integer | Reproducibility rating | 0-3 scale |

### `S5_Quality_Assessment_Scores.csv`

| Variable | Type | Description | Values/Range |
|----------|------|-------------|--------------|
| study_id | String | Unique identifier | Format: AUTHOR_YEAR_XXX |
| criterion_1_design | Integer | Research design clarity | 0-2 |
| criterion_2_data | Integer | Data quality | 0-2 |
| criterion_3_model | Integer | Model description | 0-1 |
| criterion_4_evaluation | Integer | Evaluation rigor | 0-2 |
| criterion_5_statistics | Integer | Statistical testing | 0-1 |
| criterion_6_reproducibility | Integer | Reproducibility | 0-1 |
| criterion_7_limitations | Integer | Limitations acknowledged | 0-1 |
| total_score | Integer | Total quality score | 0-10 |
| quality_tier | String | Quality classification | High (≥7), Medium (5-6), Low (3-4) |
| assessor_1 | String | First assessor | Reviewer ID |
| assessor_2 | String | Second assessor | Reviewer ID |
| inter_rater_agreement | Float | Agreement coefficient | 0.0-1.0 |

---

## 3. Analysis Tables

### `table1_study_characteristics.csv`

Summary statistics of study characteristics by year, publication type, and geography.

| Variable | Type | Description |
|----------|------|-------------|
| characteristic | String | Characteristic name |
| category | String | Category value |
| count | Integer | Number of studies |
| percentage | Float | Percentage of total |

### `table2_llm_models.csv`

Distribution of LLM models and architectural approaches.

| Variable | Type | Description |
|----------|------|-------------|
| model_type | String | LLM architecture type |
| model_family | String | Specific model family |
| count | Integer | Frequency |
| percentage | Float | Adoption rate |
| mean_performance | Float | Average performance |

### `table3_markets_applications.csv`

Financial markets coverage and application domains.

| Variable | Type | Description |
|----------|------|-------------|
| asset_class | String | Asset category |
| count | Integer | Number of studies |
| percentage | Float | Coverage percentage |
| gap_severity | String | Gap assessment |

### `table4_performance_metrics.csv`

Summary of reported performance metrics.

| Variable | Type | Description |
|----------|------|-------------|
| metric | String | Performance metric name |
| n_studies | Integer | Number reporting metric |
| mean | Float | Mean value |
| median | Float | Median value |
| std_dev | Float | Standard deviation |
| min | Float | Minimum value |
| max | Float | Maximum value |

### `table5_quality_assessment.csv`

Quality score distribution across studies.

| Variable | Type | Description |
|----------|------|-------------|
| quality_tier | String | Quality classification |
| n_studies | Integer | Number of studies |
| percentage | Float | Percentage |
| mean_score | Float | Average quality score |

### `table6_top_studies.csv`

Detailed information on high-quality studies (score ≥7).

Includes all variables from `SYNTHESIS_DATA_READY.csv` filtered for quality_tier = "High".

### `table7_research_gaps.csv`

Identified research gaps and future directions.

| Variable | Type | Description |
|----------|------|-------------|
| gap_category | String | Gap type |
| gap_description | String | Detailed description |
| severity | String | Importance level |
| recommendations | String | Suggested actions |

---

## Missing Data Codes

- **NA**: Not applicable
- **NR**: Not reported
- **NK**: Not known/unclear
- **--**: Field not relevant for this study type

---

## Data Types Reference

- **String**: Text field
- **Integer**: Whole number
- **Float**: Decimal number
- **Boolean**: TRUE/FALSE
- **Date**: YYYY-MM-DD format

---

## Quality Assessment Criteria Details

### Criterion 1: Research Design (0-2 points)
- 0: Unclear or poorly defined
- 1: Adequate description
- 2: Clear, well-justified design

### Criterion 2: Data Quality (0-2 points)
- 0: Poor quality or insufficient documentation
- 1: Adequate dataset with basic documentation
- 2: High-quality, well-documented dataset

### Criterion 3: Model Description (0-1 point)
- 0: Insufficient architectural details
- 1: Clear model architecture and configuration

### Criterion 4: Evaluation Rigor (0-2 points)
- 0: Weak evaluation methodology
- 1: Adequate metrics and baselines
- 2: Rigorous evaluation with proper validation

### Criterion 5: Statistical Testing (0-1 point)
- 0: No significance tests
- 1: Statistical tests reported

### Criterion 6: Reproducibility (0-1 point)
- 0: Code/data not available
- 1: Code or data publicly available

### Criterion 7: Limitations (0-1 point)
- 0: No limitations discussed
- 1: Limitations acknowledged

---

## Version History

- **v1.0.0** (2026-02-10): Initial data dictionary release

---

## Contact

For questions about variable definitions or data interpretation:
- **Author**: Ing. Samuel Seidel
- **Institution**: University of Hradec Králové
- **Dataset DOI**: Pending
