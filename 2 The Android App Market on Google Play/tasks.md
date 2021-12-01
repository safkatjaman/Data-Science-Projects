Task 1: Instructions
Import the data, drop duplicate rows, and inspect the data.

Load datasets/apps.csv into a DataFrame and assign it to the variable apps_with_duplicates.
Drop all duplicate rows from apps_with_duplicates and assign the result to apps.
Print the total number of apps.
Finally, display a random sample of 5 rows from apps.
Good to know
This project lets you apply the skills from Joining Data with pandas. We recommend that you take this course before starting this project.

The data for this project was scraped from the Google Play website. While there are many popular datasets for Apple App Store, there aren't many for Google Play apps, which is partially due to the increased difficulty in scraping the latter as compared to the former.

Helpful links:

pandas read_csv()documentation
pandas drop_duplicates()documentation
Note: This project also uses the plotting libraries Seaborn and Plotly to help visualize the results of some steps. However, the tasks have been written in such a way that you should be able to complete them without any prior experience.



Task 2: Instructions
Clean the dataset.

Create a list named chars_to_remove that contains the following characters: + , and $.
Create a list named cols_to_clean that contains the following column names: Installs and Price.
For each column in cols_to_clean in the apps DataFrame, replace each character in chars_to_remove with the empty string ''.
Note: Make sure to use an empty string '' and not a space character ' '
Finally, print a summary of the apps dataframe using the info() function. Observe the output.
Note: Notice that Installs and Price are still of type object and not int or float as we would have expected after removal of the special characters. We will solve this issue in the next task.
Helpful links:

pandas apply() documentation
Python replace() documentation
pandas info()documentation



Task 3: Instructions
Convert Installs and Price columns to float data type using astype() function.
Verify the corrected data types by using the dtypes attribute of apps dataframe. (You can also reuse the info() function to verify the corrected data types)
Helpful links:

astype() documentation
Pandas data types



Task 4: Instructions
Create data for a bar chart that shows the distribution of apps across different categories.

Find the number of unique app categories. Save your result in num_categories.
Count the number of apps in each category and then sort the categories in descending order of app count. Save your answer in sorted_num_apps_in_category.
Helpful links:

unique() documentation
value_counts() documentation
sort_values() documentation



Task 5: Instructions
Create a plot annotation for average app rating.

Find the average app rating and assign it to avg_app_rating.
Helpful links:

mean() documentation
Plotly histogram documentation



Task 6: Instructions
Examine the relationship between size, price, and rating of apps using jointplot().

Recall from Task #1 that we had observed some missing values in the Rating and Size columns. To make rational decisions, it is important that we do not consider these missing values in our analysis. We will work with a subset apps_with_size_and_rating_present DataFrame for this task.

Select rows from apps where both Rating and Size values are present, ie - they are not null. Store the result in the apps_with_size_and_rating_present dataframe.
From apps_with_size_and_rating_present, select the categories having atleast 250 apps. Assign the result to large_categories dataframe.
Fill out x and y to create a joint plot of Rating as a function of Size.
From apps_with_size_and_rating_present dataframe, select all Paid apps. Save the result in paid_apps.
Fill out x and y to create a joint plot of Rating as a function of Price.
Helpful links:

There are many ways to subset a dataframe and select rows based on a column value. This exercise from Data Manipulation with pandas may be a good starting place.
jointplot() documentation



Task 7: Instructions
Use a strip plot to visualize the distribution of paid apps across different categories.

Plot a strip plot with x-axis extending along the Price range and y-axis depicting the Category.
Find apps priced above $200. Print the Category, App and Price columns for such apps.
Here are some interesting websites that can estimate app price:

Estimate my app
How much to make an app
Helpful links:

stripplot() documentation
Filter rows in pandas



Task 8: Instructions
Filter out "junk" apps.
Note: For simplicity, we will continue to use the popular_app_cats dataframe (from previous task) and not our original dataframe apps

Select rows from popular_app_cats that contain apps priced below $100 and assign it to apps_under_100.
Re-plot your strip plot using apps_under_100 dataframe (instead of popular_app_cats used in the previous task).



Task 9: Instructions
Prep the data for a box plot that compares the number of installs of paid apps vs. number of installs of free apps.

From apps, filter rows where for Type == Paid, and select the Installs column and assign it to y of trace0.
From apps, filter rows where for Type == Free, and select the Installs column and assign it to y of trace1.
Helpful links:

Plotly box plot documentation
Interpreting box plots article'



Task 10: Instructions
Load the user review data and plot it to visualize sentiment of paid vs. free apps.

Read datasets/user_reviews.csv into the reviews_df DataFrame.
Merge apps and reviews_df DataFrames and assign the result to merged_df.
Create a box plot with Type on the x-axis and Sentiment_Polarity on the y-axis.
If you'd like to learn more about sentiment analysis, check out DataCamp's Natural Language Processing Fundamentals in Python course.

Helpful links:

pandas merge() function documentation
boxplot() documentation

# Load user_reviews.csv
reviews_df = pd.read_csv('datasets/user_reviews.csv')

# Join the two dataframes
merged_df = pd.merge(apps, reviews_df, on = "App")

# Drop NA values from Sentiment and Review columns
merged_df = merged_df.dropna(subset = ['Sentiment', 'Review'])

sns.set_style('ticks')
fig, ax = plt.subplots()
fig.set_size_inches(11, 8)

# User review sentiment polarity for paid vs. free apps
ax = sns.boxplot(x = 'Type', y = 'Sentiment_Polarity', data = merged_df)
ax.set_title('Sentiment Polarity Distribution')

<code>Answer:</code>
Text(0.5, 1.0, 'Sentiment Polarity Distribution')