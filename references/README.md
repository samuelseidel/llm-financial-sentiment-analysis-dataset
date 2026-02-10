# References - Included Studies

This folder contains the complete bibliography for all studies included in the systematic review.

## Files

### `included_studies_list.csv`

Clean, standalone reference list for all included studies.

**Columns:**
- `Citation_Key`: Unique identifier (e.g., "Dakalbab2025")
- `Author`: Author names (full list)
- `Year`: Publication year
- `Title`: Article title

**Format:** CSV (comma-separated values)
**Encoding:** UTF-8
**Use cases:**
- Quick reference lookup
- Import into reference managers
- Citation verification

### `included_studies.bib`

BibTeX bibliography file for all included studies.

**Format:** BibTeX
**Entry type:** @article
**Fields:** author, title, year
**Use cases:**
- LaTeX manuscript citations
- Import into reference managers (Zotero, Mendeley, EndNote)
- Automated bibliography generation

## Usage

### Import into Zotero
1. File → Import → Select `included_studies.bib`
2. All 90+ studies will be imported

### Import into Mendeley
1. File → Import → BibTeX → Select `included_studies.bib`

### Use in LaTeX
```latex
\bibliography{included_studies}
\cite{Dakalbab2025}
```

### Load in Python
```python
import pandas as pd

# Load reference list
refs = pd.read_csv('references/included_studies_list.csv')

# Search by author
dakalbab = refs[refs['Author'].str.contains('Dakalbab')]

# Filter by year
recent = refs[refs['Year'] >= 2024]
```

### Load in R
```r
# Load reference list
refs <- read.csv('references/included_studies_list.csv')

# Search by author
dakalbab <- refs[grepl("Dakalbab", refs$Author), ]

# Filter by year
recent <- refs[refs$Year >= 2024, ]
```

## Note on Study Count

The main dataset (`SYNTHESIS_DATA_READY.csv`) contains the subset of studies for which complete data extraction was performed. The full list of all 118 screened studies can be found in:
- `data/screening/full_text_assessment_results.csv` (118 studies assessed)
- `data/extraction/SYNTHESIS_DATA_READY.csv` (90 studies with complete data)

## Citation

When citing specific studies from this review, use the Citation_Key to look up the full reference.

Example:
```bibtex
@article{Dakalbab2025,
  author = {Dakalbab, Fatima Mohamad and Kumar, Ayush and Abu Talib, Manar and Nasir, Qassim},
  title = {Advancing Forex prediction through multimodal text-driven model and attention mechanisms},
  year = {2025}
}
```

## Additional Information

For complete bibliographic details including:
- Publication venue
- DOI/URL
- Geographic origin
- Dataset details
- Performance metrics

See the main synthesis file: `data/extraction/SYNTHESIS_DATA_READY.csv`

---

**Last Updated:** February 10, 2026
**Total Studies:** 90 (with complete data extraction)
