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
![Cluster 1](https://user-images.githubusercontent.com/80976652/172026009-01e368d6-a9cb-4808-8178-f922bf44d2f7.png)
###### Cluster 2: Rugby
![Cluster_2](https://user-images.githubusercontent.com/80976652/172026077-1e3ff791-8c92-4d6c-a364-1e3cfd348891.png)
###### Cluster 3: Politics
![Cluster_3](https://user-images.githubusercontent.com/80976652/172026094-9ec38de5-246f-4fc9-bbe3-88dd4128a35b.png)
###### Cluster 4: Governance
![Cluster_4](https://user-images.githubusercontent.com/80976652/172026129-e79d273d-3fef-44c7-ab9d-47e7dfaadef2.png)
###### Cluster 5: Economy
![cluster_5](https://user-images.githubusercontent.com/80976652/172026341-12e17baa-a3ef-439b-a077-0e17e2082fc1.png)
###### Cluster 6: Video Games
![cluster_6](https://user-images.githubusercontent.com/80976652/172026462-5c9cb687-4fbd-4573-a801-30d7ef60356b.png)
###### Cluster 7: Tennis
![cluster_7](https://user-images.githubusercontent.com/80976652/172026515-04859796-9800-4f03-bbb2-4a7b9123d433.png)
###### Cluster 8: Web
![cluster_8](https://user-images.githubusercontent.com/80976652/172026563-622ebdf9-e23d-4dc7-989d-34ec29bb1bf9.png)
###### Cluster 9: Music
![cluster_9](https://user-images.githubusercontent.com/80976652/172026658-27b1587c-ae6f-47b1-bfd7-3671616bf19a.png)
###### Cluster 10: Business
![cluster_10](https://user-images.githubusercontent.com/80976652/172026698-076ee6fa-50e5-4777-8ea8-e4074e643813.png)
###### Cluster 11: Russia
![cluster_11](https://user-images.githubusercontent.com/80976652/172026828-b1bb1cb9-d273-4b2f-bbb6-e7c81b5bd9f0.png)
###### Cluster 12: Internet Services
![cluster_12](https://user-images.githubusercontent.com/80976652/172026874-2565af98-cb65-4d64-a370-90acef304a56.png)
###### Cluster 13: Films
![cluster_13](https://user-images.githubusercontent.com/80976652/172026901-187a00c2-569d-4473-90a1-8db4ce472c2b.png)
###### Cluster 14: Football
![cluster_14](https://user-images.githubusercontent.com/80976652/172026944-839cd846-8d8a-42fa-abfe-4fe03c19b5e6.png)
###### Cluster 15: Athletics
![cluster_15](https://user-images.githubusercontent.com/80976652/172026986-3d2df068-991c-464c-9c04-db157af604db.png)
