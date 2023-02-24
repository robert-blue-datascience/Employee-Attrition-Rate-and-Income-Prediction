Employee Attrition
================
Blue
2022-11-22

In this project, I will be using a dataset from Kaggle to determine the
factors that cause high employee attrition rates as well as factors that
play into employee income as well. All data can be found here:
<https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset>

### Install Packages

### Read in data

    ##   ID Age Attrition    BusinessTravel DailyRate             Department
    ## 1  1  32        No     Travel_Rarely       117                  Sales
    ## 2  2  40        No     Travel_Rarely      1308 Research & Development
    ## 3  3  35        No Travel_Frequently       200 Research & Development
    ## 4  4  32        No     Travel_Rarely       801                  Sales
    ## 5  5  24        No Travel_Frequently       567 Research & Development
    ## 6  6  27        No Travel_Frequently       294 Research & Development
    ##   DistanceFromHome Education   EducationField EmployeeCount EmployeeNumber
    ## 1               13         4    Life Sciences             1            859
    ## 2               14         3          Medical             1           1128
    ## 3               18         2    Life Sciences             1           1412
    ## 4                1         4        Marketing             1           2016
    ## 5                2         1 Technical Degree             1           1646
    ## 6               10         2    Life Sciences             1            733
    ##   EnvironmentSatisfaction Gender HourlyRate JobInvolvement JobLevel
    ## 1                       2   Male         73              3        2
    ## 2                       3   Male         44              2        5
    ## 3                       3   Male         60              3        3
    ## 4                       3 Female         48              3        3
    ## 5                       1 Female         32              3        1
    ## 6                       4   Male         32              3        3
    ##                  JobRole JobSatisfaction MaritalStatus MonthlyIncome
    ## 1        Sales Executive               4      Divorced          4403
    ## 2      Research Director               3        Single         19626
    ## 3 Manufacturing Director               4        Single          9362
    ## 4        Sales Executive               4       Married         10422
    ## 5     Research Scientist               4        Single          3760
    ## 6 Manufacturing Director               1      Divorced          8793
    ##   MonthlyRate NumCompaniesWorked Over18 OverTime PercentSalaryHike
    ## 1        9250                  2      Y       No                11
    ## 2       17544                  1      Y       No                14
    ## 3       19944                  2      Y       No                11
    ## 4       24032                  1      Y       No                19
    ## 5       17218                  1      Y      Yes                13
    ## 6        4809                  1      Y       No                21
    ##   PerformanceRating RelationshipSatisfaction StandardHours StockOptionLevel
    ## 1                 3                        3            80                1
    ## 2                 3                        1            80                0
    ## 3                 3                        3            80                0
    ## 4                 3                        3            80                2
    ## 5                 3                        3            80                0
    ## 6                 4                        3            80                2
    ##   TotalWorkingYears TrainingTimesLastYear WorkLifeBalance YearsAtCompany
    ## 1                 8                     3               2              5
    ## 2                21                     2               4             20
    ## 3                10                     2               3              2
    ## 4                14                     3               3             14
    ## 5                 6                     2               3              6
    ## 6                 9                     4               2              9
    ##   YearsInCurrentRole YearsSinceLastPromotion YearsWithCurrManager
    ## 1                  2                       0                    3
    ## 2                  7                       4                    9
    ## 3                  2                       2                    2
    ## 4                 10                       5                    7
    ## 5                  3                       1                    3
    ## 6                  7                       1                    7

|                                                  |                |
|:-------------------------------------------------|:---------------|
| Name                                             | initial_salary |
| Number of rows                                   | 870            |
| Number of columns                                | 36             |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                |
| Column type frequency:                           |                |
| character                                        | 9              |
| numeric                                          | 27             |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                |
| Group variables                                  | None           |

Data summary

**Variable type: character**

| skim_variable  | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:---------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| Attrition      |         0 |             1 |   2 |   3 |     0 |        2 |          0 |
| BusinessTravel |         0 |             1 |  10 |  17 |     0 |        3 |          0 |
| Department     |         0 |             1 |   5 |  22 |     0 |        3 |          0 |
| EducationField |         0 |             1 |   5 |  16 |     0 |        6 |          0 |
| Gender         |         0 |             1 |   4 |   6 |     0 |        2 |          0 |
| JobRole        |         0 |             1 |   7 |  25 |     0 |        9 |          0 |
| MaritalStatus  |         0 |             1 |   6 |   8 |     0 |        3 |          0 |
| Over18         |         0 |             1 |   1 |   1 |     0 |        1 |          0 |
| OverTime       |         0 |             1 |   2 |   3 |     0 |        2 |          0 |

**Variable type: numeric**

| skim_variable            | n_missing | complete_rate |     mean |      sd |   p0 |     p25 |     p50 |      p75 |  p100 | hist  |
|:-------------------------|----------:|--------------:|---------:|--------:|-----:|--------:|--------:|---------:|------:|:------|
| ID                       |         0 |             1 |   435.50 |  251.29 |    1 |  218.25 |   435.5 |   652.75 |   870 | ▇▇▇▇▇ |
| Age                      |         0 |             1 |    36.83 |    8.93 |   18 |   30.00 |    35.0 |    43.00 |    60 | ▂▇▇▃▂ |
| DailyRate                |         0 |             1 |   815.23 |  401.12 |  103 |  472.50 |   817.5 |  1165.75 |  1499 | ▇▇▇▇▇ |
| DistanceFromHome         |         0 |             1 |     9.34 |    8.14 |    1 |    2.00 |     7.0 |    14.00 |    29 | ▇▅▂▂▂ |
| Education                |         0 |             1 |     2.90 |    1.02 |    1 |    2.00 |     3.0 |     4.00 |     5 | ▂▅▇▆▁ |
| EmployeeCount            |         0 |             1 |     1.00 |    0.00 |    1 |    1.00 |     1.0 |     1.00 |     1 | ▁▁▇▁▁ |
| EmployeeNumber           |         0 |             1 |  1029.83 |  604.79 |    1 |  477.25 |  1039.0 |  1561.50 |  2064 | ▇▇▇▇▇ |
| EnvironmentSatisfaction  |         0 |             1 |     2.70 |    1.10 |    1 |    2.00 |     3.0 |     4.00 |     4 | ▅▆▁▇▇ |
| HourlyRate               |         0 |             1 |    65.61 |   20.13 |   30 |   48.00 |    66.0 |    83.00 |   100 | ▇▇▆▇▇ |
| JobInvolvement           |         0 |             1 |     2.72 |    0.70 |    1 |    2.00 |     3.0 |     3.00 |     4 | ▁▃▁▇▁ |
| JobLevel                 |         0 |             1 |     2.04 |    1.09 |    1 |    1.00 |     2.0 |     3.00 |     5 | ▇▇▃▂▁ |
| JobSatisfaction          |         0 |             1 |     2.71 |    1.11 |    1 |    2.00 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| MonthlyIncome            |         0 |             1 |  6390.26 | 4597.70 | 1081 | 2839.50 |  4945.5 |  8182.00 | 19999 | ▇▅▂▁▁ |
| MonthlyRate              |         0 |             1 | 14325.62 | 7108.38 | 2094 | 8092.00 | 14074.5 | 20456.25 | 26997 | ▇▇▇▇▇ |
| NumCompaniesWorked       |         0 |             1 |     2.73 |    2.52 |    0 |    1.00 |     2.0 |     4.00 |     9 | ▇▃▂▂▁ |
| PercentSalaryHike        |         0 |             1 |    15.20 |    3.68 |   11 |   12.00 |    14.0 |    18.00 |    25 | ▇▅▃▂▁ |
| PerformanceRating        |         0 |             1 |     3.15 |    0.36 |    3 |    3.00 |     3.0 |     3.00 |     4 | ▇▁▁▁▂ |
| RelationshipSatisfaction |         0 |             1 |     2.71 |    1.10 |    1 |    2.00 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| StandardHours            |         0 |             1 |    80.00 |    0.00 |   80 |   80.00 |    80.0 |    80.00 |    80 | ▁▁▇▁▁ |
| StockOptionLevel         |         0 |             1 |     0.78 |    0.86 |    0 |    0.00 |     1.0 |     1.00 |     3 | ▇▇▁▂▁ |
| TotalWorkingYears        |         0 |             1 |    11.05 |    7.51 |    0 |    6.00 |    10.0 |    15.00 |    40 | ▇▇▂▁▁ |
| TrainingTimesLastYear    |         0 |             1 |     2.83 |    1.27 |    0 |    2.00 |     3.0 |     3.00 |     6 | ▂▇▇▂▃ |
| WorkLifeBalance          |         0 |             1 |     2.78 |    0.71 |    1 |    2.00 |     3.0 |     3.00 |     4 | ▁▃▁▇▂ |
| YearsAtCompany           |         0 |             1 |     6.96 |    6.02 |    0 |    3.00 |     5.0 |    10.00 |    40 | ▇▃▁▁▁ |
| YearsInCurrentRole       |         0 |             1 |     4.20 |    3.64 |    0 |    2.00 |     3.0 |     7.00 |    18 | ▇▃▂▁▁ |
| YearsSinceLastPromotion  |         0 |             1 |     2.17 |    3.19 |    0 |    0.00 |     1.0 |     3.00 |    15 | ▇▁▁▁▁ |
| YearsWithCurrManager     |         0 |             1 |     4.14 |    3.57 |    0 |    2.00 |     3.0 |     7.00 |    17 | ▇▂▅▁▁ |

