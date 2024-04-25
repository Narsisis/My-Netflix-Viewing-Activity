# My-Netflix-Viewing-Activity
This report presents the findings of an analysis conducted on my Netflix Viewing activity. Journey with me!

# Getting Started
Once I've got a notebook open, I imported the pandas library and read the viewing_activity CSV file (the download from netflix came with multitudes of data) into a pandas dataframe and I'll call it df (who doesn't)

Next I did a quick preview of the data to make sure everything looks correct (not that I knew what I was looking for). I started with df.shape, which will tell me the number of rows and columns in the dataframe that I have just created. OMG! 15043 rows of data and 10 columns. I seeee!

# Preparing the Data for Analysis

Before I can show my great skills, I should probably clean up this data a bit to make it easier to work with. If you are familiar with data analysis, you might want to check for duplicate or missing values, dropping the columns that are not needed and yadda yadda yadda.
Before I proceed, I should probably state that my goal is to analyze how much Netflix I have watched, so we'll need to keep the columns that relates to these. Everything else can and should go. And before I do this, I also realised that I shared my password with my sisters so I have 5 different profiles on the account, so to ensure that I am getting the true data, I have to filter to just my own profile because every movie I have watched on netflix, I watched using my own profile.
# 1 Filtering the data to just my profile 
To filter my data, since the values are strings, I will use the str to filter. And this left me with 4225 rows.
# 2 Dropping unwanted columns
So in order to drop the columns from the newly created df, I'll use df.drop() and pass it two arguments: which should be obvious by now, A list of the columns I do not need and pf course, axis=1, which tells pandas to drop columns and not rows. Very important!
# 3 Converting Strings to Datetime and Timedelta in Pandas
The data in our two time-related columns (start time and duration) certainly looks correct, but what format is this data actually being stored in? We can use df.dtypes to get a quick list of the data types for each column in our dataframe: and everything was stored in object data type which means they are strings and we will not be able to do any analysis on the date so we need to change that datatype to. So specifically, I had to;
-Convert Start Time to datetime (a data and time format pandas can understand and perform calculations with)


# 4 Changing the timezone so that we'll see everything in local time (YAY GMT+1)
To do this I had to set  Start time as the dataframe index .
Then I converted the start time from UTC timezone to WAT time using tz_convert method.
Then I also reset the index so we can have our dataframe back the way it was.

# 5 Creating time deltas on the Duartion column so I can see the days of the week and hours of the day
As the name suggests, duration — a measure of a length of time. So, rather than converting it to a datetime, I was told to convert it to a timedelta, which is a measure of time duration that pandas understands.

# 6 Filtering data that were less than 1 minute
While taking a look at my data, remember that we have 4225 rows but after filtering those rows where the duration are less than 1 minute, i was left with 2922 rows.


# Analysing the data

# 1 What is the sum of my viewing activity?
Once I had filtered the data to what I needed, I decided to do a sum of total duration spent watching netflix and you would not believe.
I used the sum method for this.

# On what days do I watch Netflic the most?
I will use the start time to answer these. So I had to do a timedelta on my start time to be able to get the day of the week and the hour of day for these.
These would add 2 extra columns to my dataframe. The day of week column would have values ranging between 0-6 with 0 indication Monday and 6 indicating sunday.
The hour of day would have values ranging from 0-23 with 0 being 12 AM and then the rest goes on.
To achive this, I had to change the column to a categorical datatype to ensure that what i want is what I will see on my graph when I plot them
I then had to extract the weekday column and do a value count to see on what days I watched netflix the most.
I then had to extract the hour column and do a value count to see on what hours I watched the most (This data had to be categirical as well).

# Observation

It was observed that I had spent 35 days 02 hours and 35 minutes watching Netflix titles since september 2022.
It was also observed that I spent more time on weekends (Saturday and Sunday) watching Netflix.
It was also observed that I watch more titles between the hours of 3 Pm - 7 PM.

# Conclusion

While I do not know if that is a lot of screen time with the understanding that netflix is not the only thing I do to relax, there are also other social media and other video platforms which I use.
Outside of the fact that I have watched a lot of titles, it's no surprise to see that most of my viewing happened during the evenings. 

