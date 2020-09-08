Problem Statement: Servicenow optimization ticket classification using NLP

Due to the rise of usage of virtual systems, support ticket systems have come into prominence.
Addressing the issue tickets to appropriate person or unit in the support team has critical importance in order to provide 
improved end user satisfaction while ensuring better allotment of support recourses. we have systems which provide the user to choose the related 
categories or unit within defined categories may seem like better, but the systems some times are not useful because of those users,
especially new users which have never used the system before or have doubt, usually have no idea about the related category or department.
In this system, bag of word approach, machine learning techniques and other algorithms which proven performance in text processing are used. 
It reduces manual efforts and human errors while ensuring high service levels and improved end-user satisfaction
 
1.Proposed System
The proposed system basically contains a phase classification process to assign issue ticket
to related support unit. The classification aims to detect the related category of ticket
which is directly related to the department of the issue . For example an issue ticket describing
network connection problem must be directed to the network  category/department.

2. Implementation and Experimental Results
The recommended system is implemented using previously labeled data.

2.1 Dataset

1.Here the data set we have used receives the issue in form of mail. 
2.We have columns (Ticket,Address,Title,Description,Source,MA_Title,MA_Description,MA_Support_Group,MA_Mis_Assigned_Support_Group,Person,Team) 
3.Ticket unique alphanumercal number assign when person raise a ticket.
4.Address of person who have raise a ticket. 5.Title is short subject of issue. 
6.Description is a breif about a issue. 7.Source is email and some are blank in our dataset. 
8.MA_Title and MA_Description is same as Title and Description
9.MA_Support_Group:This is our target column which has many groups to which ticket is assigned. 
10.MA_Mis_Assigned_Support_Group 11.Team: To which team the person belongs to.

Target Column:'MA_Support_Group' we need to predict the group to which are ticket would be assigned.

2.2 Pre-Preparation
In the preparation step, purifying description of tickets from email is carried out.

1.Expanding Contractions
Contractions are shortened version of words or syllables
Examples would be, do not to don’t 

2. Removing accented characters
Usually in any text corpus, you might be dealing with accented characters/letters, especially if you only want to analyze the English language. 
Hence, we need to make sure that these characters are converted and standardized into ASCII characters.

3.Scrube data(Removing Special Characters)
Special characters and symbols are usually non-alphanumeric characters or even occasionally numeric characters (depending on the problem), 
which add to the extra noise in unstructured text. Usually, simple regular expressions (regexes) can be used to remove them.

4.Stemming 
Word stems are also known as the base form of a word.

5.Lemmatization
Lemmatization is very similar to stemming, where we remove word affixes to get to the base form of a word.

2.3 Feature Extraction

1.Bag of word
Based on bag of word approach, to convert the text data into numerical form, each term in the
dataset is considered as an attribute which is independent of each other. A dictionary is
constructed by using these attributes. Using the indexes of the dictionary each ticket is
represented as a vector each element of which refers the term weighting coefficient. 

2. TF-IDF
A further method which is the most frequently used is term frequency- inverse document
frequency (tf-idf). The tf-idf value increases comparatively to the number of times a term
appears in the document, but is offset by the frequency of the term in the corpus. 

3.Topic Modelling
1.Gensim :Gensim is a Python library for topic modelling, document 
indexing and similarity retrieval with large corpora. Target audience is the natural language processing (NLP)

2.We have used LdaMulticore model as it offers plenty of useful features like process Pools or process safe Queues
 that were used for the multicore LDA implementation.
 
3.pyLDAvis
pyLDAvis is a interactive LDA visualization python package.
The area of circle represents the importance of each topic over the entire corpus, the distance between 
the center of circles indicate the similarity between topics. For each topic, the histogram on the 
right side listed the top 30 most relevant terms.

2.4 Train and Test split.
2.5 Building ML and Neural Net models
1.Build support vector machine classifier which has given F1-score of about 0.88

Note: As we have multiclass classification problem we must use f1-score as a metric.

2.We have done parameter tuning for model and have used Grid Search Cross Validation to find best parameters for AdaBoostClassifier,
RandomForestClassifier,GradientBoostingClassifier,XGBClassifier.

3.plot confusion matrix ,to find the performance of a classification algorithm.

4.Build a simple neural net architecture with train accuracy as 0.99 and validation accuracy as 0.75 but it is overfitting .

5.We again build a simple neural net with optimizer as 'adam' with train accuracy as 0.99 and validation accuracy as 0.70 
but overfitting is reduce compare to previous model.

6.We have build layer of LSTM it has given train accuracy as 0.97 and validation accuracy as 0.67.

7.We have added layer of dropout with LSTM to reduce overfitting and got train accuracy as 0.96 and validation accuracy as 0.66

Note: In keras we don't have F1-score as default matrix so we have used accuracy as metrix.

3. Conclusion
This usecase  to assign tickets automatically, a model based on
supervised machine learning algorithms is proposed. Dataset consisting of previously
categorized tickets are used to train classification algorithms. Bag of words approach is
utilized to extract features vectors. Morphological analysis of terms is performed to avoid
data sparseness problem and decrease the vector size for this TFIDF is used.
we have implemented Ml model like support vector machine,RandomForestClassifier,AdaBoostClassifier and
 Neural Net with LSTM .
 
4.Future Work

We can further classify it as the second classification tries to
determine the related subcategory or unit under the specified category that describes which
type of the problem in the determined department.
example: Here we have identified it as issue with Human Resource(HR) department
So in second classification we would identify it as  recruiting, training and development,
compensation and benefits administration, health and safety within human resource departments .
