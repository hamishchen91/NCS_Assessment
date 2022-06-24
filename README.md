# NCS_Assessment
Cheng CHEN - NCS Data Specialist Assessment


Q1

Q1-a

It is suitable for correlation analysis, but not for ANOVA analysis because there are no groups for doing ANOVA.
It can do the ANOVA analysis after grouping by clustering, however it does not make sense to do ANOVA after clustering.

correlation matrix of the ingredient of additives is as follows:


According to the correlation matrix, it shows high and positive correlation between ingredient a and g, and relatively high correlation among 1) b and h; 2) d, f, h.
Meanwhile, it demonstrates negative relationship between ingredient: 1) a, d, e; 2) c, d, g, h; 3) f, g.
In other words, the ingredient a and g are always added together in the formulations. It is common that the ingredient mixed together with relatively high correlation. Conversely, the additives are not commonly added together with negative relationship stated above.


Q1-b

The distribution of each additive is shown in Graph 1, and the box-plot of each additive is shown in Graph 2. 
Graph 1 and 2 indicate that most of the formulations are without or with less additive f, h and i. For the additive c, it shows two extremes -- some formulations without or with less additive c, but others formulations with high proportion of it. Finally, additives a, b, d, e, and g are the main ingredients for most of the formulation.

Graph 1: Distribution of Additives



Graph 2: Box-plot of Additives

Q1-c
Based on elbow method and Silhouette Coefficient (shown in Graph 3), the optima k of KMeans is k=8. Thus, the distinctive number of formulations present in the dataset is 8.


Graph 3: K Selection
