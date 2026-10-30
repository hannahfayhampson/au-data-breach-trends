# 🔐 Australian Data Breach Trends

Analysing Australian data breach trends to identify key cyber risks.

> 🚧 **Work in progress.** Key findings and charts will be added here as the analysis develops.

---

## 🎯 The question

**What is driving data breaches in Australia, and where is the risk concentrated?**

1. How have breach numbers changed since mandatory reporting began in 2018?
2. What is the split between malicious attacks, human error and system faults, and how is it shifting?
3. Which sectors are hit hardest, and how do their causes differ?
4. How quickly are organisations identifying and reporting breaches?
5. Based on this, what are the top three risks organisations should prioritise?

## ✨ Key findings

*Coming soon.*

## 📥 Data

Source: Office of the Australian Information Commissioner (OAIC) Notifiable Data Breaches reports, published half-yearly.

- `data/raw/` holds figures as compiled from the reports
- `data/processed/` holds cleaned, analysis-ready data

## 🛠️ Methods & tools

`Python` · `pandas` · `matplotlib` · `seaborn` · `scipy` · `Jupyter`

## 📁 Project structure

```
au-data-breach-trends/
├── data/
│   ├── raw/            # data as collected from OAIC reports
│   └── processed/      # cleaned data used in the analysis
├── notebooks/          # Jupyter notebooks, numbered in order
├── images/             # charts used in this README
├── reports/            # board risk briefing
├── requirements.txt    # Python packages
└── README.md
```

## ⚠️ Limitations

*Coming soon.*

## ▶️ How to run it

```bash
git clone https://github.com/hannahfayhampson/au-data-breach-trends.git
cd au-data-breach-trends
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Then open the notebooks in `notebooks/` in order.
