# etl-project

For my ETL project, I decided to work with something I'm passionate about... Video Games! 

I recently relapsed and have been playing a fair amount of World of Warcraft (BfA).

I was able to identify a few data sets from kaggle.com that sparked my interest. Unfortunately, these data sets are all from past expansion but stil quite exhaustive.

The data came in four separate CSV files. One with player info, one with locations and coordinates, another with location and what expansion they were introduced in and final file with zones and recommended player levels.

Fortunately, the datasets did not need much cleaning aside from trimming some whitespace, formatting df headers, and converting to datetimes.

One of the files though, 'wow_ah.csv', contained over 10 million rows... this made things difficult. I wrestled with breaking the df into multiple smaller dfs and then multiple tables in the db but wanted to give it a go and see what difficulties would arise with such large datasets. 

For example, using the pandas 'to_datetime' function took roughly 3 minutes while the to_sql function took roughly 20 minutes. This became a huge source of frustration when I forgot to remvoe duplicate lines from the df, pushed the df to the db table... and could not add a primary key.

I decided to use MySQL mainly because it's what I'm most comfortable with. However, given the relationship between the datasets (zone, map_id and other columns were shared across datasets) it also made the most sense (though given the size, MongoDB may have been a better choice).

One other issues I ran into was trying to commit/push a 700MB file to github. I would not recommend this. The push errored out and left me a commit behind the master branch. Git reset did not seem to work so I simply created a new repo, added the jupyter notebook files and smaller csv files and pushed them to github successfully!

