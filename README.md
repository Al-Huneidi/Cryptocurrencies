# Cryptocurrencies

## Overview

Present visualizations of what cryptocurrencies are on the trading market and how cryptocurrencies could be grouped toward creating a classification for developing a new investment product.

## Objectives

Prepare the data for dimensions reduction with PCA and clustering using K-means.
Reduce data dimensions using PCA algorithms from sklearn.
Predicte clusters using cryptocurrencies data using the K-means algorithm form sklearn.
Create some plots and data tables to present your results.


### Data Preprocessing

Started by loading the data in a Pandas DataFrame named “crypto_df.” 

#### Inspected the data.
Looked at first five rows of dataframe.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Inspect_Data/1_DataFrame_from_csv.png)

Got the number of rows and columns and the datatypes for each column.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Inspect_Data/2_Data_Types_For_Each_Column.png)

Continued with the following data preprocessing tasks:

	•	Removed all cryptocurrencies that aren’t trading. 
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/1_Coins_Not_Trading.png)

	•	Removed all cryptocurrencies that don’t have an algorithm defined.
	•	Removed the IsTrading column.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/2_DataFrame_with_IsTrading_Column%20Removed.png)

	•	Removed all cryptocurrencies with at least one null value. Checked dataframe to ensure
	the number of rows were reduced as an indication that all rows with nulls were removed:
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/3_Proof_Null_Values_Removed.png)

	•	Removed all cryptocurrencies without coins mined. 
	•	Stored the names of all cryptocurrencies on a DataFramed named coins_name, 
	and used the crypto_df.index as the index for this new DataFrame. 
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/4_New_DataFrame_coins_name_df.png)

	•	Removed the CoinName column.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/5_DataFrame_with_CoinsName_Column_Removed.png)

	•	Used get_dummies to create dummies variables for all of the text features, 
	and stored the resulting data on a DataFrame named X. Snippet of output after creating dummies.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/6_Snippet_Dummies.png)

	•	Used the StandardScaler from sklearn  to standardize all of the data from the X DataFrame.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Preprocessing/7_Standardized_data.png)
  
  
### Reducing Data Dimensions Using PCA
Used the PCA algorithm from sklearn to reduce the dimensions of the X DataFrame down to three principal components. 
Created a DataFrame named “pcs_df” that includes the following columns: 
PC 1, PC 2, and PC 3. Used the crypto_df.index as the index for this new DataFrame.

![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/PCA_Dimensions/PCA_Data_Transformed_to_DataFrame.png)


### Clustering Cryptocurrencies Using K-means
Used the KMeans Algorithm from sklearn to cluster the cryptocurrencies using the PCA data.

	•	Created an elbow curve to find the best value for K, and used
	the pcs_df DataFrame to find how many clusters to use in the KMeans algorithm. 
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Clustering_K-means/1_Elbow_Curve.png)

	•	With the defined best value for K, ran the K-means algorithm to predict the K clusters
	for the cryptocurrencies’ data. Used the pcs_df to run the K-means algorithm.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Clustering_K-means/2_PCS_DataFrame_With_Predicitve_Class.png)

	•	Created a new DataFrame named “clustered_df,” that includes the following columns: 
	Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class,
	while maintaining the index of the crypto_df DataFrame as is shown below:
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Clustering_K-means/3_clusterd_df.png)

### Visualizing Results
Data visualizations of the final results.
	•	Created a 3D scatter plot using Plotly Express to plot the clusters using the clustered_df DataFrame.
	Included the following parameters on the plot: hover_name="CoinName" and hover_data=["Algorithm"] to show this
	additional info on each data point. 
Top-down image of 3D plot:
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/1_3D.png)

Image to include data upon hover:
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/2_3D_with_Hover_label.png)

	•	Used hvplot.table to create a data table with all the current tradable cryptocurrencies
	with columns: CoinName, Algorithm, ProofType, TotalCoinSupply, TotalCoinsMined, and Class.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/3_hover_table.png)

	•	Created a scatter plot using hvplot.scatter to present the clustered data about cryptocurrencies having x="TotalCoinsMined" and y="TotalCoinSupply" to contrast the number of available coins versus the total number of mined coins. Included the hover_cols=["CoinName"] parameter to include the cryptocurrency name on each data point.
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/4_Scatterplot.png)

Image to include data upon hover:
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/5_Scatter_hover.png)

### Recommendation to Improve Analysis Results

I was curious about an outlier on the scatter plot, BitTorrent. I did some research to identify why it is an outlier. BitTorrent is a communication protocol, not a cryptocurrency. 
![alt text](https://github.com/Al-Huneidi/Cryptocurrencies/blob/master/Screenshots/Visualizations/6_BitTorrent_Outlier.png)


I recommend the dataset be cleaned further to eliminate entries that are not true cryptocurrencies but rather just built on BlockChain.  


About BitTorrent:  

BitTorrent (abbreviated to BT) is a communication protocol for peer-to-peer file sharing (P2P) which is used to distribute data and electronic files over the Internet.
BitTorrent is one of the most common protocols for transferring large files, such as digital video files containing TV shows or video clips or digital audio files containing songs. Peer-to-peer networks have been estimated to collectively account for approximately 43% to 70% of all Internet traffic (depending on location) as of February 2009.[1] In February 2013, BitTorrent was responsible for 3.35% of all worldwide bandwidth, more than half of the 6% of total bandwidth dedicated to file sharing.[2] Source: https://en.wikipedia.org/wiki/BitTorrent. 

Resource:

crypto_data.csv