We can see that we have 870 observations with 36 columns, 9 of which are
Character variables and 27 Numeric variables. We can also see a few
columns that have no variation, thus will not have any value in our
analysis. These columns are Over18 (all Y), EmployeeCount (all 1), and
StandardHours (all 80). We will remove these three columns for now. We
can also remove ID and EmployeeNumber as they are just unique
identifiers and are not quantitative variables.

### Removing Unessessary Columns

|                                                  |           |
|:-------------------------------------------------|:----------|
| Name                                             | sal_clean |
| Number of rows                                   | 870       |
| Number of columns                                | 31        |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |           |
| Column type frequency:                           |           |
| character                                        | 8         |
| numeric                                          | 23        |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |           |
| Group variables                                  | None      |

Data summary

**Variable type: character**

| skim_variable  | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:---------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| Attrition      |         0 |             1 |   2 |   3 |     0 |        2 |          0 |
| BusinessTravel |         0 |             1 |  10 |  17 |     0 |        3 |          0 |
| Department     |         0 |             1 |   5 |  22 |     0 |        3 |          0 |
| EducationField |         0 |             1 |   5 |  16 |     0 |        6 |          0 |
| Gender         |         0 |             1 |   4 |   6 |     0 |        2 |          0 |
| JobRole        |         0 |             1 |   7 |  25 |     0 |        9 |          0 |
| MaritalStatus  |         0 |             1 |   6 |   8 |     0 |        3 |          0 |
| OverTime       |         0 |             1 |   2 |   3 |     0 |        2 |          0 |

**Variable type: numeric**

| skim_variable            | n_missing | complete_rate |     mean |      sd |   p0 |    p25 |     p50 |      p75 |  p100 | hist  |
|:-------------------------|----------:|--------------:|---------:|--------:|-----:|-------:|--------:|---------:|------:|:------|
| Age                      |         0 |             1 |    36.83 |    8.93 |   18 |   30.0 |    35.0 |    43.00 |    60 | ▂▇▇▃▂ |
| DailyRate                |         0 |             1 |   815.23 |  401.12 |  103 |  472.5 |   817.5 |  1165.75 |  1499 | ▇▇▇▇▇ |
| DistanceFromHome         |         0 |             1 |     9.34 |    8.14 |    1 |    2.0 |     7.0 |    14.00 |    29 | ▇▅▂▂▂ |
| Education                |         0 |             1 |     2.90 |    1.02 |    1 |    2.0 |     3.0 |     4.00 |     5 | ▂▅▇▆▁ |
| EnvironmentSatisfaction  |         0 |             1 |     2.70 |    1.10 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▆▁▇▇ |
| HourlyRate               |         0 |             1 |    65.61 |   20.13 |   30 |   48.0 |    66.0 |    83.00 |   100 | ▇▇▆▇▇ |
| JobInvolvement           |         0 |             1 |     2.72 |    0.70 |    1 |    2.0 |     3.0 |     3.00 |     4 | ▁▃▁▇▁ |
| JobLevel                 |         0 |             1 |     2.04 |    1.09 |    1 |    1.0 |     2.0 |     3.00 |     5 | ▇▇▃▂▁ |
| JobSatisfaction          |         0 |             1 |     2.71 |    1.11 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| MonthlyIncome            |         0 |             1 |  6390.26 | 4597.70 | 1081 | 2839.5 |  4945.5 |  8182.00 | 19999 | ▇▅▂▁▁ |
| MonthlyRate              |         0 |             1 | 14325.62 | 7108.38 | 2094 | 8092.0 | 14074.5 | 20456.25 | 26997 | ▇▇▇▇▇ |
| NumCompaniesWorked       |         0 |             1 |     2.73 |    2.52 |    0 |    1.0 |     2.0 |     4.00 |     9 | ▇▃▂▂▁ |
| PercentSalaryHike        |         0 |             1 |    15.20 |    3.68 |   11 |   12.0 |    14.0 |    18.00 |    25 | ▇▅▃▂▁ |
| PerformanceRating        |         0 |             1 |     3.15 |    0.36 |    3 |    3.0 |     3.0 |     3.00 |     4 | ▇▁▁▁▂ |
| RelationshipSatisfaction |         0 |             1 |     2.71 |    1.10 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| StockOptionLevel         |         0 |             1 |     0.78 |    0.86 |    0 |    0.0 |     1.0 |     1.00 |     3 | ▇▇▁▂▁ |
| TotalWorkingYears        |         0 |             1 |    11.05 |    7.51 |    0 |    6.0 |    10.0 |    15.00 |    40 | ▇▇▂▁▁ |
| TrainingTimesLastYear    |         0 |             1 |     2.83 |    1.27 |    0 |    2.0 |     3.0 |     3.00 |     6 | ▂▇▇▂▃ |
| WorkLifeBalance          |         0 |             1 |     2.78 |    0.71 |    1 |    2.0 |     3.0 |     3.00 |     4 | ▁▃▁▇▂ |
| YearsAtCompany           |         0 |             1 |     6.96 |    6.02 |    0 |    3.0 |     5.0 |    10.00 |    40 | ▇▃▁▁▁ |
| YearsInCurrentRole       |         0 |             1 |     4.20 |    3.64 |    0 |    2.0 |     3.0 |     7.00 |    18 | ▇▃▂▁▁ |
| YearsSinceLastPromotion  |         0 |             1 |     2.17 |    3.19 |    0 |    0.0 |     1.0 |     3.00 |    15 | ▇▁▁▁▁ |
| YearsWithCurrManager     |         0 |             1 |     4.14 |    3.57 |    0 |    2.0 |     3.0 |     7.00 |    17 | ▇▂▅▁▁ |

My next step in data clean-up is to convert the character variables into
factors.

### Process the data

