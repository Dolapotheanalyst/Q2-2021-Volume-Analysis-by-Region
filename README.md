# Q2-2021-Volume-Analysis-by-Region
This project analyzes regional volume trends in Q2 2021, focusing on customer attrition, growth slowdowns, and onboarding effects
#Q2 2021 Volume Analysis by Region

#📩 Email Request
The board is asking to see how volume looks in Q2. I got some data gathered! But didn’t have a chance to pull anything together and was hoping you could take a stab at it.
I think they just want to see the Q2 2021 volume by region and wanted to know if everything was looking good. I think this file has what you need.
I don’t remember all the region codes – I know NAAM ends in 1, EMEA ends in 3, and APAC and LATAM are 2 and 4, but I don’t remember which is which. I do know LATAM has the lowest volume, so just go ahead and assign that to whichever comes out lowest.

##🛠 Data Cleaning
🔹 Handling Wrapped Data
I discovered the data was wrapped together, which didn’t look good, so I:
Unwrapped it using the Wrap/Unwrap Text option in Excel’s Home ribbon.
AutoFit the column width using the Format ribbon extension.

🔹 Structuring the Dataset
I created a table using Ctrl + T and named it "Volume by Client", since this dataset represents client volume.
I checked for blanks using the Filter option—there were none, meaning the dataset was complete.

🔹 Formatting Date and Volume Columns
The Date column was stored as text, so I converted it using Text to Columns.
The Volume column was also stored as text, so I reformatted it to Number for accurate calculations.

🔹 Cleaning the GEOID Dataset
I checked the GEOID dataset (Client Geography data) and applied similar formatting:
Unwrapped text
AutoFit column width
Converted to a table named "Geo by Client"
I checked for duplicates and blank values—there were none for Client ID, meaning the dataset was in good shape.
However, the GeoID column contained several duplicates.

I copied it to a new sheet and removed duplicates, leaving the following unique codes:
Geo001
Geo002
Geo003
Geo004

📍 Assigning Region Names
Since the email provided hints about regional codes:
Geo001 = NAAM (ends in 1)
Geo003 = EMEA (ends in 3)
Geo002 and Geo004 were unassigned.
The email mentioned that LATAM had the lowest volume, so I had to determine which GeoID had the lowest total volume and assign LATAM accordingly.

🔍 Data Matching Using XLOOKUP
To link GeoID from the Geo dataset to the Client ID in the Volume dataset:
I noticed that Client ID in the Volume dataset had 7 characters, while in the Geo dataset, it had 9 characters due to the "C-" prefix.
I extracted the relevant portion using the A-Right function to make them match.
Using XLOOKUP, I assigned the correct GeoID to each Client ID in the Volume dataset.

📊 Volume Analysis by Region
Since LATAM had the lowest volume, I used SUMIFS to determine the total volume per region:
Region	GeoID	Total Volume
NAAM	Geo001	3,002,286
EMEA	Geo003	830,760
APAC	Geo002	562,005
LATAM	Geo004	425,262
✔ LATAM had the lowest volume, as expected.
✔ Regional assignments were now properly mapped.
✔ The volume distribution for Q2 2021 was confirmed.

🔍 Discoveries Using Pivot Table
Customer Attrition in LATAM
2 customers left the LATAM region in Q2, removing 7k in volume from the dataset.
Q2 Growth Slowdown
Q1 growth was 4%, but it slowed to 2.7% in Q2, primarily due to:
0.7% (7k volume) decline from the loss of two customers in LATAM.
LATAM’s overall growth rate dropped from 9% in Q1 to flat in Q2 (year-on-year).
NAAM Region Onboarding Impact
Clients onboarded in Q2 2020 in the NAAM region anniversaried in Q2 2021, making the perceived growth appear slower.

✅ Final Data Integration
To streamline reporting, I merged all the cleaned and structured data into a single "Volume Data" worksheet. Using XLOOKUP, I assigned the appropriate Region Names for each GeoID.
#Key Techniques
Data Cleaning & Formatting
Pivot Table Analysis
XLOOKUP & SUMIFS for Data Mapping
Identifying Business Insights from Volume Trends

📝 Key Features
📌 Automated Data Cleaning using Excel functions
📊 Pivot Table Analysis to track volume movements
🔍 Business Insights on customer churn and revenue shifts
📈 Growth Trend Analysis across different regions

🎯 Key Takeaways
✔ Data cleaning ensured accuracy—formatting, handling missing values, and standardizing IDs improved the dataset.
✔ XLOOKUP and SUMIFS simplified analysis, making it easy to assign regions and calculate totals.
✔ Pivot Tables uncovered key business insights, including customer attrition, slowed growth, and onboarding effects.
✔ GitHub Portfolio Project showcases Excel skills, data analysis, and business intelligence insights.

