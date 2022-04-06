# -*- coding: utf-8 -*-
"""
Created on Wed Apr  6 16:13:01 2022

@author: NagaKushal8
"""



# Importing Libraries

import pandas as pd
import re 
from nltk.corpus import stopwords  
from nltk.stem import WordNetLemmatizer
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import confusion_matrix 
from sklearn.metrics import accuracy_score



# Importing dataset 
messages = pd.read_csv('C:/Users/nagku/Desktop/Kaggle/NLP/Spamclassifer()/SMSSpamCollection.txt', sep='\t',names=["label", "message"])


# Pre-processing of the text-data

lm = WordNetLemmatizer()
corpus = []
for i in range(0, len(messages)):
    review = re.sub('[^a-zA-Z]', ' ', messages['message'][i])
    review = review.lower()
    review = review.split()
    
    review = [lm.lemmatize(word) for word in review if not word in stopwords.words('english')]
    review = ' '.join(review)
    corpus.append(review)

# Creating the Bag of words 
tf = TfidfVectorizer(max_features = 2000)
bow=tf.fit_transform(corpus).toarray()

#converting categorical values of labelcolumn  to numeric
Y=pd.get_dummies(messages['label'],drop_first=True)


# diving the data for training and testing purposes
x_train,x_test,y_train,y_test = train_test_split(bow,Y,test_size=0.25)

# Creating the classifier model using nb classifer
model = MultinomialNB().fit(x_train, y_train)

y_pred = model.predict(x_test)

# Evaluating the performance of the classification model (model):
cf = confusion_matrix(y_test,y_pred)

accuracy = accuracy_score(y_test,y_pred)