|                                                  |           |
|:-------------------------------------------------|:----------|
| Name                                             | sal_clean |
| Number of rows                                   | 870       |
| Number of columns                                | 31        |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |           |
| Column type frequency:                           |           |
| factor                                           | 8         |
| numeric                                          | 23        |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |           |
| Group variables                                  | None      |

Data summary

**Variable type: factor**

| skim_variable  | n_missing | complete_rate | ordered | n_unique | top_counts                            |
|:---------------|----------:|--------------:|:--------|---------:|:--------------------------------------|
| Attrition      |         0 |             1 | FALSE   |        2 | No: 730, Yes: 140                     |
| BusinessTravel |         0 |             1 | FALSE   |        3 | Tra: 618, Tra: 158, Non: 94           |
| Department     |         0 |             1 | FALSE   |        3 | Res: 562, Sal: 273, Hum: 35           |
| EducationField |         0 |             1 | FALSE   |        6 | Lif: 358, Med: 270, Mar: 100, Tec: 75 |
| Gender         |         0 |             1 | FALSE   |        2 | Mal: 516, Fem: 354                    |
| JobRole        |         0 |             1 | FALSE   |        9 | Sal: 200, Res: 172, Lab: 153, Man: 87 |
| MaritalStatus  |         0 |             1 | FALSE   |        3 | Mar: 410, Sin: 269, Div: 191          |
| OverTime       |         0 |             1 | FALSE   |        2 | No: 618, Yes: 252                     |

**Variable type: numeric**

| skim_variable            | n_missing | complete_rate |     mean |      sd |   p0 |    p25 |     p50 |      p75 |  p100 | hist  |
|:-------------------------|----------:|--------------:|---------:|--------:|-----:|-------:|--------:|---------:|------:|:------|
| Age                      |         0 |             1 |    36.83 |    8.93 |   18 |   30.0 |    35.0 |    43.00 |    60 | ▂▇▇▃▂ |
| DailyRate                |         0 |             1 |   815.23 |  401.12 |  103 |  472.5 |   817.5 |  1165.75 |  1499 | ▇▇▇▇▇ |
| DistanceFromHome         |         0 |             1 |     9.34 |    8.14 |    1 |    2.0 |     7.0 |    14.00 |    29 | ▇▅▂▂▂ |
| Education                |         0 |             1 |     2.90 |    1.02 |    1 |    2.0 |     3.0 |     4.00 |     5 | ▂▅▇▆▁ |
| EnvironmentSatisfaction  |         0 |             1 |     2.70 |    1.10 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▆▁▇▇ |
| HourlyRate               |         0 |             1 |    65.61 |   20.13 |   30 |   48.0 |    66.0 |    83.00 |   100 | ▇▇▆▇▇ |
| JobInvolvement           |         0 |             1 |     2.72 |    0.70 |    1 |    2.0 |     3.0 |     3.00 |     4 | ▁▃▁▇▁ |
| JobLevel                 |         0 |             1 |     2.04 |    1.09 |    1 |    1.0 |     2.0 |     3.00 |     5 | ▇▇▃▂▁ |
| JobSatisfaction          |         0 |             1 |     2.71 |    1.11 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| MonthlyIncome            |         0 |             1 |  6390.26 | 4597.70 | 1081 | 2839.5 |  4945.5 |  8182.00 | 19999 | ▇▅▂▁▁ |
| MonthlyRate              |         0 |             1 | 14325.62 | 7108.38 | 2094 | 8092.0 | 14074.5 | 20456.25 | 26997 | ▇▇▇▇▇ |
| NumCompaniesWorked       |         0 |             1 |     2.73 |    2.52 |    0 |    1.0 |     2.0 |     4.00 |     9 | ▇▃▂▂▁ |
| PercentSalaryHike        |         0 |             1 |    15.20 |    3.68 |   11 |   12.0 |    14.0 |    18.00 |    25 | ▇▅▃▂▁ |
| PerformanceRating        |         0 |             1 |     3.15 |    0.36 |    3 |    3.0 |     3.0 |     3.00 |     4 | ▇▁▁▁▂ |
| RelationshipSatisfaction |         0 |             1 |     2.71 |    1.10 |    1 |    2.0 |     3.0 |     4.00 |     4 | ▅▅▁▇▇ |
| StockOptionLevel         |         0 |             1 |     0.78 |    0.86 |    0 |    0.0 |     1.0 |     1.00 |     3 | ▇▇▁▂▁ |
| TotalWorkingYears        |         0 |             1 |    11.05 |    7.51 |    0 |    6.0 |    10.0 |    15.00 |    40 | ▇▇▂▁▁ |
| TrainingTimesLastYear    |         0 |             1 |     2.83 |    1.27 |    0 |    2.0 |     3.0 |     3.00 |     6 | ▂▇▇▂▃ |
| WorkLifeBalance          |         0 |             1 |     2.78 |    0.71 |    1 |    2.0 |     3.0 |     3.00 |     4 | ▁▃▁▇▂ |
| YearsAtCompany           |         0 |             1 |     6.96 |    6.02 |    0 |    3.0 |     5.0 |    10.00 |    40 | ▇▃▁▁▁ |
| YearsInCurrentRole       |         0 |             1 |     4.20 |    3.64 |    0 |    2.0 |     3.0 |     7.00 |    18 | ▇▃▂▁▁ |
| YearsSinceLastPromotion  |         0 |             1 |     2.17 |    3.19 |    0 |    0.0 |     1.0 |     3.00 |    15 | ▇▁▁▁▁ |
| YearsWithCurrManager     |         0 |             1 |     4.14 |    3.57 |    0 |    2.0 |     3.0 |     7.00 |    17 | ▇▂▅▁▁ |

Now we have a new dataset called “sal_data” that has 8 factors and 23
numeric variables that we can use for our KNN, NB, and LM analysis later
on.

## EDA - Deep analysis on Attrition and Monthly Income vs each variable

My first step in going into my EDA is to create an EDA dataset that I
can use for visual analysis. Factors tend to work best as they are split
up into different levels and you can visualize the data easier this way.
A new dataset will allow me to do this without affecting my analysis
dataset. I will call this new set “sal_eda”

|                                                  |         |
|:-------------------------------------------------|:--------|
| Name                                             | sal_eda |
| Number of rows                                   | 870     |
| Number of columns                                | 31      |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |         |
| Column type frequency:                           |         |
| factor                                           | 25      |
| numeric                                          | 6       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |         |
| Group variables                                  | None    |

Data summary

**Variable type: factor**

