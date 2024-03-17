# Winequality-Red
# Introduction
The two datasets are related to red and white variants of the Portuguese "Vinho Verde" wine. For more details, consult the reference [Cortez et al., 2009]. Due to privacy and logistic issues, only physicochemical (inputs) and sensory (the output) variables are available (e.g. there is no data about grape types, wine brand, wine selling price, etc.).  

# Dataset   
[Orijinal Dataset](https://github.com/ManoPart/winequality-red/blob/a10c805c78b2e3ce38f027339c6f8b13183f3b6f/winequality-red.csv)  
[Kaggle Dataset](https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009)  
# Paper   
[Paper](https://github.com/ManoPart/winequality-red/blob/06cddc8bbcecf1f92cc1fdd1c325c5397dbcf776/paper_red.pdf)  
# Code Result   
1.Combine all CSV files in a DataFrame and then call the results as below  
2.Display data type  
3.Data details, including count, mean and standard deviation  

# Objective  
Use machine learning to determine which physiochemical properties make a wine 'good'!  
1 - File Reader (for csv) to linear correlation node and to interactive histogram for basic EDA.  
2- File Reader to 'Rule Engine Node' to turn the 10 point scale to dichtome variable (good wine and rest), the code to put in the rule engine is something like this:  

quality > 6.5 => "good"  
3- Rule Engine Node output to input of Column Filter node to filter out your original 10point feature (this prevent leaking)  
4- Column Filter Node output to input of Partitioning Node (your standard train/tes split, e.g. 75%/25%, choose 'random' or 'stratified')  
5- Partitioning Node train data split output to input of Train data split to input Decision Tree Learner node and  
6- Partitioning Node test data split output to input Decision Tree predictor Node  
7- Decision Tree learner Node output to input Decision Tree Node input  
8- Decision Tree output to input ROC Node.. (here you can evaluate your model base on AUC value)  
