# Students Performance – Exploratory Data Analysis

An exploratory data analysis (EDA) of student exam scores in math, reading and writing, done in a Jupyter/Colab notebook (`week_EDA.ipynb`) with pandas, NumPy, Matplotlib and Seaborn.

## Dataset

**File:** `StudentsPerformance.csv`  
**Size:** 1,000 rows × 8 columns, no missing values

| Column | Type | Description |
|---|---|---|
| `gender` | categorical | Student gender |
| `race/ethnicity` | categorical | Group label (A–E) |
| `parental level of education` | categorical | Highest education level of the parents |
| `lunch` | categorical | `standard` or `free/reduced` |
| `test preparation course` | categorical | `none` or `completed` |
| `math score` | integer | Score out of 100 |
| `reading score` | integer | Score out of 100 |
| `writing score` | integer | Score out of 100 |

## What the notebook does

1. **Load and inspect** – reads the CSV, then checks `head()`, `tail()`, `info()`, `shape`, and missing values (`isnull().sum()`).
2. **Descriptive statistics** – mean, median, mode, standard deviation and quartiles for the three score columns.
3. **Feature engineering** – adds new columns:
   - `Total Score` – sum of the three subject scores (max 300)
   - `Percentage` – `Total Score / 300 × 100`
   - `Average Score` – mean of the three subject scores
   - `Pass/Fail` – `Pass` if all three subjects are ≥ 40, otherwise `Fail`
4. **Outlier detection** – IQR method applied to math score.
5. **Visualisation** – histogram of math scores and a box plot comparing the three subjects.

## Key observations

| Subject | Mean | Median | Std dev | Min | Max |
|---|---|---|---|---|---|
| Math | 66.09 | 66 | 15.16 | 0 | 100 |
| Reading | 69.17 | 70 | 14.60 | 17 | 100 |
| Writing | 68.05 | 69 | 15.20 | 10 | 100 |

- The dataset is clean: no nulls, and all score columns are integers.
- Reading has the highest average and math the lowest.
- Mean and median are close in every subject, so the distributions are roughly symmetric.
- The lowest scores (math 0, writing 10, reading 17) are the likely true outliers on the low side.

## Requirements

- Python 3.8+
- `pandas`, `numpy`, `matplotlib`, `seaborn`

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## How to run

1. Place `StudentsPerformance.csv` in the same folder as the notebook.
2. Change the load path in the second cell. It currently points to a Google Colab location:
   ```python
   df = pd.read_csv("StudentsPerformance.csv")   # was "/content/StudentsPerformance.csv"
   ```
3. Launch and run all cells:
   ```bash
   jupyter notebook week_EDA.ipynb
   ```

## Known issues

- **Outlier bounds bug:** the upper bound is computed as `Q3 - 1.5*IQR`. It should be `Q3 + 1.5*IQR`. Because of this, the `math_outliers` table currently returns most of the dataset instead of the handful of real outliers. Fix:
  ```python
  upper = Q3 + 1.5 * IQR
  ```
- **Pass mark is an assumption:** the threshold of 40 per subject is hard-coded and not part of the dataset. Adjust it to match your grading rules.

## Possible next steps

- Compare average scores by `gender`, `lunch`, `test preparation course` and `parental level of education` (groupby and bar plots).
- Add a correlation heatmap between math, reading and writing scores.
- Plot the distributions of reading and writing scores, not just math.
- Add a short written conclusions section at the end of the notebook (the last cell is currently empty).

## Project structure

```
.
├── week_EDA.ipynb
├── StudentsPerformance.csv
└── README.md
```
## Output

<img width="571" height="413" alt="image" src="https://github.com/user-attachments/assets/60f7892d-5f17-4c4a-94ca-2ee8b179854b" />

<img width="552" height="413" alt="image" src="https://github.com/user-attachments/assets/ac53b1ef-8a46-46b9-8631-18580878b1b5" />


