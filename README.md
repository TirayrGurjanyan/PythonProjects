# Learning Python

These will be my forays into learning Python for data science. I'll track my
projects here with a quick note on what each project does.

##Twitter Counter

This code connects to the Twitter API and searches for tweets based on a
keyword provided by the user. It then gets the text of the tweets and counts
all the words (filtering the most common words like "of" or "the") and prints
a word count for the N most common words in tweets that match the search.
There is also an example of using the Twitter API to look up a users stream
and then search through their tweets to get their most commonly used words.

## TOAES Webscrape/Highlight Words

This code loads a webpage and accesses the paragraph tags or finds the text of the book and then deconstructs that into a series of words
and once again counts the occurences of each word. This was designed to reuse
much of the idea from the Twitter Counter, but apply it to data picked out of
a webpage using the BeautifulSoup Library. It also applies the common word
filter. A major improvement this time was to modularize most of the code so it
can be imported. wordCountMaker.py contains all of the code for making the
html, the image, and manipulating the dictionaries built out of the words.
This can be imported and then the user only needs to provide the text from the
beautiful soup library to the dictionary; since this must be done on a page by
page basis.

The Highlight Words addition takes these word counts and creates a dictionary
from the words found (technically two: one with formatting removed and one
with formatting in tact). It then calculates for each word that number of
times it appears relative to the most common word and assigns a color based on
this frequency compared to the sample's mode. It then creates an HTML file
where each word is colored and placed back in order; the colors are currently
in bins of 10%. So if a word is in the top 10% most common words, it will be
red. If it's in the 10-20% most common words, it will be orange. And so on,
until we get to the words that appear with very little frequency, which are
left as black and unbolded, so that there is a contrast. All words that are in the top 
80% most common words are bolded. This macro also makes a plot of the N most common words 
(N is set in the plot making function as "limit"). This also makes a plot of the words and their counts and places it in the HTML page. The most common words in the King James Version of the Bible available in project Guttenburg is shown below.

![60 Most Common Words in KJV](wordCounter/img/bibleWordCountPlot.png)

## MLB Database Analyzer

This code loads in a CSV from http://www.seanlahman.com/baseball-archive/statistics/ that contains stats from all years of the MLB. The code makes nested dictionaries for each player by the year of their stats. So for Jim Bob, there is one dictionary made of sub-dictionaries for each year of stats. So stats['jimbob'][2009] would return a dictionary of Jim Bob's stats from 2009. The code also santizes the inputs, replacing all missing data with -999 so these missing values can be easily checked and removed from future analyses. There are functions to draw the correlations between all possible statistical variable combinations, to compute the career average of a players stats, to remove pitchers from the main batting dictionary, to add whether or not a player has been added to the hall of fame, and to add a players personal information (name, date of birth, etc) to the dictionary so that the dictionary can be fully filtered into "only those players who would be inducted into the hall of fame as a position player (not a pitcher)" and then a machine learning algorithm can be applied to predict if a player will be inducted to the hall of fame (and the personal information can be used to associate the players name with the prediction).

## Pygame Test

This is simply an attempt to make a small interactive session with a few
classes and interaction from the user. There is no "game" really... the user
can spawn a set of ever changing circular objects that move around within a
space. There is a counter that computes the score for each object
(lifetime). This is based on the pygame module that is freely available
online. No more work is planned for this, it was a simple chance to explore
the pygame library, work on infinite loops with user input, and to build a few
classes and class managers.
