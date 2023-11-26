# Assignment 5: Feature Engineering with automated tools

### Group Name: TheBoys
### Group Members

| Name                                     | Matrix Number |
| :---------------------------------------- | :-------------: | 
| Pang Chern Hong             |MCS231006      |
| Wu JiaMing             |MCS221033      |
| Liu KaiYuan            |MCS231020      |
| Nian Cong             |MCS231007      |
## Featuretools
This automated tools possess 3 main components which are entity set, deep features synthesis, and feature primitives. Where entity set is a collection of entities and the relationships among these features, while deep feature synthesis is an automated method for performing feature engineering on relational and temporal data, and feature primitives are often methods used to create new features in a dataset. 

In this project we implement the entity set to the deep feature synthesis already, while for some reasons the results is dissapointing, and thus it can not really be trusted.

## H2O.ai
This automated tool uses built-in AI to automatically recommend new features, identify bias, and create feature insights. In this projrct, We separate the data into train set and test set, then the H2O implement various of the machine learning and regression models to test out the predictive powers of them, top 10 models were selected and listed. 

This tool is more appropriate to be used in our case, especially it is well-suited for housing price prediction tasks that involve extensive data. H2O leverages parallelized processing, allowing it to distribute computations across multiple nodes. This results in faster model training times, particularly beneficial when dealing with substantial amounts of housing data.
