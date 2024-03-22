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

6. **Deriving 'num_tags' Column:** To enhance our dataset, we extracted the number of tags associated with each recipe by applying the len() function to the 'tags' column. This transformation allows us to quantify the level of categorization for each recipe and explore potential relationships between the number of tags and recipe ratings more effectively.


**Cleaned DataFrame Head**

(Only Important columns extracted for display)

|   recipe_id | submitted           |   num_tags |   average_rating |   average_rating_per_recipe |
|------------|--------------------|-----------|-----------------|----------------------------|
|      333281 | 2008-10-27 00:00:00 |         14 |              4.5 |                           4 |
|      453467 | 2011-04-11 00:00:00 |          9 |              5   |                           5 |
|      306168 | 2008-05-30 00:00:00 |         10 |              4.6 |                           5 |
|      306168 | 2008-05-30 00:00:00 |         10 |              4.6 |                           5 |
|      306168 | 2008-05-30 00:00:00 |         10 |              4.6 |                           5 |

All the columns and it's data types are listed below

|    Column name            | Data Type      |
|---------------------------|----------------|
| name                      | object         |
| recipe_id                 | int64          |
| minutes                   | int64          |
| contributor_id            | int64          |
| submitted                 | datetime64[ns] |
| tags                      | object         |
| nutrition                 | object         |
| n_steps                   | int64          |
| steps                     | object         |
| description               | object         |
| ingredients               | object         |
| n_ingredients             | int64          |
| date                      | datetime64[ns] |
| rating                    | float64        |
| review                    | object         |
| average_rating            | float64        |
| average_rating_per_recipe | float64        |
| num_tags                  | int64          |



### Univariate Analysis

**Ratings Distribution:** This visualization depicts the frequency of different rating scores assigned to recipes. Notably, higher ratings appear to be more prevalent, indicating a positive trend in user evaluations.
<iframe
  src="assets/ratingdist.html"
  width="800"
  height="300"
  frameborder="0"
></iframe>
**Average Rating of Contributors Distribution:** Illustrated here is the distribution of average ratings contributed by users. The majority of ratings cluster around the higher end, suggesting a general positive sentiment towards recipes, with a central tendency around 4.7.
<iframe
  src="assets/averageratingdist.html"
  width="800"
  height="300"
  frameborder="0"
></iframe>
**Number of Tags Distribution:** Displayed in this plot is the distribution of the number of tags associated with recipes. It reveals a normal distribution centered around approximately 16 tags, offering insights into common tagging practices among recipes.
<iframe
  src="assets/num_tagsdist.html"
  width="800"
  height="300"
  frameborder="0"
></iframe>

### Bivariate Analysis

In this scatter plot, each point represents the average rating of all recipes with a specific number of tags. The x-axis indicates the number of tags associated with recipes, while the y-axis represents the average rating of those recipes. The plot suggests a positive association between the number of tags and the average rating, indicating that recipes with more tags tend to have higher average ratings. This trend suggests that recipes with a greater variety of tags may be perceived more positively by users.
<iframe
  src="assets/bivariate.html"
  width="800"
  height="300"
  frameborder="0"
></iframe>
<hr>

### Interesting Aggregates
<font color="red"> i'm not sure what to write here???</font>



## Assessment of Missingness


<hr>

## Hypothesis Testing

### Permutation Test

**Null Hypothesis (H0):** There is no significant difference in the average rating of recipes between those with a small number of tags and those with a large number of tags.

**Alternative Hypothesis (H1):** Recipes with a large number of tags have a significantly higher average rating than recipes with a small number of tags.

By conducting permutation testing, we can objectively assess whether the observed difference in mean ratings is statistically significant, providing valuable insights into the relationship between the number of tags and recipe ratings.

**Choice of Test Statistic:** Difference in mean ratings between recipes with a large number of tags and those with a small number of tags.

**Choice of Significance Level (α):** 0.05 (standard practice)

