
# A Four-Year Overview of the Irish Prison Services Daily Statistics: Trends and Insights

DASHBOARD LINK:
https://public.tableau.com/shared/7XZB35NG4?:display_count=n&:origin=viz_share_link

PROBLEM STATEMENT:

The Irish Prison Service faces significant challenges in managing the capacity, distribution, and demographics of prisoners across various facilities. The system must adapt to fluctuating prisoner numbers while ensuring the fair treatment and rehabilitation of individuals in custody. This report delves into the trends observed from 2017 to 2020, highlighting critical issues such as overcapacity, gender disparities, and the impact of temporary releases.

INSIGHTS AND ANALYSIS:

1. *Prisoner Population Trends*: An analysis reveals a slight discrepancy between the average total prisoners in the system and the average bed capacity count, indicating instances of overcapacity that can strain resources and affect prison conditions.

2. *Gender Disparity*: The significant difference in the number of males (61,714) compared to females (30,794) on trial/remand underscores the gender disparity within the system, highlighting the need for gender-specific rehabilitation and support programs.

3. *Temporary Releases*: The fluctuating numbers in temporary releases from 2017 to 2020 reflect the system's responsiveness to overcrowding issues, yet they also signal the need for a more sustainable solution to manage prison populations effectively.

4. *Geographical Distribution*: The geographical representation of prisoners and the location-wise bed capacity outline the uneven distribution across facilities, which can lead to logistical challenges in prisoner management and rehabilitation efforts.

5. *Bed Capacity and Inspector Oversight*: The data on bed capacity per inspector by gender across different years emphasizes the workload on inspectors and the potential impact on oversight quality, which is crucial for maintaining standards of care and security.

METHODOLOGY:

1. *Data Collection*: Data was sourced from the Irish Prison Services, encompassing various metrics such as prisoner numbers, bed capacity, temporary releases, and gender distribution from 2017 to 2020.

2. *Data Analysis*: Utilized statistical tools and software to analyze trends, disparities, and distribution patterns. The analysis included calculating averages, percentages, and creating visual representations like pie charts and geographical maps to illustrate key findings.

3. *Visualization*: Developed a comprehensive dashboard to visually represent the data, facilitating easier interpretation of the trends and insights derived from the analysis.

4. *Data Cleaning*: One of the pivotal steps in preparing our dataset for analysis was the data cleaning process. Given the complexity and the volume of data provided by the Irish Prison Services, ensuring the accuracy and usability of the data was crucial. To accomplish this, we employed Python, a powerful programming language known for its ease of use in data manipulation and cleaning tasks.

Python Libraries Used
pandas: For data manipulation and analysis.
numpy: For numerical data processing.
Data Cleaning Steps
The data cleaning process involved several key steps, implemented using Python code. These steps helped in removing inconsistencies, handling missing values, and ensuring the integrity of the dataset for accurate analysis.

Loading the Data: Imported the dataset using pandas.
Identifying Missing Values: Checked for any missing values within the dataset.
Handling Missing Values: Decisions were made on whether to fill in missing values based on their significance to the analysis or to remove the records with missing values altogether.
Removing Duplicates: Ensured that the dataset did not contain duplicate records.
Data Type Correction: Corrected the data types of certain columns to facilitate analysis, for instance, converting date strings into datetime objects.

Python Code Snippet for Data Cleaning
import pandas as pd

#*Load the dataset*

df = pd.read_csv('/path_to_your_dataset/cleaned_ips_daily_statistics (1).csv')

#*Correcting the 'Report Date' format and converting to datetime*

df['Report Date'] = pd.to_datetime(df['Report Date'], format='%d_%B_%Y')

#*Checking for missing values and deciding on a strategy*

#*For this example, we'll fill numerical missing values with the median and categorical with the mode*

numerical_columns = df.select_dtypes(include=['float64', 'int64']).columns
categorical_columns = df.select_dtypes(include=['object']).columns

for col in numerical_columns:
    df[col] = df[col].fillna(df[col].median())

for col in categorical_columns:
    df[col] = df[col].fillna(df[col].mode()[0])

#*Removing any duplicate rows*

df.drop_duplicates(inplace=True)

#*Ensuring 'Location' is categorized for efficiency*

df['Location'] = df['Location'].astype('category')

#*Correcting 'Bed Capacity per Inspector of Prisons' if needed*

#*Example: correcting a possible typo or inconsistency*

df['Bed Capacity per Inspector of Prisons'] = df.apply(lambda row: row['Bed Capacity'] if pd.isnull(row['Bed Capacity per Inspector of Prisons']) else row['Bed Capacity per Inspector of Prisons'], axis=1)

#*Save the cleaned dataset*

df.to_csv('/path_to_cleaned_dataset/cleaned_ips_daily_statistics_final.csv', index=False)

print("Data cleaning completed and saved.")

CALCULATIONS:

- *Average Total Prisoners in System*: Calculated as the mean of the total prisoner counts over the four-year period.
- *Average Bed Capacity Count*: Derived from the mean of the bed capacities reported annually.
- *Gender Distribution Analysis*: Comparison of male and female prisoners on trial/remand to highlight disparities.
- *Yearly and Location-wise Breakdown*: Pie charts and geographical maps created to display the distribution and bed capacity across various locations.

CONCLUSION AND RECOMMENDATIONS:

The analysis of the Irish Prison Services from 2017 to 2020 uncovers significant challenges in managing prisoner populations, ensuring equitable gender representation, and maintaining optimal bed capacities. Recommendations for addressing these issues include investing in infrastructure to expand bed capacities, implementing gender-specific programs, and exploring alternative sentencing methods to alleviate overcrowding. By taking proactive steps, the Irish Prison Service can enhance its effectiveness in rehabilitation and management, ensuring a safer, more equitable system for all stakeholders.

REFERENCES:

- Irish Prison Services data reports (2017-2020).

SNAPSHOT OF THE DASHBOARD (TABLEAU):

![IRISH PRISON SERVICES DASHBOARD](https://github.com/Shweta97shinde/Irish-Prison-Services-Statistics-in-Tableau/assets/152994004/fc261765-d11d-463c-95cb-7d57adfb6a7c)





