# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

### OVERVIEW

The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, more information can be found at the websites below:
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)

Class size is one of the small number of variables in American K-12 education that are both thought to influence student learning legislative mandates on maximum class size have been very popular at the state level.  In recent decades, at least 24 states have mandated or incentivized class-size reduction (CSR). As small classes would be higher to maintain due to manpower costs (more teachers required) and infrastructure (more classrooms and separate facilities), a deeper study on whether CSR does indeed provide better student outcomes is required.

Teacher experience is used as an alternative to compare the effects of Teacher-Student Ratio on the measured SAT and ACT outcomes

### PROBLEM STATEMENT

Better student performance is traditionally associated lower Teacher-Student ratios and experienced teachers.

As a member of the California State Education Department deliberating whether mandate smaller class sizes or hire more experienced teachers. This project aims conduct a preliminary study to verify this hypothesis in California using data from the 2019 SAT & ACT from K12 test-takers to see if this relationship exists by comparing the

    - Teacher-Student Ratio
    - Teacher's Teaching Experience (Average years of teaching experience and average years of teaching in the county)

of counties with students scoring above the SAT benchmark and ACT score of 21 in 2019 (hereby referred to as the measured outcomes)

To answer the question:
> "Do lower Teacher-K12 Student Ratios or greater teacher experience affect the measured outcomes for the SAT and ACT?"

### DATASETS

We will be using the following datasets in this notebook, brief description of the datasets below:

* [`act_2019_ca.csv`](./data/act_2019_ca.csv): 2019 ACT Scores in California by School
* [`sat_2019_ca.csv`](./data/sat_2019_ca.csv): 2019 SAT Scores in California by School
* [`StaffEducation.txt`](./data/StaffEducation.txt): 2018-2019 Certificated Staff Education Report: State of California Teachers: Shows the number of teachers per county by education level for counties in California in 2018-2019
* [`StaffExp.txt`](./data/StaffExp.txt): 2018-2019 Certificated Staff Experience Report: State of California Teachers: Shows the average teacher years in service and teaching years in the county for counties in California in 2018-2019

---

### METHODOLOGY

2 consolidated DataFrames showing the measured ACT and SAT outcomes for every California county vis-a-vis the Teacher-K12 Students Ratio, Average Teacher's Years in Service and Average Teacher's Years teaching in County, were obtained after cleaning the data. EDA and visualisation were performed on the DataFrames.

---
### OBSERVATIONS AND FINDINGS

Following cleaning and merging the DataFrames, EDA on the DataFrames yielded the following insights:

* **For SAT** :
  * The counties with the highest and lowest teacher-student ratio are Modoc (104.598%) and Mono (28.571%).
  * The counties with the highest and lowest teacher average years of service are Calaveras (16 years) and Lake (10 years) .
  * The counties with the highest and lowest teacher average years in county are Los Angeles (14 years) and Lake (7 years).

Counties that performed above the state average (12.98%) for students who met SAT benchmarks have the following means:
  * Mean Teacher-Student Ratio: 66.72
  * Mean Years of Service: 13.68 years.
  * Mean Years in County: 11.16 years.

* **For ACT**:
  * The counties with the highest and lowest teacher-student ratio are Modoc (104.598%) and Mono (28.571%).
  * The counties with the highest and lowest teacher average years of service are Calaveras (16 years) and Lake (7 years).
  * The counties with the highest and lowest teacher average years in county are Los Angeles (14 years) and Lake (7 years).

  Counties that performed above the state average (56.76%) for students who scored >=21 marks for the ACT:
  * Mean Teacher-Student Ratio: 65.54
  * Mean Years of Service: 13.32 years.
  * Mean Years in County: 10.32 years.

  For the SAT, counties with lower Teacher-Student Ratios do not exhibit better outcomes in terms of greater % of students meeting the 2019 SAT benchmark. Counties with teachers who had greater years of experience in service and in the county itself exhibited better outcomes. Counties that score above the mean of the measured outcome have the following features:

  - Teacher-Student Ratio > 50%-75%
  - Average Teacher's Years of Service >= 12
  - Average Years of Teaching in County >= 10


  For the ACT. Counties with a lower Teacher-Student Ratio exhibit better outcomes in terms of a greater % of students scoring >= 21 marks for the 2019 ACT. This may be because the ACT has more subjects and may benefit more from focused attention from teachers. Counties with teachers who had greater years of experience in service also exhibited better outcomes, however, the greater years of teacher experience in the county does not. This may be an outlier observation as we are only taking a 1 year snapshot in 2018-2019. Counties that score above the mean of the measured outcome have the following features:

  - Teacher-Student Ratio > 58%-73%
  - Average Teacher's Years of Service >= 11
  - Average Years of Teaching in County >= 8
---

### CONCLUSION AND RECOMMENDATIONS  


* There is **insufficient evidence** that lower Teacher-K12 Student Ratios will positively affect SAT and ACT outcomes as no correlation was observed for the SAT while a weak negative correlation was observed for the ACT.

* There is **weak evidence** that teachers with greater experience teaching in the county and in the teaching profession will positively affect the SAT and ACT outcomes as weak positive correlations were observed for the SAT and ACT.

As a member of the California Education Department, my preliminary recommendation would be for the state to hire more experienced teachers (with at least 8 years of experience teaching in the county or 11 years of experience overall) rather than trying to decrease the Teacher-K12 Student Ratio as teaching experience has shown to improve SAT and ACT outcomes compared to Teacher-K12 Student Ratios.

### WAY AHEAD

More granular data is needed to drill down to the schools in California that require additional support. Access to the data below at the district/school level will be helpful for deeper analysis:

 - Teacher Experience
 - Number of Teachers Teaching K12 Classes (Numbers used in this study is the total number of teachers teaching at all levels, it would be more accurate to calculate the K12 Teachers-K12 Student Ratio)
 - Raw SAT and ACT Scores at the school level to calculate scores instead of meeting certain benchmarks
