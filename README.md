# recipes-and-ratings
**Authors: Jovanna Fernando and Sia Patodia**
	---

## Introduction

Welcome to our recipe analysis project! In this project, we delve into the fascinating world of cooking by examining a dataset containing various recipes. Our primary focus is on understanding what factors impact recipe ratings.

### Question Identification:
The central question of our project is: What factors exactly impact recipe ratings? We aim to uncover the key factors that contribute to the ratings assigned to recipes in our dataset.

### Why is this important?
Understanding what affects recipe ratings is crucial for anyone who enjoys cooking or exploring new recipes. Recipe ratings are often one of the first things users look at when deciding which recipe to cook. By gaining insights into the factors that influence ratings, users can make more informed decisions about which recipes to try, leading to a more satisfying cooking experience.

### All about the dataset!
**Number of Rows:**
**Relevant Columns:**

	---

## Data Cleaning and Exploratory Data Analysis

### Data Cleaning

1. **Replace Zero Ratings**: Replace zero ratings with NaN values in the "rating" column to handle missing or invalid data.

2. **Convert String Columns**: Convert string columns containing lists (e.g., 'tags', 'nutrition', 'ingredients', 'steps') into their respective list data structures using the eval function.

3. **Drop Unnecessary Columns**: Remove the "recipe_id" column, as it may not be relevant for the analysis, and rename the "id" column to "recipe_id" for clarity.

4. **Calculate Average Rating per Recipe**: Compute the average rating per recipe by grouping the DataFrame by recipe ID and calculating the mean of the ratings.

5. **Convert Date Columns**: Convert date columns ('date', 'submitted') to datetime format using the pd.to_datetime function for consistency and analysis.

6. **Count Number of Tags per Recipe**: Determine the number of tags associated with each recipe by calculating the length of the 'tags' list.

7. **Prepare Data for Reviews Analysis**: Create a dictionary mapping recipe IDs to their average ratings for further analysis.

8. **Calculate Reviews per Recipe**: Group the DataFrame by recipe ID and count the number of reviews for each recipe.

9. **Filter Outliers**: Exclude recipes with more than 100 reviews to focus on recipes with a reasonable number of reviews.

### Univariate Analysis

Distribution of Ratings

<iframe
  src="assets/ratingdist.html"
  width="400"
  height="300"
  frameborder="0"
></iframe>

	---

## Assessment of Missingness
[Discuss how missing data was handled and assessed in the dataset.]

	---

## Hypothesis Testing
[Explain the hypothesis testing conducted in the project.]

	---

## Framing a Prediction Problem
[Detail the process of framing a prediction problem in the project.]

	---

## Baseline Model
[Describe the development and evaluation of the baseline model.]

	---

## Final Model
[Discuss the development and evaluation of the final model.]

	---

## Fairness Analysis
[Provide an analysis of fairness considerations in the project.]

	---

