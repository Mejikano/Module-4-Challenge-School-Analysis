# School Analysis

### Resources
- Data source: schools_complete.csv and students_complete.csv
- Software: Python 3.7.10, Jupyter Notebook 6.3.0


## Overview

This analysis processes scores from different schools, districts and students to provide insights to the school board required for informed and strategic discussions school in order to make school budget and priorities decisions. This summary provide information at different aggregations such as: School, School Size, School Spend, School Type including their score performance. 

Ultimately the data cleansing and analysis disregard Thomas High School 9th grade scores per school board request due to score alterations academic dishonesty, both math and reading scores will be replaced by NaN to re-assess and provide the amended analysis.


## Results

### District Summary 

Comparing the District summary performance, it does not show a **significant** change on the metrics specially if the percentage % of Passing Math, Passing Reading and Overall Passing is formated the same way as the original analysis (just round numbers, no decimal values). 


So, how is the district summary affected? 
- it is slightly affected and I would say that it is not relevant for the school board decision making. Refer below details.

**Original Analysis Reference**

![Original - District Summary](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/original_district_summary.png)

The Original Summary formated the percentage as round number with no decimal values using the following statement on the code below, refer % Passing Math, % Passing Reading, % Overall Passing: **{:.0f}**

```
    # Format the columns.
    district_summary_df["Average Math Score"] = district_summary_df["Average Math Score"].map("{:.1f}".format)

    district_summary_df["Average Reading Score"] = district_summary_df["Average Reading Score"].map("{:.1f}".format)

    district_summary_df["% Passing Math"] = district_summary_df["% Passing Math"].map("{:.0f}".format)

    district_summary_df["% Passing Reading"] = district_summary_df["% Passing Reading"].map("{:.0f}".format)

    district_summary_df["% Overall Passing"] = district_summary_df["% Overall Passing"].map("{:.0f}".format)
```

**New Analysis Reference**

![THS Cleanned - District Summary](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_district_summary.png)


The New Summary formated the percentage number with one decimal value using the following statement on the code below, refer % Passing Math, % Passing Reading, % Overall Passing: **{:.1f}**

```
    # Format the columns.
    district_summary_df["Average Math Score"] = district_summary_df["Average Math Score"].map("{:.1f}".format)
    district_summary_df["Average Reading Score"] = district_summary_df["Average Reading Score"].map("{:.1f}".format)
    district_summary_df["% Passing Math"] = district_summary_df["% Passing Math"].map("{:.1f}".format)
    district_summary_df["% Passing Reading"] = district_summary_df["% Passing Reading"].map("{:.1f}".format)
    district_summary_df["% Overall Passing"] = district_summary_df["% Overall Passing"].map("{:.1f}".format)
```

### School Summary 

How is the school summary affected?
School Summary is not affected, just Thomas High School has some minor changes in their percentages performance. Math from 93.27% to 93.18%, Reading from 97.3% to 97.01%, Overall from 90.95% to 90.63% 

![THS Cleanned - School Summary](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_school_summary.png)


But top and bottom school performance remains the same so Thomas High School’s performance relative to the other schools was not impacted, the school kept the top 2 position:

Top 5 School- Score Performance: 
- Cabrera High School
- **Thomas High School**
- Griffin High School
- Wilson High School
- Pena High School

![THS Cleanned - Top 5 School](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_top5_performerSchools.png)


As Reference below image shows the Top 5 School performance before replacing the ninth graders’ math and reading scores.

![Original - Top 5 School](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/original_top5_performerSchools.png)


Bottom 5 School- Score Performance: 
- Rodriguez High School
- Figueroa High School
- Huang High School
- Hernandez High School
- Johnson High School


![THS Cleanned - Bottom 5 School](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_bottom5_performerschools.png)


### Scores by School Spending, Size and Type 

How does replacing the ninth-grade scores affect the following:

- Math and reading scores by grade

    - Scores are not affected for all grades of the rest of the schools but for Thomas High School only 9th graders are shown as NaN but 10th, 11th and 12th grades remains with the same percentages for both math and reading.

    ![THS Cleanned - Mathscore by grade](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_mathscore_bygrade.png)
    ![THS Cleanned - Reading by grade](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_readingscore_bygrade.png)

- Scores by school spending

    - Score Performance by school spending is not impacted by the Thomas High School 9th grade clean, all the numbers shown below were not modified.

    ![THS Cleanned - Score by School Spend](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_score_byschoolspend.png)

- Scores by school size

    - Score Performance by school Size is not impacted by the Thomas High School 9th grade clean, all the numbers shown below were not modified.

    ![THS Cleanned - Score by School Size](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_scroe_byschoolsize.png)

- Scores by school type

    - Score Performance by school Type is not impacted by the Thomas High School 9th grade clean, all the numbers shown below were not modified.

    ![THS Cleanned - Score by School Type](https://github.com/Mejikano/Module-4-Challenge-School-Analysis/blob/main/Resources/challenge_score_byschooltype.png)

Bottom line, the 9th cleanned data does not impact the overall performance metric specially if the school board look at the performance percentage as round numbers without decimal values, these values did not increase more than 1% to be reflected on each school district analysis on their passing metrics: % Passing Math, % Passing Reading, % Overall Passing:

## Summary

First of all below code cleanned the data for Thomas High School 9th grader with two code sentences required to re-assess all the School District Analysis:


```
    # Step 2. Use the loc method on the student_data_df to select all the reading scores from the 9th grade at Thomas High School and replace them with NaN.
    student_data_df.loc[(student_data_df['grade']=='9th') & (student_data_df['school_name']=='Thomas High School'), 'reading_score']=np.NaN

    #  Step 3. Refactor the code in Step 2 to replace the math scores with NaN.
    student_data_df.loc[(student_data_df['grade']=='9th') & (student_data_df['school_name']=='Thomas High School'), 'math_score']=np.NaN
```


Summarize some changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs:

- For the overall District Summary the %Overall Passing went down from %65.2 to %64.9
- Number of students went down from 39,170 to 38,709 as Thomas High School 9th grade students were substracted from the Total student count. 
- The score performance by grade is shown as nan for Thomas High School 9th grade students, both reading and math.
- Thomas High School percentages went slightly down
    - Math from 93.27% to 93.18%
    - Reading from 97.3% to 97.01% 
    - Overall from 90.95% to 90.63% 






