# Spam Classification of Emails

### Models Used
* Logistic Regression
* Decision Trees
* Naive Bayes

### Requirements
* Python 3.6.10  
* Numpy 1.18.4  
* Scikit-learn 0.23.1
* Scipy 1.4.1


### Steps to run:

1. Run the preprocessing file to extract the data from email, get the clean text after removing stopwords, punctuations and upload to ES after splitting into training and testing.      

      python preprocessing.py \
      --dirpath <path to emails folder> \
      --labels <path to labels index file> \
      --index <ES index name> \
      --seed 4

2. Get the unigrams from the Elastic Search.         

      python getUnigrams.py \
      --index <ES index name>

3. Build matrix and run the models.    

      python spamClassifier.py \
      --index <ES index name> \
      --labels <path to labels index file> \
      --features <features file path> \
      --cutoff <no of features u want to select from unigrams> \
      --result <output path folder> \
      --model <model types are : reg, logit(default), tree, nb(naive bayes)> \
      --sparse (use only when u want to create sparse matrix)

  
### Results

<img src="https://github.com/Arushi04/Spam-Classification/blob/master/images/models.png" width="550" height="350">
<img src="https://github.com/Arushi04/Spam-Classification/blob/master/images/sparse_models.png" width="600" height="300">


Top 10 words after running Logistic Regression on unigrams sparse matrix:

('freebsd', 1.1172201336086656).   
('click', 1.1067116575308757).    
('antivir', 1.079915881679438).    
('penis', 1.0705047080248018).     
('opt', 1.0648006849173453).    
('girl', 1.0265354745168107).    
('adf', 1.0224262305744003).    
('website', 0.9591053071640367).     
('products', 0.8749953047612927).    
('remove', 0.8748610351597089).     

       







