# covid-fatality-prediction
R-based 4-model COVID-19 fatality classification pipeline on 14,879 Toronto Public Health cases — logistic regression identified 2.58x fatality risk per decade with 980x higher risk for 80+ outbreak patients
# COVID-19 Fatality Prediction
### R | Toronto Public Health Data | Data Mining Course

## What This Project Does
I used real COVID-19 case data from the City of Toronto to figure out which 
patients were most likely to die from COVID. The goal was to help Toronto 
Public Health decide where to send ICU beds and vaccines first.

The dataset had 14,879 cases from January 2020. I tested 4 different 
prediction models in R and compared their results.

## What I Found
- Every 10 years of age makes you 2.58x more likely to die from COVID
- Being in an outbreak setting (like a nursing home) makes cases 1.29x deadlier
- A patient aged 80+ in a nursing home outbreak has 980x higher risk 
  than a young person with a regular case
- Bottom line: prioritize ICU beds and vaccines for elderly patients 
  in long-term care outbreaks

## Models I Tested
| Model | Test Accuracy | What I Learned |
|---|---|---|
| Decision Tree | 93.1% | Didn't actually learn anything — just predicted everyone lives |
| Logistic Regression | 93.1% | Best for understanding what drives risk |
| Random Forest | 94.7% | Highest accuracy |
| Naive Bayes | 94.7% | Same as Random Forest |

**A note on accuracy:** 92.5% of cases were non-fatal, so a model that 
just predicts "nobody dies" would also get 92.5% accuracy. The high 
accuracy numbers are misleading — logistic regression was actually the 
most useful because it told me *why* people were at risk, not just 
that they were.

## How I Cleaned the Data
- Source: City of Toronto Open Data 
- Started with 14,911 cases, removed 32 rows missing Age Group (kept 99.8%)
- No duplicate rows found
- Converted age groups to numbers (1 = ages 0-9, 10 = ages 90+)
- Outbreak status converted to 0/1 (1 = outbreak-linked, 0 = regular case)
- Target variable: Fatal (1 = died, 0 = recovered or still active)
- Split data 80% training / 20% testing using set.seed(123)

## Charts Produced
- Fatality rate by age group
- Outbreak vs non-outbreak fatality comparison
- Odds ratio chart showing risk multipliers
- Risk growth curve across age groups
- Weekly death count over time (Jan-Jul 2020)
- Age distribution of all cases

## Tools Used
- Language: R
- Libraries: rpart, randomForest, e1071, ggplot2
- Environment: RStudio

## Files in This Repo
- `covid_fatality_prediction_commented.Rmd` — full code with comments 
  explaining every line
- `Final2.rmd` — original submitted file
- `Final2.pdf` — rendered output with all charts

## Course Info
Course: Data Mining (BDA 401) — Seneca Polytechnic
Program: Honours Bachelor of Data Science and Analytics (Semester 4 of 8)
Year: 2024

Data source: https://open.toronto.ca/dataset/covid-19-cases/
