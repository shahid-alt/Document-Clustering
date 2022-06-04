# NLP Task
### Document Clustering and Optimization

##### Our Dataset contains 2225 Files which we need to segregate into separate clusters. 
##### First I've read the files and inserted them in a Pandas DataFrame for convenience. Then takes place is the Preprocessing of texts. 


1.   Cleaning of New lines and unnecassary characters in the document
2.   Lemmatization of the words.

> I've used Lemmatization instead of Stemming because Lemmatization      understands the context in which the word is being used. The Stanza library is used for the process.

3. Removal of STOPWORDS from our document.

> For this the Gensim library is used for removing the stopwords because after removal of stopwords the document made more sense as compared to other available libraries.

4. Removal of whitespaces and other non-aphanumerical characters.

##### Now the task of preprocessing is done now we'll perform the main task i.e Clustering the documents. Since, the model won't understand words we need to convert into a form in which our model will understand so, we'll generate vectors using TF-IDF Vectorizer. 

##### After generating the vector we perform some manipulation to get more accurate results. So KMeans uses Euclidean Distance to form clusters but for our task it isn't a perfect choice because Cosine Similarity works much better in Text Clustering task. 

##### Our input vector is normalized using L2 Normalization, the normalized input vector is given to our cosine similarity function.

> `X_normalized = preprocessing.normalize(X,norm='l2')`

> `X_input = 2 - 2*cosine_similarity(X_normalized)`

##### Input vector is sorted. Now we perform clustering we don't know what should be the value of K. So let's use different values of K between [5,20]. We'll use Elbow-method to determine the value of K. After plotting the inertia values against K values we find K=15 to be optimal choice.

##### We fit the preprocessed data in KMeans model with K=15, Labels are generated for each document.

##### To find out which label potential belongs to which category we use WordCloud.Plotting WordCloud for each label we can determine which category they fit in.

###### Cluster 1: Mobile Phones
###### Cluster 2: Rugby
###### Cluster 3: Politics
###### Cluster 4: Governance
###### Cluster 5: Economy
###### Cluster 6: Video Games
###### Cluster 7: Tennis
###### Cluster 8: Web
###### Cluster 9: Music
###### Cluster 10: Business
###### Cluster 11: Russia
###### Cluster 12: Internet Services
###### Cluster 13: Films
###### Cluster 14: Football
###### Cluster 15: Athletics