| skim_variable            | n_missing | complete_rate | ordered | n_unique | top_counts                            |
|:-------------------------|----------:|--------------:|:--------|---------:|:--------------------------------------|
| Attrition                |         0 |             1 | FALSE   |        2 | No: 730, Yes: 140                     |
| BusinessTravel           |         0 |             1 | FALSE   |        3 | Tra: 618, Tra: 158, Non: 94           |
| Department               |         0 |             1 | FALSE   |        3 | Res: 562, Sal: 273, Hum: 35           |
| Education                |         0 |             1 | FALSE   |        5 | 3: 324, 4: 240, 2: 182, 1: 98         |
| EducationField           |         0 |             1 | FALSE   |        6 | Lif: 358, Med: 270, Mar: 100, Tec: 75 |
| EnvironmentSatisfaction  |         0 |             1 | FALSE   |        4 | 4: 262, 3: 258, 2: 178, 1: 172        |
| Gender                   |         0 |             1 | FALSE   |        2 | Mal: 516, Fem: 354                    |
| JobInvolvement           |         0 |             1 | FALSE   |        4 | 3: 514, 2: 228, 4: 81, 1: 47          |
| JobLevel                 |         0 |             1 | FALSE   |        5 | 1: 329, 2: 312, 3: 132, 4: 60         |
| JobRole                  |         0 |             1 | FALSE   |        9 | Sal: 200, Res: 172, Lab: 153, Man: 87 |
| JobSatisfaction          |         0 |             1 | FALSE   |        4 | 4: 271, 3: 254, 1: 179, 2: 166        |
| MaritalStatus            |         0 |             1 | FALSE   |        3 | Mar: 410, Sin: 269, Div: 191          |
| NumCompaniesWorked       |         0 |             1 | FALSE   |       10 | 1: 320, 0: 111, 3: 91, 4: 85          |
| OverTime                 |         0 |             1 | FALSE   |        2 | No: 618, Yes: 252                     |
| PercentSalaryHike        |         0 |             1 | FALSE   |       15 | 11: 126, 13: 123, 14: 120, 12: 119    |
| PerformanceRating        |         0 |             1 | FALSE   |        2 | 3: 738, 4: 132                        |
| RelationshipSatisfaction |         0 |             1 | FALSE   |        4 | 4: 264, 3: 261, 1: 174, 2: 171        |
| StockOptionLevel         |         0 |             1 | FALSE   |        4 | 0: 379, 1: 355, 2: 81, 3: 55          |
| TotalWorkingYears        |         0 |             1 | FALSE   |       39 | 10: 132, 6: 72, 8: 61, 9: 58          |
| TrainingTimesLastYear    |         0 |             1 | FALSE   |        7 | 2: 309, 3: 308, 5: 75, 4: 73          |
| WorkLifeBalance          |         0 |             1 | FALSE   |        4 | 3: 532, 2: 192, 4: 98, 1: 48          |
| YearsAtCompany           |         0 |             1 | FALSE   |       32 | 1: 107, 5: 105, 3: 85, 2: 77          |
| YearsInCurrentRole       |         0 |             1 | FALSE   |       19 | 2: 223, 0: 151, 7: 136, 3: 68         |
| YearsSinceLastPromotion  |         0 |             1 | FALSE   |       16 | 0: 342, 1: 214, 2: 94, 7: 41          |
| YearsWithCurrManager     |         0 |             1 | FALSE   |       17 | 2: 202, 0: 166, 7: 131, 3: 76         |

**Variable type: numeric**

| skim_variable    | n_missing | complete_rate |     mean |      sd |   p0 |    p25 |     p50 |      p75 |  p100 | hist  |
|:-----------------|----------:|--------------:|---------:|--------:|-----:|-------:|--------:|---------:|------:|:------|
| Age              |         0 |             1 |    36.83 |    8.93 |   18 |   30.0 |    35.0 |    43.00 |    60 | ▂▇▇▃▂ |
| DailyRate        |         0 |             1 |   815.23 |  401.12 |  103 |  472.5 |   817.5 |  1165.75 |  1499 | ▇▇▇▇▇ |
| DistanceFromHome |         0 |             1 |     9.34 |    8.14 |    1 |    2.0 |     7.0 |    14.00 |    29 | ▇▅▂▂▂ |
| HourlyRate       |         0 |             1 |    65.61 |   20.13 |   30 |   48.0 |    66.0 |    83.00 |   100 | ▇▇▆▇▇ |
| MonthlyIncome    |         0 |             1 |  6390.26 | 4597.70 | 1081 | 2839.5 |  4945.5 |  8182.00 | 19999 | ▇▅▂▁▁ |
| MonthlyRate      |         0 |             1 | 14325.62 | 7108.38 | 2094 | 8092.0 | 14074.5 | 20456.25 | 26997 | ▇▇▇▇▇ |

In this EDA we will look at how each variable in our dataset interacts
with both Employee Attrition and Monthly Income.

First, lets take a look at our two variables a bit closer

### Employee Attrition

