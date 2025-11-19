# Shadows of Transparency

This repository contains the code and analysis for the paper **"Shadows of Transparency: Assessing Government Transparency Using Public Data"** (in preparation).

The work builds on the Woogle dataset and its accompanying notebook [1], analyzing patterns in Dutch Freedom of Information Act (FOIA/Woo) documents. The dataset is available through DANS [2].

## Overview

This project implements six transparency anti-patterns to systematically assess government transparency practices:

1. **Narrow Reading** - Analyzing unusually small dossier sizes
2. **Overbroad Reading** - Analyzing unusually big dossier sizes
2. **Obstructive Formatting** - Evaluating document accessibility using FAIRIscore
3. **Excessive Redaction** - Measuring redaction rates across documents
4. **Catch-All Exemptions** - Tracking usage of FOIA exemption grounds
5. **Stale Release** - Analyzing response times

## Dataset

The analysis uses three main dataframes from the Woogle dataset:

- **Bodytext dataframe**: Page-level text content and metadata
- **Document dataframe**: Document-level information
- **Dossier dataframe**: Dossier-level metadata including request/decision dates

The dataset focuses on passively released documents (category '2i') from Dutch government ministries.

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Minimum 8GB RAM (dataset processing can be memory-intensive)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/joszuijderwijk/shadows-of-transparency.git
   cd shadows-of-transparency
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

### Data Setup

1. **Download the Woogle dataset** from DANS:
   - Visit: https://doi.org/10.17026/DANS-ZAU-E3RK
   - Download the following files:
     - `woo_bodytext_2i.csv.gz`
     - `woo_documents.csv.gz`
     - `woo_dossiers.csv.gz`

2. **Create a data directory** and place the downloaded files:
   ```bash
   mkdir data
   # Move the downloaded .csv.gz files to the data/ directory
   ```

3. **Update the data path** (if needed):
   - Open `SOT.ipynb`
   - Locate the cell with `DATAFRAME_FOLDER = 'data'`
   - Update the path if you placed the data files elsewhere

### Running the Analysis

1. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook SOT.ipynb
   ```

2. **Run the cells sequentially**
   - Start with the import cell
   - The dataset loading may take several minutes
   - Each analysis section can be run independently after loading the data

### Expected Outputs

The notebook generates several visualizations and analyses:

- **General statistics**: Dataset overview (dossiers, documents, pages)
- **Time-series plots**: Documents and dossiers by year
- **Anti-pattern analyses**:
  - Dossier size distributions (local and global percentiles)
  - FAIRIscore trends by ministry
  - Redaction rate analysis
  - Exemption ground usage patterns
  - Response time analysis

Output files include:
- `big_small_dossiers.png`
- `big_small_dossiers_global.png`
- `fairscores_ministry_over_time.png`
- `redaction_ministry_over_time.png`
- `exemptions_single_plot.png`
- `exemptions_ministry_over_time.png`


## Troubleshooting

**Memory issues**: If you encounter memory errors, try:
- Closing other applications
- Processing data in smaller chunks
- Using a machine with more RAM

**Missing data files**: Ensure all three CSV files are downloaded and placed in the `data/` directory.

**Import errors**: Verify all required packages are installed using `pip list`.

## References

[1] van Heusden, R., Larooij, M., Kamps, J. et al. A collection of FAIR Dutch Freedom of Information Act documents. *Sci Data* 12, 795 (2025). https://doi.org/10.1038/s41597-025-05052-2

[2] M. Marx, 2023, "A collection of FAIR Dutch Freedom of Information Act documents", https://doi.org/10.17026/DANS-ZAU-E3RK, DANS Data Station Social Sciences and Humanities, V4


## Citation

If you use this code or analysis in your research, please cite:

```
Zuijderwijk, J., Beerepoot, I., Martens, T., Knies, E., Van der Lippe, T., & Reijers, H. A. (2025). Shadows of Transparency: Assessing Government Transparency Using Public Data [Manuscript under review].
```

## Contact

Jos Zuijderwijk - `a.j.h.zuijderwijk [at] uu [dot] nl`


## Acknowledgments

This work builds on the Woogle dataset created by van Heusden et al. and made available through DANS.
