# RUSH Sales Intelligence

An end-to-end sales analytics project for a fictional sportswear company, built to demonstrate **data-quality investigation, multi-table transformation, validation, business analysis, interactive decision support, and stakeholder communication**.

The project combines a documented Python analysis with a deployed Streamlit dashboard that lets users explore sales performance by product, retailer, geography, month, and sales method.

**🚀 [Open the live Streamlit dashboard](https://rushsalesintel.streamlit.app/)**  
**🎥 [Watch the 5-minute stakeholder walkthrough](https://www.loom.com/share/695c7e9aa12f4c85ae3d20fb9c4abcac)**

## Business questions

The analysis was designed to answer management questions such as:

1. Which product category generated the most sales in 2021?
2. Which states led women's and men's product sales?
3. Which retailer purchased the most units in 2021 and 2020?
4. How do sales patterns vary by geography, product category, retailer, month, and sales method?

## Stakeholder walkthrough

The recorded presentation is structured as a short readout to a sales team. It walks through the project from the raw source files to the final interactive dashboard, including:

- loading and exploring three source tables in Google Colab,
- checking nulls, duplicates, unexpected values, and data types,
- investigating non-unique retailer identifiers created from region/state/city combinations,
- distinguishing duplicate retailer records where the source data supported a defensible assignment,
- moving from cleaned tabular data into a more accessible Streamlit experience,
- and answering the sales team's questions using interactive filters and visualizations.

The walkthrough also highlights broader patterns beyond the requested questions, including the large change in sales between 2020 and 2021 and visible monthly trends.

The goal was not only to perform the analysis, but to **explain the process and results in plain language to a nontechnical audience**.

## Why this project matters

The interesting part of the work was not simply calculating totals. The source tables contained **duplicate and conflicting retailer identifiers**, which meant a straightforward merge could produce misleading results.

Instead of forcing every record into a clean-looking answer, the workflow:

- investigated conflicting retailer/location IDs,
- corrected records only where order patterns provided sufficient evidence,
- preserved unresolved records when the source data did not support a defensible assignment,
- retained unmatched transactions for valid product and total-sales analysis,
- and validated that the final merge did not silently add or remove sales records.

That approach prioritizes **traceability and analytical integrity over cosmetic completeness**.

## Interactive dashboard

The live Streamlit dashboard lets users explore the cleaned sales data without needing to work directly in the notebook or source tables.

It provides filters for:

- Year
- State
- Product category
- Specific product

It includes:

- Total sales, units sold, and order KPIs
- Executive insight cards based on the active filters
- U.S. sales concentration map
- State-level hover details
- Product-category sales analysis
- Monthly sales trends
- Retailer performance tables

The visual design uses a Grateful Dead-inspired palette while keeping the analysis focused on the business results.

## What this project demonstrates

- **Data cleaning:** duplicate identifiers, unmatched records, conflicting reference data
- **Data modeling:** combining transaction, product, and retailer tables
- **Validation:** checking record counts and merge behavior before analysis
- **Business analysis:** converting raw transactions into management-level answers
- **Interactive BI:** building and deploying a filterable Streamlit/Plotly dashboard
- **Stakeholder communication:** explaining technical cleaning decisions and business findings in a short sales-team presentation
- **Analytical judgment:** documenting uncertainty rather than fabricating precision

## Project workflow

1. Load and profile the raw source tables.
2. Review key fields, data types, nulls, and uniqueness.
3. Investigate conflicting retailer IDs and location mappings.
4. Apply evidence-based corrections where possible.
5. Preserve unresolved records explicitly.
6. Merge sales, product, and retailer tables.
7. Validate the merged dataset against the source transactions.
8. Calculate sales dollars and analysis fields.
9. Answer management questions and explore broader trends.
10. Export an analysis-ready dataset for the Streamlit dashboard.
11. Deploy the interactive dashboard and present the workflow and findings in a stakeholder-facing video walkthrough.

## Data

The project uses three source tables:

- `TABLE_SALES_885.csv` — transaction-level sales data
- `TABLE_PRODUCTS_885.csv` — product names and product IDs
- `TABLE_RETAILER_885.csv` — retailer and location information

The cleaned analysis table is:

- `rush_cleaned_sales.csv`

Additional field documentation is available in [`data/README.md`](data/README.md).

## Repository structure

```text
rush-sales-intelligence/
├── GB885_Final_Project_Haskett_C.ipynb   # Full EDA, cleaning, validation, and analysis
├── app.py                                # Deployed Streamlit sales dashboard
├── requirements.txt
├── README.md
└── data/
    ├── README.md
    ├── TABLE_PRODUCTS_885.csv
    ├── TABLE_RETAILER_885.csv
    ├── TABLE_SALES_885.csv
    └── rush_cleaned_sales.csv
```

## Run the dashboard locally

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

## Analysis notebook

The Jupyter notebook documents the full analytical process, including exploratory analysis, data-quality investigation, cleaning decisions, merge validation, and the final business analysis.

Because the raw CSV files are stored in the repository, the analysis is reproducible without manual file uploads.

## Tools

**Python · pandas · Streamlit · Plotly · Jupyter · Google Colab · GitHub**
