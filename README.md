# Automatic-Text-Summarization-of-Single-Arabic-Story-using-TF-IDF
This study uses the extractive summarization method TF-IDF algorithm to extract the most important part of the corpus. Two different ways were performed to implement this method with two different sentence selections the first one is to write it from scratch, and the second is to use a library, provided by scikit-learn


Many algorithms are used to create summarization, term frequency-inverse document frequency (TF-IDF) is a famous algorithm for extractive summarization. This project aimed to summarize a single Arabic story to represent the most important sections in the story. TF-IDF is a numerical statistic that shows how important a word is to a document in the collection or corpus. To accomplish the automatic summarization process, this project was divided into two steps one is to write TF-IDF from scratch and the second is to use the library TfidfVectorizer. Eight steps for making a summary in TF-IDF from scratch. First, Convert the story into a list of sentences then Pre-process the text, after that Calculate the presence of each word in each sentence so we can calculate TF by dividing the frequency of a word over the total number of words in the sentence also,  calculate the presence of each word in all sentences so we can calculate (IDF) the number of sentences over the number of the sentence containing the word and take the log of the result, then calculate TF-IDF by multiply TF * IDF. After we have TF-IDF,  sentence scores are calculated as the average of the TF-IDF value of words in the sentence and it is calculated by dividing the total TF-IDF of words in the sentence over the number of distinct words in the sentence. A threshold is calculated which is the average value of the scores of each sentence it is calculated by dividing the total sum of scores of sentences over the number of sentences. For the threshold, a 0.6 value was multiplied by the threshold to control and generate the summary. This number is defined by the user with any value between 0 and 1 according to the goal of the summary. The reason for choosing this value was based on some factors like human evaluation, and accuracy results, and after experimenting with different values, it was found that 0.6 was suitable for the document used for the summary so that the meaning is coherent and understandable without loss in information. Finally, generate a summary by extracting the sentences having scores greater than or equal to the threshold value. 
The second step was divided into three phases preprocessing, scoring or ranking sentences, and summarization the software architecture for this experiment can be seen in Figure 2. In preprocessing and with the help of NLTK package the story is split into a sentence and removed punctuation, and stopwords then tokenized into a list of words for each sentence to apply stem. Stemming is the process of reducing a word to its root by removing the affixes. ISRI Stemmer has been used as it contains the Arabic language.
 Scoring or ranking sentences step aimed to extract the most important sentence and this can be done by TF-IDF algorithm with the help of  TfidfVectorizer, this method is divided into three steps first it calculates the term frequency (TF) second calculates inverse document frequency(IDF), and finally, multiply the result of the term frequency and inverse document frequency to get  TF-IDF final result.
Term Frequency(TF)  is the number of times the term or word appears in a document compared to the total number of words in the document. In this case, the number of times a word appears in a sentence is compared to the total number of words in the sentence. Mathematically can represent a function as:


![image](https://github.com/user-attachments/assets/fc7b9aad-40ac-4325-8dff-e15e3af9252a)

 Inverse document frequency(IDF) is the log of the total number of documents compared to the number of documents that represent a word. The equation of  IDF can be seen below:
                        
![image](https://github.com/user-attachments/assets/f14332a8-7cdd-4e02-a317-041a50555e71)

Then calculate TF-IDF score for a word by multiplying TF and IDF scores.
                                                                TF-IDF = TF *IDF
In order to find the most important sentences, it takes the individual sentences from tokenized sentences and computes the sentence score by taking the sum of TF-IDF, which calculates and determines the most important sentences based on the presence of important words.
After calculating the scores, a heap queue algorithm is used which is a special tree structure. Sentences will be organized in descending order. In this work case, it gives priority to the highest TF-IDF in which the sentence that has a higher score will appear first and the top sentences will be represented in the summary based on the retention rate that can be determined by the user. 
The selection of the sentences is based on the highest TF-IDF and the number of sentences, and this can be controlled by multiplying the number of sentences with any value between 0 and 1. In this work, 0.50 were chosen to retrieve sentences from the original text. Due to different experiments and the accuracy results with keeping the minimal loss of information during the summarization process 0.50 was chosen.







	











![image](https://github.com/user-attachments/assets/b844d891-69d3-4844-8a08-00e7bc6fc8bc)




