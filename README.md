#Naive Bayes 

Objective
There are two programs present in the zip file. One is data_cleaning.py, which will demonstrate
how I cleaned the data provided on your website. The second one is NB_model.py, which will
train and test the model or calculate the probability that a word classifies as positive or negative
depending on the input.

Implementation Details
data_cleaning.py uses the folder “pos” to create a training data frame and then appends the
negative data frame created from the “neg” folder. I do the same process to create the testing
data frame. The function “form_df(path, df)” will go through each file in the folder, get rid of
unnecessary punctuation, then split the whole text into a string list consisting of whole words. I
add each new word as a column of the data frame. If it already exists, then it just keeps count of
how many times the word appears in the same text. Then I get rid of columns where the word is
less than 4 characters long in order to filter out common words like “the, am, I, on.” Then I drop
any columns in which a word only appeared once in a single text file. I do the same thing in the
function “form_testing_DF(path, DF)”, but streamlined it to better accommodate what I needed
to do with the testing data inside the model. For example, I left Null values to better identify if a
word had appeared in a text in order to find its’ probability of negative or positive weight. At the
end, I saved my data frames as CSV files.

For NB_model.py my approach was to read in my CSV files labeled as training data and
testing data. Drop the index column that. My “train_models(df)” function will take in the training
data frame and I will calculate the necessary values for the Naive Bayes Theorem by counting
the number of times a word shows up on a positive text file and when it shows up on a negative
text file. I save the probabilities in 2 dictionaries. One for negative probabilities and one for
positive. When I test my model with the “test_model(df)” function, I go row by row as each row
represents a document. If a column on that row is not null, then it means the word appeared in
the text. I take the probability of the word being positive and of being negative from the
dictionaries I formed earlier. I follow Naive Bayes Theorem by getting the product of the
probability of being positive times the probability of each word that appears in the text to
measure the probability that the text will be positive. I do the same to calculate the probability of
the text being negative by using the negative dictionary. I will take the highest probability as the
classification of positive or negative. I count how many the model got right and divide it by the
number of tested documents, and I receive an accuracy score percentage. This program can
also take in words as arguments to test if it is a likely positive or negative word.

Running The Program
In order to run these programs, make sure you have Pandas installed.

To run data_cleaning.py you must just call the python file on the command line and add the
path containing all the files of the project.
Python data_cleaning.py “path\of\project”
It will create the data frames if you would like to see them working. However, I supplied the
cleaned data sets in order to save time.
e
To run NB_model.py you can pass two different arguments:
To get the score of the Test Data you can run:
python NB_model.py score
To test a series of words for the probability of negative or positive weight in a
document you can run:
Python NB_model.py test, example1, example2, etc…
