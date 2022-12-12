# Cryptocurrencies

## Overview
The purpose of this project is to use data from the cyprto data CSV to provide a report and visualization of currently traded cryptocurrencies that can be grouped together to create a new classification system. This report can help Accountability Accounting offer customers a new investment portfolio in cryptocurrencies.

### Tools used in this projects
* Jupyter Notebooks
* Scikit-learn
* Plotly
* hvPlot
* Pandas

## Results

First thing that needs to be done is **Data Preprocessing**. Since the outcome data isn't known, preprocessing is needed to fit an unsupervised Machine Learning model to be able to run a clustering algorithm to group the cryptocurrencies.  

The original dataset contained 1,252 entries. After keeping the cryptocurrencies that are currently trading, the dataset shrinks to 1,144. The dataset is removed of any cryptocurrencies that don't have a working algorithm, aren't being mined, and any null values within the dataset. The final results identified 532 tradable cryptocurrencies. 

![D1P1](https://user-images.githubusercontent.com/109183214/207119238-d55e3e16-bf69-460b-9571-1764b56ed8a5.png)

Since the unsupervised Machine Learning model cannot work with string values, the Algorithm and ProofType were convert to and true/false number value using get_dummies().

![D1P2](https://user-images.githubusercontent.com/109183214/207120461-c1273eb7-0215-4d99-a520-11ea1fd5e043.png)

The next step is the **Principal Component Analysis (PCA)** step which will speed up the machine learning algorithms when the number of features are too high. Since the Algorithm and ProofType columns were split into the specific algorithm and proof type, the number of features went up. By using PCA, a new dataframe is created with three principal components.

![D2P1](https://user-images.githubusercontent.com/109183214/207126229-6968ffa9-509c-4834-a5a5-3fd9013db97a.png)

After PCA, the data is clustered using the K-Means algorithm. In the algorithm, the Elbow Curve is used to determine the best number of clusters needed for the algorithm to group the objects by.

![D3P1](https://user-images.githubusercontent.com/109183214/207127611-36543917-5d3e-4890-b7b6-9b0452853bb9.png)

The Elbow Curve method shows that it is best to set K = 4 clusters for the K-Means algorithm. After the model is fitted and the clusters are predicted, the original dataframe is concatentate with the dataframe with the principal components. The class for each cryptocurrency is added at the end.

![D3P2](https://user-images.githubusercontent.com/109183214/207129346-954f8ec4-214a-45e4-9110-fbddb54debed.png)

The final part is visualizing the data. This is done using hvPlot and Plotly. With the dataframe created from the last step, a 3D scatter plot can be created to show the different group for investors.

![D4P1](https://user-images.githubusercontent.com/109183214/207130476-f912621f-53e6-4555-b074-297d157c6bb7.png)

However, in order to show a scatter of the total coins mind vs total coins supply, the two columns are pulled and scaled using MinMaxScaler().fit_transform().

![D4P3](https://user-images.githubusercontent.com/109183214/207130948-5cce091e-96cd-4519-96bd-03cf8198d489.png)

With that done, a new dataframe is created for plotting the scatter points. Using hvplot, the scatter plot will look like the following.

![D4P2](https://user-images.githubusercontent.com/109183214/207131196-2f90a1f5-28c9-411f-919b-274e17b80a57.png)
