#  Q2 2021 Volume Analysis by Region  
### Comprehensive Data Cleaning, Transformation & Business Insight Project

This project focuses on analyzing Q2 2021 volume performance across global regions. It includes full data cleaning, data restructuring, Excel-based analytics, regional mapping, XLOOKUP transformation, SUMIFS aggregation, and Pivot Table insight generation. The goal was to prepare a polished, board-ready summary of regional performance — including volume distribution, customer attrition, onboarding effects, and quarter-over-quarter (QoQ) growth trends.

---

#  Email Request (Project Background)

The analysis was initiated based on a request from the company’s board.  
The forwarded email provided limited but crucial context:

- “We need to see how Q2 2021 volumes look by region.”
- “I don’t remember all the region codes… NAAM ends in 1, EMEA ends in 3, APAC and LATAM are 2 and 4.”
- “LATAM has the lowest volume — so assign LATAM to whichever code ends up lowest.”
- “The dataset attached should contain everything you need.”

This meant the dataset contained:

- **Volume data by client** for Q2 2021  
- **Client-to-Region** mapping via **Geo Codes (GeoID)**  
- But **region names were NOT given**, so we had to infer and validate region → GeoID assignments.

This project replicates the real-world challenge of **working with incomplete documentation**, requiring:

- Logical deduction  
- Business understanding  
- Careful data cleaning  
- Analytical validation  

---

#  Data Cleaning & Preparation

The raw datasets required significant cleaning before analysis.

---

##  Handling Wrapped & Unstructured Data  
The Volume dataset arrived with wrapped text and inconsistent formatting, making it visually messy and prone to errors. To prepare it for analysis:

- Unwrapped the data using **Home → Wrap Text (off)**  
- AutoFit all columns for readability  
- Converted the dataset into an Excel table (`Ctrl + T`) named **Volume by Client**  
- Applied filters to check for blank values — **none were found**, meaning the dataset was complete and reliable

This step established a clean, structured base for further transformation.

---

##  Fixing Data Type Issues  
Two major fields were incorrectly formatted as text:

### 1️ Date Column  
Dates were stored as strings.  
- Used **Text to Columns** to convert to real date values  
- Ensured Excel recognized them as valid date objects for sorting and filtering

### 2️ Volume Column  
Volume values were numeric but stored as text.  
- Reformatted to **Number**  
- Ensured accurate calculations for SUMIFS and Pivot Tables  
- Eliminated trailing spaces and formatting noise

Incorrect data types are a leading cause of calculation errors — correcting them ensures accurate aggregation later.

---

##  Cleaning the GEOID (Client Geography) Dataset  
The Client Geography file contained Client IDs and GeoIDs.  
Cleaning steps included:

- Unwrapped text for readability  
- AutoFit column widths  
- Converted to a structured table named **Geo by Client**  
- Checked for duplicates or missing Client IDs — none found  
- Detected **duplicate GeoIDs**, requiring a uniqueness check

After removing duplicates, four valid GeoIDs remained:

- **Geo001**  
- **Geo002**  
- **Geo003**  
- **Geo004**

These four codes represent NAAM, EMEA, APAC, and LATAM — but their mapping had to be logically derived.

---

#  Assigning Regions to GEOID Codes

The email provided incomplete mapping information:

- Region codes ending in **1 → NAAM**  
- Ending in **3 → EMEA**  
- Codes ending in **2 or 4 → APAC or LATAM (order unknown)**  
- “LATAM has the lowest volume.”

###  Step 1: Assign known codes  
- **Geo001 → NAAM**  
- **Geo003 → EMEA**

###  Step 2: Determine APAC vs LATAM  
To determine which GeoID represented APAC vs LATAM:

1. Calculated total volume for Geo002 and Geo004  
2. The one with **lower total volume** was assigned to LATAM  
3. The remaining GeoID became APAC  

This ensures the region mapping is **data-driven**, not guessed.

---

#  Data Matching Using XLOOKUP

