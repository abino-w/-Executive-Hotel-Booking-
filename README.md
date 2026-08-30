# Executive Hotel Booking EDA — Day 15 Assignment

End-to-end Exploratory Data Analysis (EDA) of a hotel booking dataset, covering data
quality assessment, cleaning, univariate/bivariate/group-wise/correlation analysis,
visualization, and executive-level business insights and recommendations.

## Files in this Submission

| File | Description |
|---|---|
| `Day15_Hotel_Booking_EDA.ipynb` | Full Jupyter/Colab notebook with all code, charts, and narrative markdown cells. Runs end-to-end. |
| `Executive_Hotel_Booking_EDA_Report.docx` | Executive-ready Word report summarizing findings, charts, insights, and recommendations for management. |
| `Day15_Executive_Hotel_Booking_EDA_Dataset.csv` | Source dataset (25,180 hotel bookings, 35 columns). |
| `README.md` | This file. |

## Dataset

- **Rows:** 25,180 bookings (24,994 after cleaning)
- **Columns:** 35 (booking logistics, guest profile, commercial terms, room details, outcomes)
- **Hotel types:** City Hotel, Resort Hotel
- **Locations:** 10 cities (London, Lisbon, Dubai, Barcelona, Amsterdam, Maldives, Algarve, Bali, Phuket, Goa)

## Workflow

1. **Data Understanding** — shape, dtypes, summary statistics
2. **Data Quality Assessment** — missing values, duplicate records, inconsistent
   categorical values (casing/whitespace), invalid dates, out-of-range scores, IQR outliers
3. **Data Cleaning & Preprocessing** — deduplication, text standardization, date
   parsing, missing-value imputation, indicator flags for `Agent_ID`/`Company_ID`
4. **Univariate Analysis** — distributions of hotel type, lead time, ADR, reservation status
5. **Bivariate & Group-wise Analysis** — cancellation by hotel type/lead time/deposit type,
   ADR by market segment, monthly booking trend, satisfaction vs. waiting list, revenue by location
6. **Correlation Analysis** — full numeric correlation heatmap
7. **Key Business Insights** — 5 findings
8. **Recommendations for Management** — 7 action items

## How to Run the Notebook

1. Open `Day15_Hotel_Booking_EDA.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
2. Make sure `Day15_Executive_Hotel_Booking_EDA_Dataset.csv` is in the **same directory**
   as the notebook (or update the file path in the first data-loading cell if using Colab
   with a different upload location).
3. Install dependencies if needed:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
4. Run all cells top to bottom (`Run All` / `Runtime > Run all` in Colab).

## Key Findings (Summary)

- **Overall cancellation rate: 72.2%** — high and consistent across hotel types and segments.
- **Lead time** is the strongest driver of cancellation (peaks at 85.8% for 181–365 day
  bookings), correlation +0.34 with `Is_Canceled`.
- **Deposit type anomaly:** "Non-Refund" bookings cancel 93.0% of the time — far higher
  than "Refundable" (54.7%) or "No Deposit" (51.6%), the opposite of the policy's intent.
- **Revenue exposure:** $9.6M in booked revenue was never realized vs. $3.8M collected —
  a nearly 3:1 gap.
- **Satisfaction** drops from 3.88 (no wait) to 3.19 (51+ days on waiting list); Online TA
  is both the highest-volume and highest-cancellation market segment (75.1%).

See the notebook or Word report for full detail, charts, and the complete list of
recommendations.

## Notes

- Outliers (ADR, Total_Nights, Estimated_Revenue) were retained rather than removed —
  they reflect legitimate long-stay/high-rate bookings, not data errors.
- `Company_ID` is missing for 82.3% of records by design (only applies to corporate
  bookings) and was converted to a `Has_Company` binary flag instead of being imputed
  or used to drop rows.
