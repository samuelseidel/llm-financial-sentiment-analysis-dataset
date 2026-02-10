# Large Language Models for Financial Sentiment Analysis - Dataset

[![DOI](https://img.shields.io/badge/DOI-pending-blue)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

This repository contains the complete dataset from the systematic review:

**"Large Language Models for Financial Sentiment Analysis: A Systematic Review"**

## Overview

This systematic review followed PRISMA 2020 guidelines to synthesize empirical evidence on large language model applications for financial sentiment analysis from 2015 to 2026.

### Key Statistics

- **Initial records identified:** 2,961
- **Studies included after screening:** 118
- **High-quality studies (score ≥7/10):** 36
- **Search period:** January 2015 - January 2026
- **Databases:** Scopus, Web of Science, arXiv, Google Scholar

### Novel Findings

1. **Performance-Adoption Paradox:** Most effective techniques (RAG +29.1% F1, CoT +38.87% accuracy) have lowest adoption rates (8.3%)
2. **Hybrid Architecture Advantage:** +2.84 pp mean accuracy, +7.75 pp peak performance
3. **Domain Adaptation Impact:** +4.1 pp accuracy, +86.1% Sharpe ratio improvement
4. **Methodological Gap:** Only 13.9% of high-quality studies report statistical testing

## Dataset Structure

```
├── data/
│   ├── screening/
│   │   ├── title_abstract_screening.csv          # Initial screening results
│   │   └── full_text_assessment_results.csv      # Full-text assessment
│   ├── extraction/
│   │   ├── SYNTHESIS_DATA_READY.csv              # Main synthesis data (118 studies)
│   │   ├── S4_Data_Extraction_Template.csv       # Extraction template
│   │   └── S5_Quality_Assessment_Scores.csv      # Quality scores
│   └── tables/
│       ├── table1_study_characteristics.csv       # Study characteristics
│       ├── table2_llm_models.csv                  # LLM models & architectures
│       ├── table3_markets_applications.csv        # Financial markets coverage
│       ├── table4_performance_metrics.csv         # Performance metrics
│       ├── table5_quality_assessment.csv          # Quality assessment
│       ├── table6_top_studies.csv                 # Top 36 studies
│       └── table7_research_gaps.csv               # Research gaps
├── documentation/
│   ├── DATA_DICTIONARY.md                         # Variable definitions
│   ├── CODEBOOK.md                                # Coding scheme
│   └── PRISMA_CHECKLIST.md                        # PRISMA compliance
├── figures/
│   ├── figure1_prisma_flow.pdf                    # PRISMA flow diagram
│   ├── figure2_publication_trends.pdf             # Publication trends
│   ├── figure3_quality_distribution.pdf           # Quality scores
│   ├── figure4_quality_criteria_radar.pdf         # Quality criteria
│   ├── figure5_architectural_evolution.pdf        # Model evolution
│   ├── figure6_asset_class_distribution.pdf       # Market coverage
│   └── figure7_performance_by_model.pdf           # Performance comparison
└── README.md                                       # This file
```

## Data Files Description

### Screening Data

**`title_abstract_screening.csv`**
- Records screened at title/abstract level
- Fields: Study ID, Title, Authors, Year, Include/Exclude, Reason

**`full_text_assessment_results.csv`**
- Full-text eligibility assessment
- Fields: Study ID, Eligibility criteria (1-4), Final decision, Notes

### Extraction Data

**`SYNTHESIS_DATA_READY.csv`** (Main Dataset)
- Complete data from 118 included studies
- Fields: Study metadata, LLM architecture, dataset, performance metrics, quality scores
- Primary file for replication and meta-analysis

**`S5_Quality_Assessment_Scores.csv`**
- Quality assessment using 7-criteria framework (0-10 scale)
- Criteria: Research design, data quality, model description, evaluation rigor, statistical testing, reproducibility, limitations

### Analysis Tables

- **Table 1:** Study characteristics (year, publication type, geography)
- **Table 2:** LLM models and architectures (BERT variants, GPT models, domain-specific)
- **Table 3:** Financial markets and applications (stocks, crypto, forex, commodities)
- **Table 4:** Performance metrics summary (accuracy, F1, Sharpe ratio)
- **Table 5:** Quality assessment distribution
- **Table 6:** Top 36 high-quality studies (detailed analysis)
- **Table 7:** Identified research gaps and future directions

## Usage

### Citation

If you use this dataset, please cite:

```bibtex
@article{seidel2026llm,
  title={Large Language Models for Financial Sentiment Analysis: A Systematic Review},
  author={Seidel, Samuel},
  journal={[Journal name pending]},
  year={2026},
  note={Dataset available at: https://github.com/samuelseidel/llm-financial-sentiment-analysis-dataset}
}
```

### Loading the Data (Python)

```python
import pandas as pd

# Load main synthesis data
df = pd.read_csv('data/extraction/SYNTHESIS_DATA_READY.csv')

# Load quality assessment scores
quality = pd.read_csv('data/extraction/S5_Quality_Assessment_Scores.csv')

# Filter for high-quality studies (score >= 7)
high_quality = quality[quality['total_score'] >= 7]
```

### Loading the Data (R)

```r
# Load main synthesis data
df <- read.csv('data/extraction/SYNTHESIS_DATA_READY.csv')

# Load quality assessment scores
quality <- read.csv('data/extraction/S5_Quality_Assessment_Scores.csv')

# Filter for high-quality studies (score >= 7)
high_quality <- quality[quality$total_score >= 7, ]
```

## Methodology

### Search Strategy

**Databases:**
- Scopus
- Web of Science (Core Collection)
- arXiv
- Google Scholar
- Grey literature

**Search Terms:**
```
("large language model*" OR "LLM" OR "GPT" OR "BERT" OR "transformer*" OR "foundation model*")
AND
("sentiment analysis" OR "sentiment classification" OR "opinion mining")
AND
("financial" OR "stock" OR "cryptocurrency" OR "forex" OR "market*")
```

**Inclusion Criteria:**
1. Analyzed financial markets (stocks, cryptocurrency, forex, commodities)
2. Employed sentiment analysis methods using LLMs
3. Reported quantitative performance metrics
4. Represented empirical research (not purely theoretical)

**Exclusion Criteria:**
1. Not focused on financial sentiment analysis
2. No LLM methods used
3. No quantitative results reported
4. Non-English language
5. Duplicate publications

### Quality Assessment

Studies evaluated using 7-criteria framework (0-10 scale):

1. **Research Design** (0-2): Clarity of objectives and methodology
2. **Data Quality** (0-2): Dataset size, representativeness, documentation
3. **Model Description** (0-1): Architecture and configuration details
4. **Evaluation Rigor** (0-2): Appropriate metrics, baselines, validation
5. **Statistical Testing** (0-1): Significance tests reported
6. **Reproducibility** (0-1): Code/data availability
7. **Limitations** (0-1): Acknowledged weaknesses

**Quality Tiers:**
- High: ≥7 points (36 studies, 30.5%)
- Medium: 5-6 points (46 studies, 39.0%)
- Low: 3-4 points (36 studies, 30.5%)

## Key Findings

### Model Architecture Distribution

| Architecture | Adoption | Mean Performance |
|--------------|----------|------------------|
| BERT variants | 58.3% | +2.84 pp accuracy |
| GPT models | 23.6% | +3.12 pp accuracy |
| Domain-specific (FinBERT) | 30.6% | +4.1 pp accuracy |
| Hybrid (LLM + time-series) | 50.0% | +7.75 pp peak |

### Market Coverage

| Asset Class | Coverage | Gap |
|-------------|----------|-----|
| Stocks | 38.1% | Moderate |
| Cryptocurrency | 32.2% | Moderate |
| Forex | 4.2% | Critical |
| Commodities | 0.8% | Critical |
| Bonds/Derivatives | 0% | Critical |

## Limitations

1. **Search Period:** Cut-off January 2026 may miss recent publications
2. **Language:** English-only studies included
3. **Publication Bias:** Grey literature search limited
4. **Quality Variation:** 69.5% of studies scored below 7/10
5. **Statistical Testing:** Only 13.9% of high-quality studies report significance tests

## Reproducibility

All data extraction was performed independently by two reviewers with inter-rater reliability assessment:
- Cohen's Kappa (screening): 0.85
- Inter-rater agreement (quality): 0.89

Discrepancies resolved through discussion and consensus.

## License

This dataset is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute the material
- **Adapt** — remix, transform, and build upon the material

Under the following terms:
- **Attribution** — You must give appropriate credit and indicate if changes were made

## Contact

**Author:** Ing. Samuel Seidel
**Institution:** Faculty of Informatics and Management, University of Hradec Králové
**Email:** [Your email]

## Acknowledgments

- Research community for making preprints and code openly available
- PRISMA 2020 guidelines for systematic review methodology
- All authors whose work contributed to this systematic review

## Version History

- **v1.0.0** (2026-02-10): Initial release
  - 118 studies included
  - Complete PRISMA 2020-compliant dataset
  - 7 publication-quality figures

## Related Resources

- Manuscript: [Link to published article when available]
- PRISMA Checklist: See `documentation/PRISMA_CHECKLIST.md`
- Analysis Code: [Link to analysis scripts if public]

---

**Last Updated:** February 10, 2026
**Dataset Version:** 1.0.0
**DOI:** Pending
