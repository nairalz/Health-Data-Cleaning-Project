# Health-Data-Cleaning-Project
Data Preparation &amp; Exploration with Power Query (Excel &amp; Power BI)
The data comes from the OECD (Organisation for Economic Co-operation and Development) and covers several key dimensions of public health and well-being across member countries.

Through this project, I learned how to:

Import, clean, and prepare multi-source datasets.

Manage inconsistent structures and missing values.

Detect and resolve duplicate or conflicting records.

Build complete data grids and heatmaps to visualize data availability.

Prepare clean, analysis-ready tables for Power BI.

📊 Datasets Used

The project is based on five OECD datasets, all related to population health and healthcare systems:

#	Dataset	Focus	Key Measures
1	Perceived Health Status	Self-reported health	% of population by sex, age, and health category
2	Perceived Health Status by Socio-Economic Status	Self-reported health (by income)	% of population reporting good/very good health
3	Health Expenditure and Financing	System financing	% of GDP, PPP per person by financing scheme
4	Patient Experiences (Financial Barriers)	Access to healthcare	% skipping consultations, tests, or medicines due to cost
5	Risk Factors for Health	Lifestyle habits	% of daily smokers
🌍 Reference Countries

I selected 10 OECD countries to ensure diverse health system models and socio-economic profiles:

🇨🇭 Switzerland (focus country)
🇫🇷 France – 🇩🇪 Germany – 🇮🇹 Italy – 🇪🇸 Spain – 🇬🇷 Greece – 🇸🇪 Sweden – 🇳🇴 Norway – 🇨🇦 Canada – 🇯🇵 Japan

This subset allowed me to explore data relationships and make meaningful cross-country comparisons.

⚙️ Power Query Workflow (ETL Light)
1. Extract

Imported data from OECD CSV/Excel files.

Created Connection Only queries to keep the workbook efficient.

2. Transform

Reference Queries → create filtered versions without altering raw data.

Merge Queries → join with the reference countries table to keep only selected nations.

Expand Columns → extract fields from nested tables.

Change Type with Locale → fix regional number formatting issues (e.g., 58.2 vs 58,2).

Remove Columns / Rows → exclude irrelevant indicators (e.g., “Mode of provision”).

Duplicate Queries → experiment without affecting main datasets.

Group By → aggregate observations where necessary (e.g., average of subcategories).

Add Columns → create flags and data completeness checks.

3. Load

Clean datasets loaded into Excel (tables named PR_*).

Raw datasets kept as Connection Only queries.

🔍 Data Quality Assessment

To evaluate data coverage and consistency, I built reference grids combining all dimension values:

Country × Sex × Age × Health Status × Year

Using these grids, I visualized data completeness with heatmaps.

Findings:

Perceived Health Status: complete from 2010–2015, partial afterwards; Japan reports every 3 years.

Socio-economic status: good coverage overall.

Financing & Expenditure: highly variable availability depending on indicator.

Patient Experience: sporadic coverage across countries and years.

Risk Factors: missing values for Germany, Austria, and Switzerland; better for Greece and Japan.

This step was crucial to understanding which analyses were possible and where caution was required.

🧮 Duplicate & Conflict Resolution

Detected “duplicate” rows using Keep Duplicates in Power Query.

Identified that many were not true duplicates, but observations differing by hidden dimensions such as “mode of provision” or “type of care”.

Decided not to reintroduce those detailed columns to maintain a simplified but coherent analytical level.

When necessary, applied aggregation by average to merge overlapping records.