A major challenge arose:  
**Client IDs in the Volume dataset did not match Client IDs in the Geo dataset.**

- Volume dataset IDs = **7 characters**  
- Geo dataset IDs = **9 characters**, including `"C-"` prefix

To resolve:

1. Extracted the last characters using **RIGHT()**  
2. Used **XLOOKUP** to match cleaned Client IDs  
3. Retrieved **GeoIDs** for each client  
4. Used **XLOOKUP** again to map GeoIDs → Region Names

This created a fully connected dataset linking:

**Client → GeoID → Region → Volume**

---

#  Q2 2021 Volume Summary by Region

After assigning region names and aggregating volumes:

| Region | GeoID  | Total Volume |
|--------|--------|--------------|
| **NAAM** | Geo001 | **3,002,286** |
| **EMEA** | Geo003 | **830,760** |
| **APAC** | Geo002 | **562,005** |
| **LATAM** | Geo004 | **425,262** |

###  LATAM confirmed as lowest-volume region  
###  Region assignments validated  
###  Q2 performance accurately reflected  

---

#  Insights from Pivot Table Analysis

Pivot Tables were used to uncover hidden trends behind Q2 performance.

---

##  1. Customer Attrition in LATAM  
- 2 customers churned in Q2  
- Resulting in **7k reduction** in total volume  
- LATAM’s growth trajectory was heavily impacted  
- Demonstrates the sensitivity of low-volume regions to customer churn

---

##  2. Growth Slowdown from Q1 → Q2  
Growth analysis revealed:

- **Q1 Growth:** 4%  
- **Q2 Growth:** 2.7%  

Breakdown:

- **0.7% decrease** from LATAM churn  
- LATAM year-on-year (YoY) growth:  
  - Q1 → **9%**  
  - Q2 → **0%**  
- Reduction due to no new clients and churn impact

This shows how regional performance contributes to global growth trends.

---

##  3. NAAM Onboarding Anniversary Effect  
Many NAAM clients who onboarded in Q2 2020 “anniversaried” in Q2 2021.

This meant:

- Their volume no longer counted as incremental growth  
- Growth metrics appeared slower  
- Revenue normalization occurred as onboarding effects tapered off

This is a real-world phenomenon seen in subscription and volume-driven businesses.

---

#  Final Data Integration

All transformed data was merged into a single sheet named **Volume Data**, containing:

- Cleaned Volume Data  
- Geo Mapping  
- Region Assignment  
- Final Aggregated Metrics  

This streamlined the entire analysis and enabled board-ready reporting.

---

#  Key Techniques Demonstrated

- Advanced Excel Data Cleaning  
- Text Unwrapping & AutoFormatting  
- Text-to-Columns Conversion  
- Numeric Formatting & Standardization  
- XLOOKUP for dataset merging  
- RIGHT() for string extraction  
- SUMIFS for metric aggregation  
- Pivot Table Analytics  
- Business Insight Interpretation  
- Region Classification Logic  

This project mirrors real corporate analytics workflows where datasets are:

- Messy  
- Incomplete  
- Poorly labeled  

And must be structured and interpreted with precision.

---

#  Key Features of This Project

- Detailed data cleaning and preparation workflow  
- Accurate regional volume assignment  
- Logical deduction based on available metadata  
- Churn and growth trend analysis  
- Quarter-over-quarter performance narrative  
- Clear business intelligence insights  
- Strong Excel-based analytics demonstration  

---

#  Key Takeaways

✔ Clean data leads to reliable insights  
✔ XLOOKUP and SUMIFS make multi-source merging efficient  
✔ Pivot Tables reveal the root causes behind growth shifts  
✔ LATAM’s low volume magnifies churn effects  
✔ NAAM’s onboarding anniversary explains stabilize growth  
✔ APAC and EMEA show moderate, stable volume patterns  
✔ This project is ideal for showing real-world data analyst skills  

---

#  Author
**Adewumi Dolapo**  
Data Analyst | Excel | Business Intelligence | Data Cleaning | Reporting
