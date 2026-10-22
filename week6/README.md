# Healthcare Data – Exploratory Data Analysis

An exploratory data analysis of a preprocessed healthcare dataset, covering patient demographics, medical conditions, admission types, billing amounts and insurance providers. The analysis is in `edatask6.py`, exported from a Google Colab notebook (`edatask6.ipynb`), and uses pandas, NumPy, Matplotlib and Seaborn.

## Dataset

**File:** `healthcare_preprocessed (1).csv`

Columns used in the analysis:

| Column | Description |
|---|---|
| `Age` | Patient age |
| `Gender` | Patient gender |
| `Medical_Condition` | Diagnosed medical condition |
| `Admission_Type` | Type of hospital admission |
| `Admission_Date` | Date of admission (converted to a datetime) |
| `Billing_Amount` | Amount billed for the stay |
| `Insurance_Provider` | Patient's insurance provider |

## What the analysis covers

1. **Overview** – loads the data and checks `head()`, row and column counts, column names and `info()`.
2. **Patient demographics**
   - Age distribution (histogram with KDE)
   - Age distribution split by gender
   - Gender distribution (bar chart)
3. **Medical conditions**
   - Count of patients per condition
   - Condition distribution by gender
4. **Admission types**
   - Count of each admission type
   - Cross-tabulation and stacked bar chart of admission type by medical condition
5. **Billing analysis**
   - Overall billing amount distribution
   - Billing by medical condition (violin plot and average billing bar chart)
   - Billing by insurance provider (violin plot and average billing bar chart)
6. **Time-based billing** – converts `Admission_Date` to a monthly period (`Admission_Month`) and computes the average billing amount per month.

## Requirements

- Python 3.8+
- `pandas`, `numpy`, `matplotlib`, `seaborn`

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## How to run

1. Put the CSV in the same folder as the script.
2. Update the load path, which currently points to a Colab location:
   ```python
   df = pd.read_csv("healthcare_preprocessed (1).csv")   # was "/content/healthcare_preprocessed (1).csv"
   ```
3. Run it as a script or in a notebook:
   ```bash
   python edatask6.py
   ```
   Or upload `edatask6.py` to Colab / Jupyter and run the cells in order.

## Known issues

- **Indentation error:** in the billing amount histogram block, the lines after `plt.figure(figsize=(10,6))` start with an extra leading space, which raises an `IndentationError`. Remove the extra space.
- **Wrong title and label:** the violin plot of billing by insurance provider is titled "Billing Amount Distribution by Medical Condition" and its x-label is "Medical Condition". Both should say "Insurance Provider".
- **Duplicate variable:** `insurance_biling` repeats the `Insurance_billing` calculation and is never used. It can be deleted.
- **Unplotted result:** `monthly_billing` is calculated but never plotted or printed. A line chart of average billing by month would complete this step.

## Possible next steps

- Plot `monthly_billing` as a line chart to look for trends over time.
- Add a correlation or group comparison of `Age` against `Billing_Amount`.
- Check for outliers in `Billing_Amount` using the IQR method.
- Add a written conclusions section summarising the findings.

## Project structure

```
.
├── edatask6.py
├── healthcare_preprocessed (1).csv
└── README_healthcare_eda.md
```

## Output

<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/1a2a7244-472d-41e0-aade-818615bfba99" />

<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/60a388fa-f5f2-40e0-ab4f-9e87be2982bf" />

<img width="713" height="547" alt="image" src="https://github.com/user-attachments/assets/59ff0525-b9ae-4546-a80d-d9f0cd5c3a7d" />

<img width="704" height="547" alt="image" src="https://github.com/user-attachments/assets/9231bf2b-2ff1-4681-b519-34eb295e6cfb" />

<img width="859" height="592" alt="image" src="https://github.com/user-attachments/assets/faeaf9c6-a1b7-4cb5-8e85-ce10824f3e30" />

<img width="713" height="547" alt="image" src="https://github.com/user-attachments/assets/de41f4d6-bfd3-4866-9a13-b97e28e78dff" />

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/cf32ae54-a2ff-421f-a2af-f2a0bdb43ca0" />

<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/ea41267b-85e1-4119-a234-252af9850dad" />

<img width="1023" height="592" alt="image" src="https://github.com/user-attachments/assets/a841ae72-6e13-475f-9d9c-3b223591be71" />

<img width="1023" height="606" alt="image" src="https://github.com/user-attachments/assets/6d5e70ac-3ea1-455c-bebb-d28c35eade77" />

<img width="1023" height="547" alt="image" src="https://github.com/user-attachments/assets/be602743-adab-46e6-93bc-1bb9c76491e6" />
