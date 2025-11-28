# Africa Debt Data Downloader

A tiny static web app that generates **official World Bank CSV/ZIP download links** for debt indicators, per African country.  
No backend, no build step – just a single `index.html` file.

Live site: **https://isnakolah.github.io/debt-indicator/**

---

## What it does

- Lets you select:
  - Any of the **54 African countries**, or
  - **All African Countries (54)** using a multi-country World Bank API call.
- Shows groups of datasets by **source**:
  - **World Bank – International Debt Statistics (IDS)**  
    - External debt stocks & structure  
    - Debt service & repayments
  - **Other sources & portals** (links only):
    - IMF World Economic Outlook (WEO)
    - IMF Global Debt Database (GDD)
    - AfDB Africa Debt portal
    - African Debt Database (ADD)
- For each World Bank indicator:
  - Builds the correct `downloadformat=csv` ZIP URL for the selected country.
  - Provides a **“Download CSV (World Bank)”** button.
  - Shows the underlying API URL for copy/paste into scripts.

All logic is client-side JavaScript; nothing is stored or tracked.

---

## Data sources

The app only *builds links*; the data itself is served directly by:

- **World Bank Data API – International Debt Statistics (IDS)**  
  - API: `https://api.worldbank.org/v2/country/{country}/indicator/{indicator}?downloadformat=csv`  
  - Datasets such as:
    - `DT.DOD.DECT.CD` – External debt stocks, total (current US$)  
    - `DT.DOD.DECT.GN.ZS` – External debt stocks (% of GNI)  
    - `DT.TDS.DECT.CD` – Total external debt service (current US$)  
    - …and related ratios and flows.

Linked portals (no data is proxied):

- IMF World Economic Outlook & Global Debt Database  
- African Development Bank (AfDB) debt portal  
- African Debt Database (ADD)

---

## Using the site

1. Open: **https://isnakolah.github.io/debt-indicator/**
2. Choose a **country** from the dropdown  
   (or “All African Countries (54)” for a multi-country download).
3. Scroll through the grouped datasets.
4. Click **“Download CSV (World Bank)”** for any dataset.  
   - Your browser downloads a ZIP from the World Bank.  
   - Inside the ZIP you’ll find a `..._Data.csv` file with the time series.
5. Use the **indicator details** / **data portal** buttons to read metadata or explore more series.

---

## Local development

No build tools required.

Clone the repo:

```bash
git clone https://github.com/isnakolah/debt-indicator.git
cd debt-indicator