![](Title1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

We see that out of the 870 observed employees, 140 left. This is roughly
a 16% Attrition Rate. There are also many more employees who have stayed
vs those who have left, but we still want to explore why our attrition
rate is so high. Typically, companies want to aim for attrition rates
lower than 10%.

Lets move on to the second variable: Monthly Income

### Monthly Income

This plot displays the distribution of monthly income across all 870
employees

![](Title1_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

We can clearly see the monthly income is right skewed with a majority of
employees making \> 8,000 a month.

Due to the wide spread of income (from 0-20,000), I want to group them
into 5 groups: 0 - 3999, 4000 - 7999, 8000 - 11999, 12000 - 15999, and
16000 - \<20000. This will allow me to look at different statistics
between the various income classes.

Lets see what our new column looks like

![](Title1_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

As we suspected, the majority of employees recorded make less than 8,000
per month.

Now lets take a look at the relationship between the two explanatory
variables (Monthly Income and Attrition). I added a reference line at
16% to show the company attrition rate

![](Title1_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

This bar chart shows that employees making less than 4,000 per month are
more likely to leave their job than any other group. The range between
8000 - 11,999 are close to the line as well

Lets dive into the HourlyRate, DailyRate, and MonthlyRate variables. I
mainly will be checking to see if they have any correlation towards both
Monthly Income and Attrition Rates.

![](Title1_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->![](Title1_files/figure-gfm/unnamed-chunk-8-2.png)<!-- -->![](Title1_files/figure-gfm/unnamed-chunk-8-3.png)<!-- -->

There does not seem to be any kind of correlation between any of the
three rates in association with Monthly Income nor with Attrition rate,
but we can perform a better analysis before selecting the model.

Now lets take a look at each variable and any associations they might
have with Monthly Income and Attrition Rate. I will be doing Box Plots
and Bar Graphs to visualize these relationships (if any).

### Age

First lets take a look the Age range of all recorded employees

![](Title1_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

The majority of employees are between 34 and 35 with the youngest at 18
and the oldest at 60. Now lets look at the relationship between
attrition and the income ranges:

![](Title1_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

This bar chart shows that employees between 18 - 22 and older than 52
tend to leave their jobs more frequently while the middle group tends to
stick around for a bit longer. The older group could likely be
attributed towards retirement age (65 in the US).

Just like with monthly income, I will split up the age variable into 4
different groups: 18 - 25, 25 - 35, 35 - 45, 45 - 50, \>50 then explore
the relationship between income and these age groups.

    ## [1] 18 60

    ## Warning: Removed 5 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

The Age ranges with the highest income seem to be between 45 - \>50.

### BusinessTravel

![](Title1_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

    ## Warning: Removed 3 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-12-2.png)<!-- -->

The employees that are on the road away from home look to have the
highest attrition values; however, more travel looks to be associated
with higher pay.

### Department

![](Title1_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

    ## Warning: Removed 3 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-13-2.png)<!-- -->

Sales looks to have the highest attrition rate followed by Human
Resources. Human Resources also looks to have the highest variance of
salary but all three departments look to have around the same mean
monthly income.

### Distance from Home

![](Title1_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

There does not seem to be any significant relationship between how far
an employees commute is vs their attrition rate

### Education

![](Title1_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

    ## Warning: Removed 5 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-15-2.png)<!-- -->

Education levels lower than 4 look to have the higher levels of
attrition and an education level of 5 is associated with an overall
higher salary.

### Education Field

![](Title1_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

    ## Warning: Removed 6 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-16-2.png)<!-- -->

Much like the department, employees who studied Human Resources have the
highest variance of salaries compared to the other fields. They also
have a higher level of attrition along with Marketing and those with
technical degrees.

### Environment Satisfaction

![](Title1_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-17-2.png)<!-- -->

Employees not satisfied with their environment tend to have a higher
attrition rate.

### Gender

![](Title1_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

    ## Warning: Removed 2 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-18-2.png)<!-- -->

Men tend to quit more (just slightly) than women, but men also have
higher salaries. Women though tend to have a higher median income range.

### Job Involvement

![](Title1_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-19-2.png)<!-- -->

Employees that have little job involvement are associated with a higher
attrition rate with the higher job involvement being associated with
higher salaries.

### Job Level

![](Title1_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

    ## Warning: Removed 5 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-20-2.png)<!-- -->

Higher job levels are associated with higher pay while lower job levels
are associated with a higher attrition rate.

### Job Role

![](Title1_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

    ## Warning: Removed 9 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-21-2.png)<!-- -->

Managers and Research Directors make the highest salaries. The data also
shows that employees in sales tend to have the highest attrition rates.

### Job Satisfaction

![](Title1_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-22-2.png)<!-- -->

Job satisfaction looks to have a relatively equal variance for salaries;
however, lower satisfaction is associated with a higher attrition rate.

### Marital Status

![](Title1_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

    ## Warning: Removed 3 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-23-2.png)<!-- -->

Single employees tend to quit in higher percentages and have the lowest
variance in salaries.

### Number of Comapnies Worked

![](Title1_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

    ## Warning: Removed 10 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-24-2.png)<!-- -->

Employees who have hopped around more tend to have a higher attrition
rate. The salaries though are relatively equal in variance.

### Over Time

![](Title1_files/figure-gfm/unnamed-chunk-25-1.png)<!-- -->

    ## Warning: Removed 2 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-25-2.png)<!-- -->

Employees with higher rates of over time are associated with higher
attrition rates; however, there is no change in monthly income between
employees who do and do not.

### Percent Salary Hike

![](Title1_files/figure-gfm/unnamed-chunk-26-1.png)<!-- -->

    ## Warning: Removed 15 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-26-2.png)<!-- --> Employees
who have 22-24% Salary Hikes tend to have higher rate of attrition. This
higher percent salary hike also is associated with higher average
monthly incomes.

### Performance Rating

![](Title1_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

    ## Warning: Removed 2 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-27-2.png)<!-- -->

Performance rating (between a 3 and a 4) looks to have very little
effect on either Attrition rate or Monthly Income

### Relationship Satisfaction

![](Title1_files/figure-gfm/unnamed-chunk-28-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-28-2.png)<!-- -->

Employees with a lower Relationship Status look to have a higher rate of
Attrition, but no change in the mean monthly income.

### Stock Option Level

![](Title1_files/figure-gfm/unnamed-chunk-29-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-29-2.png)<!-- -->

Employees with either 0 stock option level or the highest have the
highest rates of attrition. This could be either lower level employees
for no stock option or executives closer to retirement. But Stock option
levels don’t have any variance in the mean of the monthly income.

# Stock Option Levels vs Age and Income

![](Title1_files/figure-gfm/unnamed-chunk-30-1.png)<!-- --> The higher
age groups tend to have the higher level of stock options vs the lower
age groups

### Total Working Years

![](Title1_files/figure-gfm/unnamed-chunk-31-1.png)<!-- -->

    ## `geom_smooth()` using formula 'y ~ x'

![](Title1_files/figure-gfm/unnamed-chunk-31-2.png)<!-- -->

Less experienced employees are associated with a higher attrition rate.
Same goes for employees with 31+ years (due to retirement likely). Also,
employees with more years of experience are also associated with higher
salaries.

### Times Trained in the last year

![](Title1_files/figure-gfm/unnamed-chunk-32-1.png)<!-- -->

    ## Warning: Removed 7 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-32-2.png)<!-- -->

Employees who have not been trained very much in the last year are more
likely to quit over employees who have had ample training opportunities.
It also shows that the more training an employee goes through, the
higher their overall salaries.

### Work Life Balance

![](Title1_files/figure-gfm/unnamed-chunk-33-1.png)<!-- -->

    ## Warning: Removed 4 rows containing missing values (geom_segment).

![](Title1_files/figure-gfm/unnamed-chunk-33-2.png)<!-- -->

Employees with lower work/life balance have a higher chance of quitting
vs employees with a better balance.

### Years at Company

![](Title1_files/figure-gfm/unnamed-chunk-34-1.png)<!-- -->

    ## `geom_smooth()` using formula 'y ~ x'

![](Title1_files/figure-gfm/unnamed-chunk-34-2.png)<!-- -->

Much like Total Working Years, employees who have been with the company
for the shortest amount of time have a higher chance of attrition as
well as employees who have been with the company the longest (retirement
is likely the culprit again). And the longer an employee is with the
company, the higher their chance for a higher salary.

### Years in Current Role

![](Title1_files/figure-gfm/unnamed-chunk-35-1.png)<!-- -->

    ## `geom_smooth()` using formula 'y ~ x'

![](Title1_files/figure-gfm/unnamed-chunk-35-2.png)<!-- -->

It looks like only the two bookends (shortest and longest at current
role) tend to have any kind of visible effect on attrition rate.

### Years since Last Promotion

![](Title1_files/figure-gfm/unnamed-chunk-36-1.png)<!-- -->

    ## `geom_smooth()` using formula 'y ~ x'

![](Title1_files/figure-gfm/unnamed-chunk-36-2.png)<!-- -->

The graph suggests that the longer an employee goes without a promotion,
the higher chance they have to quit.

### Years with Current Manager

![](Title1_files/figure-gfm/unnamed-chunk-37-1.png)<!-- -->

    ## `geom_smooth()` using formula 'y ~ x'

![](Title1_files/figure-gfm/unnamed-chunk-37-2.png)<!-- -->

Same with the years working and years at the current company, the
employees who have been in their position the shortest and longest have
the higher rates of attrition.

# KNN and Naive Bayes Predictions For Attrition Rate

## KNN

### Finding the best variables using forward, backward, and step-wise selection

First, we can create a clean KNN dataset to use to build our 3 models
off of. This clean data set will remove any variable we cannot create in
either binary or is non-numerical. KNN uses Euclidian distances, so
categorical variables that use levels will not apply, thus will be left
out; however, binary can still be useful in determining the prediction.

    ##              (Intercept)                      Age                DailyRate 
    ##                     TRUE                     TRUE                    FALSE 
    ##         DistanceFromHome                Education  EnvironmentSatisfaction 
    ##                     TRUE                    FALSE                     TRUE 
    ##                   Gender               HourlyRate           JobInvolvement 
    ##                    FALSE                     TRUE                     TRUE 
    ##                 JobLevel          JobSatisfaction            MonthlyIncome 
    ##                     TRUE                     TRUE                    FALSE 
    ##              MonthlyRate       NumCompaniesWorked                 OverTime 
    ##                    FALSE                     TRUE                     TRUE 
    ##        PercentSalaryHike        PerformanceRating RelationshipSatisfaction 
    ##                    FALSE                    FALSE                     TRUE 
    ##         StockOptionLevel        TotalWorkingYears    TrainingTimesLastYear 
    ##                     TRUE                     TRUE                     TRUE 
    ##          WorkLifeBalance           YearsAtCompany       YearsInCurrentRole 
    ##                     TRUE                     TRUE                     TRUE 
    ##  YearsSinceLastPromotion     YearsWithCurrManager 
    ##                     TRUE                     TRUE

    ##              (Intercept)                      Age                DailyRate 
    ##                     TRUE                     TRUE                    FALSE 
    ##         DistanceFromHome                Education  EnvironmentSatisfaction 
    ##                     TRUE                    FALSE                     TRUE 
    ##                   Gender               HourlyRate           JobInvolvement 
    ##                    FALSE                     TRUE                     TRUE 
    ##                 JobLevel          JobSatisfaction            MonthlyIncome 
    ##                     TRUE                     TRUE                    FALSE 
    ##              MonthlyRate       NumCompaniesWorked                 OverTime 
    ##                    FALSE                     TRUE                     TRUE 
    ##        PercentSalaryHike        PerformanceRating RelationshipSatisfaction 
    ##                    FALSE                    FALSE                     TRUE 
    ##         StockOptionLevel        TotalWorkingYears    TrainingTimesLastYear 
    ##                     TRUE                     TRUE                     TRUE 
    ##          WorkLifeBalance           YearsAtCompany       YearsInCurrentRole 
    ##                     TRUE                     TRUE                     TRUE 
    ##  YearsSinceLastPromotion     YearsWithCurrManager 
    ##                     TRUE                     TRUE

    ##              (Intercept)                      Age                DailyRate 
    ##                     TRUE                     TRUE                    FALSE 
    ##         DistanceFromHome                Education  EnvironmentSatisfaction 
    ##                     TRUE                    FALSE                     TRUE 
    ##                   Gender               HourlyRate           JobInvolvement 
    ##                    FALSE                     TRUE                     TRUE 
    ##                 JobLevel          JobSatisfaction            MonthlyIncome 
    ##                     TRUE                     TRUE                    FALSE 
    ##              MonthlyRate       NumCompaniesWorked                 OverTime 
    ##                    FALSE                     TRUE                     TRUE 
    ##        PercentSalaryHike        PerformanceRating RelationshipSatisfaction 
    ##                    FALSE                    FALSE                     TRUE 
    ##         StockOptionLevel        TotalWorkingYears    TrainingTimesLastYear 
    ##                     TRUE                     TRUE                     TRUE 
    ##          WorkLifeBalance           YearsAtCompany       YearsInCurrentRole 
    ##                     TRUE                     TRUE                     TRUE 
    ##  YearsSinceLastPromotion     YearsWithCurrManager 
    ##                     TRUE                     TRUE

All three selection processes produced the same results, so we will just
need to build 1 model with the selection! It’s interesting to see that
the EDA assesment aggrees that DailyRate and MonthlyRate don’t have any
association with Attrition, but HourlyRate does.

### Build KNN Model Based on the selection process

We can build our model using the 18 parameters we pulled from our three
selection processes:

Age, DistanceFromHome, EnvironmentSatisfaction, HourlyRate,
JobInvolvement, JobLevel, JobSatisfaction, NumCompaniesWorked, OverTime,
RelationshipSatisfaction, StockOptionLevel, TotalWorkingYears,
TrainingTimesLastYear, WorkLifeBalance, YearsAtCompany,
YearsInCurrentRole, YearsSinceLastPromotion, and YearsWithCurrManager.

In addition, I will also be oversampling using an Adaptive Synthetic
(ADASYN) algorithm to help with the imbalanced dataset between yes and
no.

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction   0   1
    ##          0  95   5
    ##          1  48 137
    ##                                           
    ##                Accuracy : 0.814           
    ##                  95% CI : (0.7639, 0.8575)
    ##     No Information Rate : 0.5018          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.6285          
    ##                                           
    ##  Mcnemar's Test P-Value : 7.968e-09       
    ##                                           
    ##             Sensitivity : 0.6643          
    ##             Specificity : 0.9648          
    ##          Pos Pred Value : 0.9500          
    ##          Neg Pred Value : 0.7405          
    ##              Prevalence : 0.5018          
    ##          Detection Rate : 0.3333          
    ##    Detection Prevalence : 0.3509          
    ##       Balanced Accuracy : 0.8146          
    ##                                           
    ##        'Positive' Class : 0               
    ## 

    ## Sensitivity 
    ##   0.6643357

    ## Specificity 
    ##   0.9647887

    ##  Accuracy 
    ## 0.8140351

## Niave Bayes

Now we will perform the same steps as above, but this time with a Naive
Bayes model. We can include more variables as they do not require only
numeric values.

Just like with KNN, we will create a new dataset to work with.

    ##                      (Intercept)                              Age 
    ##                             TRUE                             TRUE 
    ##  BusinessTravelTravel_Frequently      BusinessTravelTravel_Rarely 
    ##                             TRUE                             TRUE 
    ##                        DailyRate DepartmentResearch & Development 
    ##                            FALSE                            FALSE 
    ##                  DepartmentSales                 DistanceFromHome 
    ##                            FALSE                             TRUE 
    ##                        Education      EducationFieldLife Sciences 
    ##                            FALSE                             TRUE 
    ##          EducationFieldMarketing            EducationFieldMedical 
    ##                             TRUE                             TRUE 
    ##              EducationFieldOther   EducationFieldTechnical Degree 
    ##                             TRUE                             TRUE 
    ##          EnvironmentSatisfaction                       GenderMale 
    ##                             TRUE                             TRUE 
    ##                       HourlyRate                   JobInvolvement 
    ##                             TRUE                             TRUE 
    ##                         JobLevel           JobRoleHuman Resources 
    ##                            FALSE                            FALSE 
    ##     JobRoleLaboratory Technician                   JobRoleManager 
    ##                             TRUE                            FALSE 
    ##    JobRoleManufacturing Director         JobRoleResearch Director 
    ##                             TRUE                            FALSE 
    ##        JobRoleResearch Scientist           JobRoleSales Executive 
    ##                            FALSE                            FALSE 
    ##      JobRoleSales Representative                  JobSatisfaction 
    ##                             TRUE                             TRUE 
    ##             MaritalStatusMarried              MaritalStatusSingle 
    ##                             TRUE                             TRUE 
    ##                    MonthlyIncome                      MonthlyRate 
    ##                            FALSE                            FALSE 
    ##               NumCompaniesWorked                      OverTimeYes 
    ##                             TRUE                             TRUE 
    ##                PercentSalaryHike                PerformanceRating 
    ##                            FALSE                            FALSE 
    ##         RelationshipSatisfaction                 StockOptionLevel 
    ##                             TRUE                            FALSE 
    ##                TotalWorkingYears            TrainingTimesLastYear 
    ##                             TRUE                             TRUE 
    ##                  WorkLifeBalance                   YearsAtCompany 
    ##                             TRUE                             TRUE 
    ##               YearsInCurrentRole          YearsSinceLastPromotion 
    ##                             TRUE                             TRUE 
    ##             YearsWithCurrManager 
    ##                             TRUE

    ##                      (Intercept)                              Age 
    ##                             TRUE                             TRUE 
    ##  BusinessTravelTravel_Frequently      BusinessTravelTravel_Rarely 
    ##                             TRUE                             TRUE 
    ##                        DailyRate DepartmentResearch & Development 
    ##                            FALSE                            FALSE 
    ##                  DepartmentSales                 DistanceFromHome 
    ##                             TRUE                             TRUE 
    ##                        Education      EducationFieldLife Sciences 
    ##                            FALSE                            FALSE 
    ##          EducationFieldMarketing            EducationFieldMedical 
    ##                            FALSE                            FALSE 
    ##              EducationFieldOther   EducationFieldTechnical Degree 
    ##                            FALSE                             TRUE 
    ##          EnvironmentSatisfaction                       GenderMale 
    ##                             TRUE                             TRUE 
    ##                       HourlyRate                   JobInvolvement 
    ##                             TRUE                             TRUE 
    ##                         JobLevel           JobRoleHuman Resources 
    ##                            FALSE                             TRUE 
    ##     JobRoleLaboratory Technician                   JobRoleManager 
    ##                             TRUE                            FALSE 
    ##    JobRoleManufacturing Director         JobRoleResearch Director 
    ##                             TRUE                             TRUE 
    ##        JobRoleResearch Scientist           JobRoleSales Executive 
    ##                            FALSE                            FALSE 
    ##      JobRoleSales Representative                  JobSatisfaction 
    ##                             TRUE                             TRUE 
    ##             MaritalStatusMarried              MaritalStatusSingle 
    ##                             TRUE                             TRUE 
    ##                    MonthlyIncome                      MonthlyRate 
    ##                            FALSE                            FALSE 
    ##               NumCompaniesWorked                      OverTimeYes 
    ##                             TRUE                             TRUE 
    ##                PercentSalaryHike                PerformanceRating 
    ##                            FALSE                            FALSE 
    ##         RelationshipSatisfaction                 StockOptionLevel 
    ##                             TRUE                            FALSE 
    ##                TotalWorkingYears            TrainingTimesLastYear 
    ##                             TRUE                             TRUE 
    ##                  WorkLifeBalance                   YearsAtCompany 
    ##                             TRUE                             TRUE 
    ##               YearsInCurrentRole          YearsSinceLastPromotion 
    ##                             TRUE                             TRUE 
    ##             YearsWithCurrManager 
    ##                             TRUE

    ##                      (Intercept)                              Age 
    ##                             TRUE                             TRUE 
    ##  BusinessTravelTravel_Frequently      BusinessTravelTravel_Rarely 
    ##                             TRUE                             TRUE 
    ##                        DailyRate DepartmentResearch & Development 
    ##                            FALSE                            FALSE 
    ##                  DepartmentSales                 DistanceFromHome 
    ##                             TRUE                             TRUE 
    ##                        Education      EducationFieldLife Sciences 
    ##                            FALSE                            FALSE 
    ##          EducationFieldMarketing            EducationFieldMedical 
    ##                            FALSE                            FALSE 
    ##              EducationFieldOther   EducationFieldTechnical Degree 
    ##                            FALSE                             TRUE 
    ##          EnvironmentSatisfaction                       GenderMale 
    ##                             TRUE                             TRUE 
    ##                       HourlyRate                   JobInvolvement 
    ##                             TRUE                             TRUE 
    ##                         JobLevel           JobRoleHuman Resources 
    ##                            FALSE                             TRUE 
    ##     JobRoleLaboratory Technician                   JobRoleManager 
    ##                             TRUE                            FALSE 
    ##    JobRoleManufacturing Director         JobRoleResearch Director 
    ##                             TRUE                            FALSE 
    ##        JobRoleResearch Scientist           JobRoleSales Executive 
    ##                            FALSE                            FALSE 
    ##      JobRoleSales Representative                  JobSatisfaction 
    ##                             TRUE                             TRUE 
    ##             MaritalStatusMarried              MaritalStatusSingle 
    ##                             TRUE                             TRUE 
    ##                    MonthlyIncome                      MonthlyRate 
    ##                            FALSE                            FALSE 
    ##               NumCompaniesWorked                      OverTimeYes 
    ##                             TRUE                             TRUE 
    ##                PercentSalaryHike                PerformanceRating 
    ##                            FALSE                            FALSE 
    ##         RelationshipSatisfaction                 StockOptionLevel 
    ##                             TRUE                            FALSE 
    ##                TotalWorkingYears            TrainingTimesLastYear 
    ##                             TRUE                             TRUE 
    ##                  WorkLifeBalance                   YearsAtCompany 
    ##                             TRUE                             TRUE 
    ##               YearsInCurrentRole          YearsSinceLastPromotion 
    ##                             TRUE                             TRUE 
    ##             YearsWithCurrManager 
    ##                             TRUE

Forward selection chose 29 variables, Backward selection chose 28, and
Sequential chose 27. We will build three models using these methods to
see which is the best fit

    ##      predNB1
    ##        No Yes
    ##   No  136   4
    ##   Yes  20  14

    ##      predNB2
    ##        No Yes
    ##   No  138   1
    ##   Yes  24  11

    ##      predNB3
    ##        No Yes
    ##   No  144   8
    ##   Yes  16   6

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction  No Yes
    ##        No  136  20
    ##        Yes   4  14
    ##                                           
    ##                Accuracy : 0.8621          
    ##                  95% CI : (0.8018, 0.9096)
    ##     No Information Rate : 0.8046          
    ##     P-Value [Acc > NIR] : 0.0308          
    ##                                           
    ##                   Kappa : 0.4663          
    ##                                           
    ##  Mcnemar's Test P-Value : 0.0022          
    ##                                           
    ##             Sensitivity : 0.9714          
    ##             Specificity : 0.4118          
    ##          Pos Pred Value : 0.8718          
    ##          Neg Pred Value : 0.7778          
    ##              Prevalence : 0.8046          
    ##          Detection Rate : 0.7816          
    ##    Detection Prevalence : 0.8966          
    ##       Balanced Accuracy : 0.6916          
    ##                                           
    ##        'Positive' Class : No              
    ## 

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction  No Yes
    ##        No  138  24
    ##        Yes   1  11
    ##                                           
    ##                Accuracy : 0.8563          
    ##                  95% CI : (0.7952, 0.9048)
    ##     No Information Rate : 0.7989          
    ##     P-Value [Acc > NIR] : 0.03244         
    ##                                           
    ##                   Kappa : 0.4072          
    ##                                           
    ##  Mcnemar's Test P-Value : 1.083e-05       
    ##                                           
    ##             Sensitivity : 0.9928          
    ##             Specificity : 0.3143          
    ##          Pos Pred Value : 0.8519          
    ##          Neg Pred Value : 0.9167          
    ##              Prevalence : 0.7989          
    ##          Detection Rate : 0.7931          
    ##    Detection Prevalence : 0.9310          
    ##       Balanced Accuracy : 0.6535          
    ##                                           
    ##        'Positive' Class : No              
    ## 

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction  No Yes
    ##        No  144  16
    ##        Yes   8   6
    ##                                           
    ##                Accuracy : 0.8621          
    ##                  95% CI : (0.8018, 0.9096)
    ##     No Information Rate : 0.8736          
    ##     P-Value [Acc > NIR] : 0.7222          
    ##                                           
    ##                   Kappa : 0.2606          
    ##                                           
    ##  Mcnemar's Test P-Value : 0.1530          
    ##                                           
    ##             Sensitivity : 0.9474          
    ##             Specificity : 0.2727          
    ##          Pos Pred Value : 0.9000          
    ##          Neg Pred Value : 0.4286          
    ##              Prevalence : 0.8736          
    ##          Detection Rate : 0.8276          
    ##    Detection Prevalence : 0.9195          
    ##       Balanced Accuracy : 0.6100          
    ##                                           
    ##        'Positive' Class : No              
    ## 

    ## Sensitivity 
    ##   0.9714286

    ## Sensitivity 
    ##   0.9928058

    ## Sensitivity 
    ##   0.9473684

    ## Specificity 
    ##   0.4117647

    ## Specificity 
    ##   0.3142857

    ## Specificity 
    ##   0.2727273

    ## Accuracy 
    ## 0.862069

    ##  Accuracy 
    ## 0.8563218

    ## Accuracy 
    ## 0.862069

The forward model looks to be the strongest fit with the best accuracy,
specificity, and sensitivity. I will take this and further refine it.
Using the parameter selection method and also looking at the EDA
visualizations

    ##      predNB_Final
    ##        No Yes
    ##   No  128  15
    ##   Yes  11  20

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction  No Yes
    ##        No  128  11
    ##        Yes  15  20
    ##                                        
    ##                Accuracy : 0.8506       
    ##                  95% CI : (0.7888, 0.9)
    ##     No Information Rate : 0.8218       
    ##     P-Value [Acc > NIR] : 0.1874       
    ##                                        
    ##                   Kappa : 0.5143       
    ##                                        
    ##  Mcnemar's Test P-Value : 0.5563       
    ##                                        
    ##             Sensitivity : 0.8951       
    ##             Specificity : 0.6452       
    ##          Pos Pred Value : 0.9209       
    ##          Neg Pred Value : 0.5714       
    ##              Prevalence : 0.8218       
    ##          Detection Rate : 0.7356       
    ##    Detection Prevalence : 0.7989       
    ##       Balanced Accuracy : 0.7701       
    ##                                        
    ##        'Positive' Class : No           
    ## 

    ## Sensitivity 
    ##   0.8951049

    ## Specificity 
    ##   0.6451613

    ##  Accuracy 
    ## 0.8505747

Final results for KNN vs NB:

# KNN

Accuracy - 81.82% Sensitivity - 65.47% Specificity - 97.28%

# NB

Accuracy - 85.05% Sensitivity - 89.51% Specificity - 64.52%

NB model has the better overall accuracy and sensitivity + specificty
score, so we will use our Naive Bayes model in our prediction fit.

### Linear Regression Model for Income Prediction

Just like with the Attrition Models, we will use forward, backward, and
stepwise selection to see which variables fit best with our model. This
time, we will be using the OLSRR package to do our variable selection.
We determined that the hourly, daily, and monthly rates don’t play into
the monthly income, so we can eliminate those off the bat.

## Selection Process

    ## [1] "JobLevel"                "JobRole"                
    ## [3] "TotalWorkingYears"       "BusinessTravel"         
    ## [5] "Gender"                  "YearsWithCurrManager"   
    ## [7] "YearsSinceLastPromotion" "DistanceFromHome"

    ## [1] "JobLevel"                "JobRole"                
    ## [3] "TotalWorkingYears"       "BusinessTravel"         
    ## [5] "Gender"                  "YearsWithCurrManager"   
    ## [7] "YearsSinceLastPromotion" "DistanceFromHome"

    ##  [1] "EducationField"           "MaritalStatus"           
    ##  [3] "Age"                      "OverTime"                
    ##  [5] "StockOptionLevel"         "YearsAtCompany"          
    ##  [7] "EnvironmentSatisfaction"  "YearsInCurrentRole"      
    ##  [9] "RelationshipSatisfaction" "NumCompaniesWorked"      
    ## [11] "JobInvolvement"           "TrainingTimesLastYear"   
    ## [13] "Attrition"                "JobSatisfaction"         
    ## [15] "WorkLifeBalance"          "Department"              
    ## [17] "Education"

Forward and Stepwise both produced 8 variables where Backward produced
17. We will proceed with creating two models to see which results in the
best RMSE.

### Build the linear regression model

    ## 
    ## Call:
    ## lm(formula = MonthlyIncome ~ ., data = train1)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -3693.4  -655.4   -28.0   596.1  4042.0 
    ## 
    ## Coefficients:
    ##                                 Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)                     -227.144    258.538  -0.879 0.379946    
    ## JobLevel                        2755.093     91.360  30.156  < 2e-16 ***
    ## JobRoleHuman Resources          -399.031    291.024  -1.371 0.170789    
    ## JobRoleLaboratory Technician    -733.991    189.401  -3.875 0.000117 ***
    ## JobRoleManager                  3969.551    259.681  15.286  < 2e-16 ***
    ## JobRoleManufacturing Director     94.807    186.735   0.508 0.611822    
    ## JobRoleResearch Director        3995.414    240.447  16.617  < 2e-16 ***
    ## JobRoleResearch Scientist       -455.323    190.498  -2.390 0.017112 *  
    ## JobRoleSales Executive           -70.852    163.327  -0.434 0.664568    
    ## JobRoleSales Representative     -538.792    241.028  -2.235 0.025716 *  
    ## TotalWorkingYears                 49.715      9.518   5.223 2.34e-07 ***
    ## BusinessTravelTravel_Frequently  233.550    160.396   1.456 0.145832    
    ## BusinessTravelTravel_Rarely      429.850    135.776   3.166 0.001615 ** 
    ## GenderMale                       106.743     84.641   1.261 0.207699    
    ## YearsWithCurrManager             -25.016     14.000  -1.787 0.074407 .  
    ## YearsSinceLastPromotion            4.757     16.173   0.294 0.768734    
    ## DistanceFromHome                  -6.752      5.050  -1.337 0.181651    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1074 on 679 degrees of freedom
    ## Multiple R-squared:  0.9454, Adjusted R-squared:  0.9441 
    ## F-statistic: 734.6 on 16 and 679 DF,  p-value: < 2.2e-16

    ## 
    ## Call:
    ## lm(formula = MonthlyIncome ~ ., data = train2)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -8340.0 -2190.7  -515.1  1569.6 14034.5 
    ## 
    ## Coefficients:
    ##                                  Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)                        36.934   1642.681   0.022 0.982069    
    ## EducationFieldLife Sciences       -43.409   1346.254  -0.032 0.974287    
    ## EducationFieldMarketing          -147.929   1423.207  -0.104 0.917248    
    ## EducationFieldMedical            -293.418   1348.159  -0.218 0.827773    
    ## EducationFieldOther               -78.456   1436.546  -0.055 0.956462    
    ## EducationFieldTechnical Degree   -399.737   1394.944  -0.287 0.774536    
    ## MaritalStatusMarried               73.884    360.525   0.205 0.837685    
    ## MaritalStatusSingle              -359.721    489.806  -0.734 0.462951    
    ## Age                               143.932     16.913   8.510  < 2e-16 ***
    ## OverTimeYes                       321.800    304.513   1.057 0.290996    
    ## StockOptionLevel                  -85.360    210.856  -0.405 0.685733    
    ## YearsAtCompany                    340.100     36.082   9.426  < 2e-16 ***
    ## EnvironmentSatisfaction             4.508    122.096   0.037 0.970558    
    ## YearsInCurrentRole                -55.860     57.955  -0.964 0.335473    
    ## RelationshipSatisfaction          -71.493    120.285  -0.594 0.552470    
    ## NumCompaniesWorked                195.871     56.633   3.459 0.000577 ***
    ## JobInvolvement                   -144.644    194.893  -0.742 0.458243    
    ## TrainingTimesLastYear             -83.488    105.277  -0.793 0.428039    
    ## AttritionYes                     -978.495    395.446  -2.474 0.013591 *  
    ## JobSatisfaction                  -284.335    121.618  -2.338 0.019683 *  
    ## WorkLifeBalance                   112.677    189.449   0.595 0.552204    
    ## DepartmentResearch & Development -560.984    873.556  -0.642 0.520973    
    ## DepartmentSales                   218.285    908.741   0.240 0.810244    
    ## Education                          56.021    132.985   0.421 0.673702    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 3501 on 672 degrees of freedom
    ## Multiple R-squared:  0.4096, Adjusted R-squared:  0.3894 
    ## F-statistic: 20.27 on 23 and 672 DF,  p-value: < 2.2e-16

    ## [1] 973.8421

    ## [1] 4088.935

Our first linear regression model has the smallest RMSE so we will
choose this one for our prediction!

# Conclusion

The evidence suggests that employee attrition is associated with several
factors both internal and external. The internal factors that the
company can immediately start working on to reduce attrition are
environmental satisfaction, distance from home (by offering more remote
work), reduce the amount of traveling needed for business, and job
involvement. There are other outside factors that the company has very
little control over such as the gender and marital status of the
employee or their job role.

Monthly salary can be predicted based on a few variables that are
expected such as years of experience, the role and level of the job
being analyzed, the measure of time since an employee’s last promotion,
and how far an employee has to travel from home.
