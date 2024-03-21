# Palate Perspectives: Exploring Recipe Ratings!
**Authors: Jovanna Fernando and Sia Patodia**
<hr>

## Introduction

Welcome to our recipe analysis project! In this project, we delve into the fascinating world of cooking by examining a dataset containing various recipes. Our primary focus is on understanding what factors impact recipe ratings.

**The central question of our project is:** <font color="blue">What factors exactly impact recipe ratings?</font>

**Why is this important?**
We aim to uncover the key factors that contribute to the ratings assigned to recipes in our dataset. Understanding what affects recipe ratings is crucial for anyone who enjoys cooking or exploring new recipes. Recipe ratings are often one of the first things users look at when deciding which recipe to cook. By gaining insights into the factors that influence ratings, users can make more informed decisions about which recipes to try, leading to a more satisfying cooking experience.


### All about the dataset!

<font color="red"> Why should readers of your website care about the dataset ???</font>

**Data Sources:**
The dataset used in this analysis is sourced from food.com, a popular online platform dedicated to sharing recipes, cooking tips, and culinary inspiration.
Food.com hosts a vast collection of user-contributed recipes spanning various cuisines, dietary preferences, and cooking styles.
Users can browse, search, and contribute recipes, as well as interact with other members by rating, reviewing, and sharing their cooking experiences.
All the data used for this project has been scarped from food.com.

The collected data is organized into tabular formats as descriped below:
- **Recipes DataFrame:** Contains details about each recipe, such as its name, preparation time, ingredients, and contributor information.
- **Interactions DataFrame:** Captures user interactions with recipes, including ratings and reviews provided by users.
- **Average Ratings DataFrame:** Provides the average rating of each contributor, obtained from user profiles.

**Combined DataFrame:**
- **Rows:** 234,429
- **Columns:** 18

**Key Attributes:**
- **Name:** Name of the recipe.
- **ID:** Unique identifier for each recipe.
- **Minutes:** Preparation time required for the recipe.
- **Contributor ID:** Identifier of the contributor who submitted the recipe.
- **Submitted:** Date when the recipe was submitted.
- **Tags:** Categorical labels providing additional context.
- **Nutrition:** Nutritional information of the recipe.
- **Number of Steps:** Number of steps in the recipe.
- **Steps:** Detailed instructions for preparing the recipe.
- **Description:** Brief overview or summary of the recipe.
- **Ingredients:** List of ingredients required for the recipe.
- **Number of Ingredients:** Count of ingredients in the recipe.
- **User ID:** Unique identifier for users interacting with recipes.
- **Recipe ID:** Identifier linking interactions to specific recipes.
- **Rating:** Numeric score representing user evaluation of the recipe.
- **Review:** Textual feedback or comments accompanying the rating.
- **Average Rating:** Average rating of each contributor.

<font color="red">In out study we focused on the number of tags?? need to write soemthing here</font>

<hr>

## Data Cleaning and Exploratory Data Analysis

### Data Cleaning

1. **Replacing Rating 0 with NaN:** In the original dataset, a rating of 0 could indicate that no rating was provided by the user. Upon inspecting the website, we found that if no stars are pressed, it automatically assigns a 0 rating. This could skew any analysis involving averaging ratings or calculating statistics based on ratings. By replacing these 0 values with NaN, we accurately represent the absence of a rating.

2. **Converting String Representation of Lists to Lists:** Certain columns like 'tags', 'nutrition', 'ingredients', and 'steps' were stored as strings representing lists (e.g., "[tag1, tag2, tag3]"). Converting them to actual lists allows for easier access and manipulation of the data.

3. **Converting 'date' and 'submitted' to DateTime Format:** The 'date' and 'submitted' columns were initially stored as objects. Converting them to DateTime format allows for better handling of date-related operations and facilitates temporal analyses.

4. **Dropping 'recipe_id' Column and Renaming 'id' to 'recipe_id':** The 'recipe_id' column is the primary identifier for each recipe. Dropping the 'recipe_id' column and renaming 'id' to 'recipe_id' ensures consistency and clarity in the dataset.

5. **Adding 'average_rating_per_recipe' Column:** To facilitate analysis, we calculated the average rating for each recipe and added it as a new column in the DataFrame. This provides a convenient way to access the average rating for each recipe, enabling comparative analyses and identifying highly-rated recipes.


**DataFrame Head**
|   recipe_id | submitted           | tags                                                                                                                                                                                                                        |   average_rating |   average_rating_per_recipe |
|------------:|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------:|----------------------------:|
|      333281 | 2008-10-27 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'for-large-groups', 'desserts', 'lunch', 'snacks', 'cookies-and-brownies', 'chocolate', 'bar-cookies', 'brownies', 'number-of-servings'] |              4.5 |                           4 |
|      453467 | 2011-04-11 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'cuisine', 'preparation', 'north-american', 'for-large-groups', 'canadian', 'british-columbian', 'number-of-servings']                                                               |              5   |                           5 |
|      306168 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        |              4.6 |                           5 |
|      306168 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        |              4.6 |                           5 |
|      306168 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        |              4.6 |                           5 | 




### Univariate Analysis

Distribution of Ratings

<iframe
  src="assets/ratingdist.html"
  width="400"
  height="300"
  frameborder="0"
></iframe>

<hr>

## Assessment of Missingness
[Discuss how missing data was handled and assessed in the dataset.]

<hr>

## Hypothesis Testing
[Explain the hypothesis testing conducted in the project.]

<hr>

## Framing a Prediction Problem
[Detail the process of framing a prediction problem in the project.]

<hr>

## Baseline Model
[Describe the development and evaluation of the baseline model.]

<hr>

## Final Model
[Discuss the development and evaluation of the final model.]

<hr>

## Fairness Analysis
[Provide an analysis of fairness considerations in the project.]

<hr>

