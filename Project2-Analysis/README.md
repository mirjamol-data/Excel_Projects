# Excel Salary Analysis

I analyzed salaries of data jobs and investigated top required skills in job postings to answer the following questions: 

### Questions to Analyze
1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023. The dataset is available via Excel course by Luke Barousse. It includes detailed information on:

**Job titles** | **Salaries** | **Locations** | **Skills**  

## 1️⃣ Do more skills get you better pay?

### 🔍 Skill: Power Query (ETL)

#### 📥 Extract

- I first used Power Query to extract the original data (`data_salary_all.xlsx`) and create two queries:
- 🗃️ First one with all the data jobs information.
- 🔧 The second listing the skills for each job ID.

#### 🔄 Transform

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.
    - 📊 data_jobs_all  
        <img width="341" height="422" alt="Screenshot 2026-03-11 094429" src="https://github.com/user-attachments/assets/58fbc787-ef67-4ed7-ac39-12286c26054d" />


    - 🛠️ data_job_skills  
        <img width="340" height="443" alt="Screenshot 2026-03-11 094441" src="https://github.com/user-attachments/assets/256e4b41-1763-4c31-adaa-9e9580e86d31" />


#### 🔗 Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 data_jobs_all   
        <img width="1919" height="1022" alt="Screenshot 2026-03-11 094819" src="https://github.com/user-attachments/assets/6d8c3cfd-048e-42b2-8e1e-18e3e55c26c2" />


    - 🛠️ data_job_skills  
        <img width="1919" height="1017" alt="Screenshot 2026-03-11 094833" src="https://github.com/user-attachments/assets/f5c92c1c-1a44-42fe-a455-ac1e79857b69" />

### 📊 Analysis
I created this Scatterplot Pivot Chart by drag-droping "Median Salary" and "Skills per Job" measures created on Power Pivot.

<img width="748" height="467" alt="Screenshot 2026-03-11 095357" src="https://github.com/user-attachments/assets/3d4124a0-1559-49ae-aae0-2f121314f208" />

#### 💡 Insights

- 📈 There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.
- 💼 Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.


#### 👉 Interpretation 

- This trend emphasizes the value of acquiring multiple relevant skills, particularly for individuals aiming for higher-paying roles.

## 2️⃣ What’s the salary for data jobs in different regions?

### 🧮 Skills: PivotTables & DAX

#### 📈Pivot Table

- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- 🧮 Then I added new measure to calculate the median salary for United States jobs.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```

#### 🧮 DAX

- To calculate the median year salary I used DAX.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### 📊 Analysis

<img width="1057" height="452" alt="Screenshot 2026-03-12 051145" src="https://github.com/user-attachments/assets/d8a89aec-b496-4550-8188-7598a29efcc1" />


#### 💡 Insights

- 💼 Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- 💰 The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.


#### 👉 Interpretation 

- These salary insights are important for planning and salary negotiations, helping professionals and companies align their offers with market standards while considering geographical variations.


## 3️⃣ What are the top skills of data professionals?

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 I created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.
- 📋 I also added slicers for Job title and Country 

#### 🔗 Data Model

- I created a relationship between my two tables using the `job_id` column.

<img width="683" height="764" alt="Screenshot 2026-03-12 051605" src="https://github.com/user-attachments/assets/14f782a1-1e0e-4493-bc93-099a805e561f" />

#### 📃 Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

<img width="1899" height="820" alt="Screenshot 2026-03-12 051633" src="https://github.com/user-attachments/assets/2ee767fb-6824-4197-a2da-0114294c74e1" />


### 📊Analysis

<img width="1350" height="447" alt="Screenshot 2026-03-12 052039" src="https://github.com/user-attachments/assets/e2c46943-51e1-4e93-80a3-c51dc8fb68ef" />

#### 💡Insights

- 💻 SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.


#### 👉 Interpretation 

- Understanding prevalent skills in the industry not only helps professionals stay competitive but also guides training and educational programs to focus on the most impactful technologies.


## 4️⃣ What’s the pay of the top 10 skills?

### 📊 Skill: Advanced Charts (Pivot Chart)

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
    - 👍 **Secondary Axis:** Skill Likelihood (as a line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 Analysis


<img width="1202" height="512" alt="Screenshot 2026-03-11 062940" src="https://github.com/user-attachments/assets/452fe778-71e0-44bd-a779-f3eb9caee744" />


#### 💡Insights
- 💰 Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- 📉 Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.



#### 👉 Interpretation 

- This chart highlights the importance of investing time in learning high-value skills like Python and SQL, which are evidently tied to higher paying roles, especially for those looking to maximize their salary in the tech industry.

## Conclusion

As a data enthusiast, I embarked on this Excel-based project to uncover valuable insights about the data jobs market. I analyzed job titles, salaries, locations, and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries, particularly in Python, SQL, and cloud technologies and found answers to my Project questions.

I hope this project serves as a practical guide for data professionals and provides an overview of the skills needed for higher-paying roles.

