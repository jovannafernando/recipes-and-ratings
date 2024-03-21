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
| name                                 |   recipe_id |   minutes |   contributor_id | submitted           | tags                                                                                                                                                                                                                        | nutrition                                    |   n_steps | steps                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | description                                                                                                                                                                                                                                                                                                                                                                       | ingredients                                                                                                                                                                    |   n_ingredients | date                |   rating | review                                                                                                                                                                                                                                                                                                                                           |   average_rating |   average_rating_per_recipe |
|:-------------------------------------|------------:|----------:|-----------------:|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------|----------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------:|:--------------------|---------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------:|----------------------------:|
| 1 brownies in the world    best ever |      333281 |        40 |           985201 | 2008-10-27 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'for-large-groups', 'desserts', 'lunch', 'snacks', 'cookies-and-brownies', 'chocolate', 'bar-cookies', 'brownies', 'number-of-servings'] | [138.4, 10.0, 50.0, 3.0, 3.0, 19.0, 6.0]     |        10 | ['heat the oven to 350f and arrange the rack in the middle', 'line an 8-by-8-inch glass baking dish with aluminum foil', 'combine chocolate and butter in a medium saucepan and cook over medium-low heat , stirring frequently , until evenly melted', 'remove from heat and let cool to room temperature', 'combine eggs , sugar , cocoa powder , vanilla extract , espresso , and salt in a large bowl and briefly stir until just evenly incorporated', 'add cooled chocolate and mix until uniform in color', 'add flour and stir until just incorporated', 'transfer batter to the prepared baking dish', 'bake until a tester inserted in the center of the brownies comes out clean , about 25 to 30 minutes', 'remove from the oven and cool completely before cutting']                                                  | these are the most; chocolatey, moist, rich, dense, fudgy, delicious brownies that you'll ever make.....sereiously! there's no doubt that these will be your fav brownies ever for you can add things to them or make them plain.....either way they're pure heaven!                                                                                                              | ['bittersweet chocolate', 'unsalted butter', 'eggs', 'granulated sugar', 'unsweetened cocoa powder', 'vanilla extract', 'brewed espresso', 'kosher salt', 'all-purpose flour'] |               9 | 2008-11-19 00:00:00 |        4 | These were pretty good, but took forever to bake.  I would send it ended up being almost an hour!  Even then, the brownies stuck to the foil, and were on the overly moist side and not easy to cut.  They did taste quite rich, though!  Made for My 3 Chefs.                                                                                   |              4.5 |                           4 |
| 1 in canada chocolate chip cookies   |      453467 |        45 |          1848091 | 2011-04-11 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'cuisine', 'preparation', 'north-american', 'for-large-groups', 'canadian', 'british-columbian', 'number-of-servings']                                                               | [595.1, 46.0, 211.0, 22.0, 13.0, 51.0, 26.0] |        12 | ['pre-heat oven the 350 degrees f', 'in a mixing bowl , sift together the flours and baking powder', 'set aside', 'in another mixing bowl , blend together the sugars , margarine , and salt until light and fluffy', 'add the eggs , water , and vanilla to the margarine / sugar mixture and mix together until well combined', 'add in the flour mixture to the wet ingredients and blend until combined', 'scrape down the sides of the bowl and add the chocolate chips', 'mix until combined', 'scrape down the sides to the bowl again', 'using an ice cream scoop , scoop evenly rounded balls of dough and place of cookie sheet about 1 - 2 inches apart to allow for spreading during baking', 'bake for 10 - 15 minutes or until golden brown on the outside and soft & chewy in the center', 'serve hot and enjoy !'] | this is the recipe that we use at my school cafeteria for chocolate chip cookies. they must be the best chocolate chip cookies i have ever had! if you don't have margarine or don't like it, then just use butter (softened) instead.                                                                                                                                            | ['white sugar', 'brown sugar', 'salt', 'margarine', 'eggs', 'vanilla', 'water', 'all-purpose flour', 'whole wheat flour', 'baking soda', 'chocolate chips']                    |              11 | 2012-01-26 00:00:00 |        5 | Originally I was gonna cut the recipe in half (just the 2 of us here), but then we had a park-wide yard sale, & I made the whole batch & used them as enticements for potential buyers ~ what the hey, a free cookie as delicious as these are, definitely works its magic! Will be making these again, for sure! Thanks for posting the recipe! |              5   |                           5 |
| 412 broccoli casserole               |      306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']          |               9 | 2008-12-31 00:00:00 |        5 | This was one of the best broccoli casseroles that I have ever made.  I made my own chicken soup for this recipe. I was a bit worried about the tsp of soy sauce but it gave the casserole the best flavor. YUM!                                                                                                                                  |              4.6 |                           5 |
|                                      |             |           |                  |                     |                                                                                                                                                                                                                             |                                              |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                |                 |                     |          | The photos you took (shapeweaver) inspired me to make this recipe and it actually does look just like them when it comes out of the oven.                                                                                                                                                                                                        |                  |                             |
|                                      |             |           |                  |                     |                                                                                                                                                                                                                             |                                              |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                |                 |                     |          | Thanks so much for sharing your recipe shapeweaver. It was wonderful!  Going into my family's favorite Zaar cookbook :)                                                                                                                                                                                                                          |                  |                             |
| 412 broccoli casserole               |      306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']          |               9 | 2009-04-13 00:00:00 |        5 | I made this for my son's first birthday party this weekend. Our guests INHALED it! Everyone kept saying how delicious it was. I was I could have gotten to try it.                                                                                                                                                                               |              4.6 |                           5 |
| 412 broccoli casserole               |      306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']          |               9 | 2013-08-02 00:00:00 |        5 | Loved this.  Be sure to completely thaw the broccoli.  I didn&#039;t and it didn&#039;t get done in time specified.  Just cooked it a little longer though and it was perfect.  Thanks Chef.                                                                                                                                                     |              4.6 |                           5 | 




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

