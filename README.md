# sparcs_descriptive_2022

2022 SPARCS de-identified data to explore healthcare trends, patient demographics, and hospital performance metrics.

## Summary 

- The **average length of stay** is **5.97 days**.
- The **median total charges** are **$58,783.83**.
- The **most common type of admission** is **Emergency**, accounting for **74.60%** of admissions.
- **57.8% of the patients** are female and **42.2% are male**.
- The majority of admissions are in the **50 to 69** age group.

## Deliverables

Repository:
1. A **Python notebook** (`sparcs_analysis.py`) that performs:
   - Data loading and cleaning.
   - Basic descriptive statistics.
   - Visualizations of the data.
   - A summary of findings based on the analysis.
2. A **README.md** file, explaining the project, the analysis process, challenges and how to run the code.

## Data Loading Method

I decided to use the **API endpoint** to retrieve the SPARCS dataset. This allowed me to get the most up-to-date information rather than downloading static CSV files. By using the API, I could manipulate the data using the Pandas library in Python and filter out only the relevant columns.

## Issues and Solutions

While working on this project, I encountered challenges:

1. **Missing Python Libraries**: 
   - Initially, I encountered `ModuleNotFoundError` errors for `requests`, `pandas`, `matplotlib`, and `seaborn`.
   - **Solution**: I installed the missing libraries using the `pip` command:
     ```bash
     pip install requests pandas matplotlib seaborn
     ```

2. **Data Type Conversions**:
   - When working with the `total_charges` and `total_costs` columns, I found that the data was stored as strings, which caused errors when calculating descriptive statistics.
   - **Solution**: I converted the relevant columns to numeric values using Pandas:
     ```python
     df['total_charges'] = pd.to_numeric(df['total_charges'].str.replace(',', '').str.replace('$', ''), errors='coerce')
     ```

3. **Missing Data**:
   - Some rows in the dataset had missing values for `length_of_stay` and `total_charges`.
   - **Solution**: I handled this by filling missing values with the median of the columns.

## Visualizations

The analysis includes the following visualizations:
- **Histogram of Length of Stay**: Displays the distribution of how long patients stay in the hospital.
- **Boxplot for Total Charges**: Identifies outliers in hospital charges.
- **Bar Plot for Type of Admission**: Analyzes admission trends.

## How to Run the Project

1. Clone the repository using the following command:
   ```bash
   git clone https://github.com/your_username/sparcs_descriptive_2022.git