The chosen significance level of 0.05 is commonly used in testing and provides a balance between Type I and Type II errors.
The test statistic, difference in mean ratings, is appropriate for comparing the average ratings between two categories.
<iframe
  src="assets/hypothesistest.html"
  width="900"
  height="300"
  frameborder="0"
></iframe>

**Conclusion:** Since the p-value (0.026) is less than the significance level (0.05), we reject the null hypothesis. We conclude that there is evidence to suggest that recipes with a large number of tags have a significantly higher average rating than recipes with a small number of tags.

<hr>



## Framing a Prediction Problem
Prediction problem: predict rating of recipes

We are building a multi-class classifier as rating of a recipe can be any value from 0 to 5

The variable we are predicting is rating. We decided to use rating since in terms of our dataset, we found it the most valuable to determine - for contributors as they will know how to best improve their recipes, as well as for users as they would know which recipes posted are the best. Rating has some relation with almost every other column, therefore, predicting rating was the best choice for our model. 

The metric we are using to evaluate our model is F1-score. Since our model is using a multi-class classifier, the f1 score accounts for both precision and recall and thus will give us a better evaluation of our model.  Accuracy is very dependent on the training/testing dataset. Since this is a multi-class classifier, a lot of variables affect the prediction, thus, F1-score can help provide a more balanced output. Although we got a higher evaluation using accuracy, we decided to keep the F-1 score since it tends to be more robust to changes and with such a dataset where a lot of the ratings are also based on personal preference, we chose a metric hat would account for robustness. since our class is imbalances ie we have a higher rating of 4 and 5, choosing accuracy would not be very indicative of the model as we could predict all ratings to be 4 or 5 and still get a high accuracy

At the time of prediction, we are guaranteed to have the list of ingredients, time for cooking, nutrition value and description of the recipe as these are all posted by the contributor. Thus, our main model is using these to predict the ratings. 

<hr>

## Baseline Model
Our pipeline uses ingredients and minutes to predict the rating. We decided to start off with these two variables, since from our Eda, we found the ingredients and time for a recipe had some r=correlation with rating. 
Quantitative: minutes
Nominal: ingredients - we found the top N most common ingredients used in our dataset as the most common ingredients would be included in the most popular recipes
Ordinal: minutes -  although minutes is a quantitative column, we decided to ordinal encode is as minutes in itself was not a good prediction. From on of our previous plots, we saw that minutes and rating tend to have a higher correlation for minutes between 20-60. For recipes that take too long or too less time, the ratings tend to be lower. Thus, we decide to ordinal encode it by putting minutes in bins

Training F1 Score: 0.6772
Test F1 Score: 0.6777
Although the scores are relatively low, since they are so close to each other, our model is training and testing well as it is not overfitting to the training data. Although accuracy was giving us a higher score(about 77%, we decide to stick with F1 scoring.). The low score could be due to the fact that we have used only 2 out of the multiple features which could affect rating. Thus, as a base, our model is “good” and sets the framework for improvement in our final model. 

<hr>

## Final Model
[Discuss the development and evaluation of the final model.]

<hr>

## Fairness Analysis

Choice of Group X: Recipes with short preparation time (less than 45 minutes).
Choice of Group Y: Recipes with long preparation time (45 minutes or more).

Evaluation Metric: Precision Score (weighted average)

Null Hypothesis (H0): The precision score for recipes with short preparation time is not significantly different from the precision score for recipes with long preparation time.

Alternative Hypothesis (H1): The precision score for recipes with short preparation time is significantly different (either higher or lower) from the precision score for recipes with long preparation time.

Test Statistic: Difference in precision scores between recipes with short and long preparation times.
Significance Level: 0.05

Conclusion: If the p-value is less than the significance level (0.05), we reject the null hypothesis and conclude that there is a significant difference in precision scores between recipes with short and long preparation times.
If the p-value is greater than or equal to the significance level, we fail to reject the null hypothesis, indicating no significant difference in precision scores between the two groups.


<hr>




 

