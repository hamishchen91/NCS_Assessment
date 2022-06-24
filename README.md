# NCS_Assessment
Cheng CHEN - NCS Data Specialist Assessment


Q1

Q1-a

It is suitable for correlation analysis, but not for ANOVA analysis because there are no groups for doing ANOVA.
It can do the ANOVA analysis after grouping by clustering, however it does not make sense to do ANOVA after clustering.

correlation matrix of the ingredient of additives is as follows:
![image](https://user-images.githubusercontent.com/66156262/175518324-1a7d3538-afee-4b1a-be3f-259c57e099d5.png)


According to the correlation matrix, it shows high and positive correlation between ingredient a and g, and relatively high correlation among 1) b and h; 2) d, f, h.
Meanwhile, it demonstrates negative relationship between ingredient: 1) a, d, e; 2) c, d, g, h; 3) f, g.
In other words, the ingredient a and g are always added together in the formulations. It is common that the ingredient mixed together with relatively high correlation. Conversely, the additives are not commonly added together with negative relationship stated above.


Q1-b

The distribution of each additive is shown in Graph 1, and the box-plot of each additive is shown in Graph 2. 
Graph 1 and 2 indicate that most of the formulations are without or with less additive f, h and i. For the additive c, it shows two extremes -- some formulations without or with less additive c, but others formulations with high proportion of it. Finally, additives a, b, d, e, and g are the main ingredients for most of the formulation.

![image](https://user-images.githubusercontent.com/66156262/175518338-64e0bc94-2eb3-4ea0-8bbe-cb86ca898003.png)

Graph 1: Distribution of Additives


![image](https://user-images.githubusercontent.com/66156262/175518353-ef564058-cd5e-4ca1-a0aa-e273f518d44a.png)

Graph 2: Box-plot of Additives

Q1-c
Based on elbow method and Silhouette Coefficient (shown in Graph 3), the optima k of KMeans is k=8. Thus, the distinctive number of formulations present in the dataset is 8.

![image](https://user-images.githubusercontent.com/66156262/175518387-40f30b5f-3f78-47ef-b33d-f3bf6755fc77.png)
![image](https://user-images.githubusercontent.com/66156262/175518399-d28e14fe-29e9-4757-9961-25ea7e7f2519.png)

Graph 3: K Selection

Graph 4 shows the means of each additives (after max-min standardization) and the radar map of each cluster of formulations. It states that each cluster contains different proportions among 9 additives. For example, cluster 0 and cluster 2 (with similar proportion of additive c, e, f, and i) are significantly different on additive a, b, d, g, h.

![image](https://user-images.githubusercontent.com/66156262/175548069-8e094e52-cb46-4580-adf0-11cc34ffe7f0.png)

Graph 4: Clusters’ Additives Means and Radar Map


Q2

Feature Engineering

Firstly, HA_Harvested is dividend by 1000 to make it keep the same scale with other features. Temperature range is also created which is defined by Max_Temp - Min_Temp, indicating the variance of temperature of current month. Finally, The Date is converted to dummy variable of months.
Moreover, some aggregation features are generated:
![1656099369843_B1330BCC-2D3B-4e88-8283-027D2833177E](https://user-images.githubusercontent.com/66156262/175655804-30175a15-9f85-4dba-8dc2-a1cc54f0595a.png)


The features above calculate the statistics of original factor within recent x (3, 6, 9, 12) months, implying the lagging effects of the weather on the FFB.

Modeling

The model input (X) 68 features into the linear regression model. However, it will cause problem if these features are thrown into the trainer. Thus, we first run the Lasso regression the do the features selection, and the parameter is set as Lasso(alpha = 1, precompute = True, tol = 1e-7). After the features selection by Lasso regression, the linear regression is run with the selected features. The samples split by 70% for training and 30% of testing. Because of aggregation features with 12 months, I tried exclude the first 12 rows of data and compared the results without significantly different. Thus the model input kept the first 12 rows of data where the aggregation features does not aggregate the whole period. 
The R square is 0.5 and MSE is 0.03 of this model. The results are shown in following graphs.

![image](https://user-images.githubusercontent.com/66156262/175655829-2ec118ea-d49f-4128-93dc-acdc0dec4b3a.png)

![image](https://user-images.githubusercontent.com/66156262/175655840-ea709f09-ca43-490c-ba3c-827328cf8b85.png)


Analysis
The model indicates that the FFB is positively affected by the recent precipitation, last 12 months average of soil moisture, and last 6 months average of HA_Harvested. At the same time, it shows negative effects of recent HA_Harvested, average soil moisture within last 3/6 month, the variance of soil moisture in last 9 months and precipitation in last 3 months.



Q3

Q3-a
a.What is the probability of the word “data” occurring in each line ? 
![image](https://user-images.githubusercontent.com/66156262/175692578-802f1774-68b6-40b6-8783-e70276a10446.png)


Q3-b
b.What is the distribution of distinct word counts across all the lines ? 
![image](https://user-images.githubusercontent.com/66156262/175692731-02526a3c-7bc8-4d37-abdc-3e4657cfdb27.png)


Q3-c
c.What is the probability of the word “analytics” occurring after the word “data” ? 

Answer: It is 1/3
![image](https://user-images.githubusercontent.com/66156262/175692874-233a3b85-4b59-46c7-a07c-7eb944df0a1c.png)

