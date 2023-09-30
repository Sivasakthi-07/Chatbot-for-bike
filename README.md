# Chatbot-for-bike-details

Here it is very simple process for running these code in your google collab or any other python platform which one you like, just import few things for getting the text from the file and processing it to python by using NLTK 

import io
import random
import string
import warnings
import numpy as np

after importing numpy, import nltk and it will require some additional files for it

import nltk
from nltk.stem import WordNetLemmatizer
nltk.download('popular', quiet=True)

Then, it will get the file from our storage via upload txt file to python platfrom and convert all text into lowercase for understanding and also remove some words.

with open('chatbotdoc.txt','r', encoding='utf8', errors ='ignore') as fin:
    raw = fin.read().lower()
sent_tokens = nltk.sent_tokenize(raw)
word_tokens = nltk.word_tokenize(raw)

lemmer = WordNetLemmatizer()
def LemTokens(tokens):
    return [lemmer.lemmatize(token) for token in tokens]
remove_punct_dict = dict((ord(punct), None) for punct in string.punctuation)
def LemNormalize(text):
    return LemTokens(nltk.word_tokenize(text.lower().translate(remove_punct_dict)))

initialize the greeting for welcome the customer

GREETING_INPUTS = ("hello", "hi", "greetings", "what's up","hey",)
GREETING_RESPONSES = ["hi", "hey", "hi there", "hello", "I am glad! You are talking to me"]

Then , not understandable words were produced by customers then we need to tell them that can't be understandable so please type words correctly by

if(req_tfidf==0):
        parker_response=parker_response+"I am sorry! I don't understand you"
        return parker_response
    else:
        parker_response = parker_response+sent_tokens[idx]
        return parker_response

if customer wants to exit the chat then they will have to do type "bye".

flag=True
print("Hi My name is Paker, I will answer your queries about bikes. If you want to exit, type Bye!")
while(flag==True):
    user_response = input()
    user_response=user_response.lower()
    if(user_response!='bye'):
        if(user_response=='thanks' or user_response=='thank you' ):
            flag=False
            print("PARKER: You are welcome..")
        else:
            if(greeting(user_response)!=None):
                print("PARKER: "+greeting(user_response))
            else:
                print("PARKER: ",end="")
                print(response(user_response))
                sent_tokens.remove(user_response)
    else:
        flag=False
        print("PARKER:Thanks for getting me!!")  
