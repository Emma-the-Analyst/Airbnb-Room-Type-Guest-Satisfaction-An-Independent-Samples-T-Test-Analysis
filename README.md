# 🏠 Airbnb Room Type & Guest Satisfaction: An Independent Samples T-Test Analysis

An Excel-based statistical analysis investigating whether **room type** (Private room vs. Entire home/apt) has a significant effect on **guest satisfaction scores** on Airbnb.

---

## 📑 Table of Contents

1. [Project Abstract](#1-project-abstract)
2. [Project Overview](#2-project-overview)
3. [Business Problem](#3-business-problem)
4. [Solution](#4-solution)
5. [Project Objective](#5-project-objective)
6. [Requirement Gathering](#6-requirement-gathering)
   - [a. Dataset](#a-dataset)
   - [b. Data Dictionary](#b-data-dictionary)
   - [c. Question Asked](#c-question-asked)
   - [d. Project Deliverable](#d-project-deliverable)
   - [e. Tool Used](#e-tool-used)
7. [Cleaning and Transformation](#7-cleaning-and-transformation)
8. [Hypothesis Testing](#8-hypothesis-testing)
   - [a. Test Selection](#a-test-selection)
   - [b. Assumptions Considered](#b-assumptions-considered-normality-of-samples)
   - [c. Hypothesis Statement](#c-hypothesis-statement)
   - [d. Decision Rule](#d-decision-rule)
   - [e. Test Results and Findings](#e-test-results-and-findings)
9. [Recommendation](#9-recommendation)
10. [Conclusion](#10-conclusion)

---

## 1. Project Abstract

This project investigates whether there is a statistically significant difference in customer satisfaction scores between Private room and Entire home/apt listings on Airbnb. Using a large sample of over 46,000 observations per group, an independent samples t-test was conducted to compare mean satisfaction ratings. The findings reveal no significant difference between the two room types, suggesting that guests are equally satisfied regardless of which type they book. This result provides valuable insights for Airbnb hosts and the platform itself when making decisions about listing strategies and resource allocation.

---

## 2. Project Overview

Airbnb offers hosts the flexibility to list their properties as either Private rooms or Entire homes/apartments. Each option presents distinct advantages and challenges. Private rooms tend to be more affordable and appeal to budget-conscious travelers, while Entire homes/apartments offer greater privacy and space, often commanding higher prices. However, the impact of room type on customer satisfaction remains unclear. This project aims to determine whether guests report significantly different satisfaction levels based on the room type they book. The analysis uses a dataset of Airbnb listings, focusing on customer review ratings as the measure of satisfaction. By applying statistical testing, this project seeks to provide data-driven recommendations for hosts and the Airbnb platform.

---

## 3. Business Problem

Airbnb hosts must decide whether to list their properties as Private rooms or Entire home/apt units. This decision affects pricing, guest expectations, and operational effort. However, Airbnb lacks clear evidence on whether one room type delivers significantly higher guest satisfaction than the other. Without this understanding, hosts cannot make fully informed listing decisions, and Airbnb cannot provide data-driven recommendations to improve overall customer experience.

---

## 4. Solution

To address the business problem, this project employs an independent samples t-test to compare customer satisfaction scores between Private room and Entire home/apt listings. The t-test is the appropriate statistical method because it allows for the comparison of means between two independent groups. The analysis will use a sample of Airbnb listings, with satisfaction scores serving as the dependent variable and room type serving as the independent variable. The test will determine whether any observed difference in mean satisfaction scores between the two groups is statistically significant or merely due to random chance. The findings will provide a clear, data-driven answer to the business question, enabling hosts and the Airbnb platform to make informed decisions.

---

## 5. Project Objective

The primary objective of this project is to determine whether there is a statistically significant difference in customer satisfaction scores between Private room and Entire home/apt listings on Airbnb. Specifically, this project aims to:

1. Analyze customer satisfaction data from a large sample of Airbnb listings.
2. Compare the mean satisfaction scores between the two room types.
3. Apply an independent samples t-test to determine if any observed differences are statistically significant.
4. Provide data-driven recommendations to Airbnb hosts and the platform based on the findings.

By achieving these objectives, this project will help hosts make informed listing decisions and enable Airbnb to offer targeted guidance that enhances overall guest satisfaction.

---

## 6. Requirement Gathering

### a. Dataset

Dataset was obtained from Kaggle. Link: [Airbnb Open Data](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata)

### b. Data Dictionary

| Column Name | Variable Type | Description | Role in the Test |
|---|---|---|---|
| `id` | Nominal | A unique numerical identifier for each Airbnb listing. | — |
| `Host_id` | Nominal | A unique numerical identifier for the host of the listing. | — |
| `room type` | Nominal | The category of rental space offered. Values include Private room and Entire home/apt. | **Grouping Variable (Independent Variable):** Used to split the data into two independent groups for comparison. |
| `review rate number` | Ratio | A numerical score (scale of 1–5) representing customer satisfaction or rating for the listing. | **Outcome Variable (Dependent Variable):** The ratio numerical variable compared between the two groups. |

### c. Question Asked

To guide this project and ensure a clear analytical direction, the following key questions were formulated:

**1. Primary Research Question**
Is there a statistically significant difference in customer satisfaction scores between Private room and Entire home/apt listings?

**2. Supporting Business Questions**
   i. Which room type delivers higher guest satisfaction?
   ii. Should Airbnb hosts prefer one room type over the other?
   iii. Can Airbnb use these findings to improve platform recommendations?

### d. Project Deliverable

The following deliverables will be produced upon completion of this project:

1. **Final Business Report:** A comprehensive document detailing the entire project, including the business problem, methodology, analysis, findings, and recommendations.
2. **Statistical Output:** The t-test results generated from Excel, including mean scores, t-statistic, degrees of freedom, and p-value.
3. **Recommendations:** Clear, actionable suggestions based on the statistical findings to guide decision-making.

### e. Tool Used

The entire project was performed using **Microsoft Excel**. Microsoft Excel was used for:
- Data cleaning and transformation
- Generating charts
- Performing the statistical test

---

## 7. Cleaning and Transformation

This was done using Excel Power Query.

**Required Column Selection**
From the original dataset, only four columns — **id**, **hostid**, **room_type**, and **review_rate_number** — were retained as they were directly relevant to the analysis. This selection ensured the dataset remained focused on the variables required to answer the business question while eliminating unnecessary complexity.

Furthermore, room type was filtered and limited to only "Entire home/apt" and "Private_room" under the room_type column.

**Null Values**
During the data cleaning process, null values were identified in the review rate number column, which served as the dependent variable for the test. All rows containing null values in the review_rate_number column were removed.

**Duplicate Check**
Duplicates were removed to ensure the independence of observations.

**Data Type Check**
After removing null values, each column was reviewed to ensure the correct data type was applied, as improper data types could lead to errors in analysis.

**Outlier Check**
Review rate number column was checked for outliers using a box and whisker plot. No outlier was observed.

![Box and whisker plot showing no outliers in review rate number](..........)

**Transformation**
Review rate number was classified under the room type (**Private_Room** and **Entire_Home/Apt**). After the classification, some rows appeared null under the new columns created. This is because each customer makes one review at a time for either Private room or Entire home/Apt. All the nulls were replaced with '0'. Ratings (1–5) for both categories were copied to be sampled.

**Sampling**
After the transformation, **Private room** category had 46,149 total rows while **Entire room/apt category** had 53,274 total rows. The first 46,149 rows from each category was selected for the test. More data points were selected for the test to ensure the result of the test reflects the true population and also makes the results more robust.

> Note: '0' was not included in the sampling.

![Sampling breakdown showing row counts per room type](..........)

---

## 8. Hypothesis Testing

### a. Test Selection

**Independent samples T-test** (used to compare means of two groups) was chosen for the research because:

1. The variables involved are two independent variables.
2. The two groups are metrics (Ratio variables) which can be used for calculations of the means.

### b. Assumptions Considered (Normality of Samples)

Both histograms show a sharp drop at rating 1 (approximately 4,125 for Private room and 4,159 for Entire home/apt), while ratings 2 through 5 display relatively balanced frequencies ranging from approximately 10,400 to 10,600, indicating approximately normal distributions with no severe skewness. Given the large sample size of 46,149 observations per group, the normality assumption is considered met for both groups, and proceeding with the independent samples t-test is justified.

### c. Hypothesis Statement

**1. Null Hypothesis (H₀)**
There is **no statistically significant difference** in the mean customer satisfaction scores between Private room and Entire home/apt listings. Any observed difference in the sample means is due to random chance.

**Mathematical Form:** H₀: μ₁ = μ₂

**2. Alternative Hypothesis (H₁)**
There is a **statistically significant difference** in the mean customer satisfaction scores between Private room and Entire home/apt listings.

**Mathematical Form:** H₁: μ₁ ≠ μ₂

### d. Decision Rule
| If | Then |
|---|---|
| p-value < 0.05 | Reject H₀ → Significant difference exists |
| p-value ≥ 0.05 | Fail to reject H₀ → No significant difference |

### OR

| If | Then |
|---|---|
| T-Statistic > T-critical | Reject H₀ → Significant difference exists |
| T-Statistic ≤ T-critical | Fail to reject H₀ → No significant difference |

> Note: The test was run with a 95% confidence interval and a p-value threshold of 5% (0.05).

### e. Test Results and Findings

The test was conducted using the Data Analysis Toolpak in Microsoft Excel, and the result is shown below:

![Excel t-test output table](..........)

The independent samples t-test revealed mean satisfaction scores of 3.281 for Private rooms and 3.278 for Entire home/apt listings, with a difference of only 0.003. With a t-statistic of 0.369, degrees of freedom of 92,295, and a two-tailed p-value of 0.712 (far exceeding the 0.05 significance level), we fail to reject the null hypothesis, confirming no statistically significant difference in customer satisfaction between the two room types.

---

## 9. Recommendation

Based on the results of the independent samples t-test, the following recommendations are proposed:

1. **List based on other factors, not satisfaction risk.** Since there is no statistically significant difference in guest satisfaction between Private room and Entire home/apt listings, hosts can choose a room type based on factors such as available space, income goals, privacy considerations, and local demand, without fear that one option will lead to lower guest ratings.
2. **Avoid resource bias toward one room type.** Airbnb should avoid allocating marketing spend, search ranking boosts, or promotional support disproportionately to one room type on the assumption that it produces happier guests, as the data does not support that assumption.
3. **Focus improvement efforts on factors that actually drive satisfaction.** Since room type is not a meaningful driver of guest satisfaction, Airbnb and hosts should redirect attention to variables more likely to influence guest experience, such as cleanliness, host responsiveness, accuracy of listing descriptions, and price fairness.
4. **Use satisfaction scores cautiously in listing recommendations.** Airbnb's recommendation algorithms should not treat room type as a satisfaction signal; instead, host-specific and listing-specific quality metrics should carry more weight in ranking and recommendation decisions.
5. **Monitor rather than assume.** Given that this analysis is based on a single point-in-time sample, Airbnb should periodically re-run this comparison as new review data comes in, to confirm the finding holds over time and across markets.

---

## 10. Conclusion

This project set out to determine whether room type — Private room versus Entire home/apt — has a statistically significant effect on guest satisfaction on Airbnb. Using an independent samples t-test on a large, balanced sample of 46,149 observations per group, the analysis found mean satisfaction scores of 3.281 for Private rooms and 3.278 for Entire home/apt listings, a difference of just 0.003. With a t-statistic of 0.369 and a two-tailed p-value of 0.712, far above the 0.05 significance threshold, the null hypothesis could not be rejected.

This indicates that guests are, on average, equally satisfied regardless of whether they book a Private room or an Entire home/apt. Room type on its own is therefore not a meaningful predictor of guest satisfaction. Airbnb hosts can make listing decisions based on practical considerations — such as available space, desired income, and privacy — without concern that their choice of room type will negatively affect guest ratings. For Airbnb as a platform, this finding suggests that efforts to improve guest satisfaction should be directed at other factors beyond room type, such as service quality, pricing, and listing accuracy.
