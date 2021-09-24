
### What is a classifier?

A classifier is a machine learning model that is used to discriminate different objects based on certain features.

### Principle of Naive Bayes Classifier:

A Naive Bayes classifier is a probabilistic machine learning model that’s used for classification task. The crux of the classifier is based on the Bayes theorem.

#### Bayes Theorem:

![image](https://user-images.githubusercontent.com/11299574/134663393-478b1109-7ee6-412f-bde9-fd034ffdc650.png)

Using Bayes theorem, we can find the probability of A happening, given that B has occurred. Here, B is the evidence and A is the hypothesis. The assumption made here is that the predictors/features are independent. That is presence of one particular feature does not affect the other. Hence it is called naive.


#### Example:

Let us take an example to get some better intuition. Consider the problem of playing golf. The dataset is represented as below.

![image](https://user-images.githubusercontent.com/11299574/134663450-6a223195-9771-4d9a-91d0-c5932352edc3.png)


We classify whether the day is suitable for playing golf, given the features of the day. The columns represent these features and the rows represent individual entries. If we take the first row of the dataset, we can observe that is not suitable for playing golf if the outlook is rainy, temperature is hot, humidity is high and it is not windy. We make two assumptions here, one as stated above we consider that these predictors are independent. That is, if the temperature is hot, it does not necessarily mean that the humidity is high. Another assumption made here is that all the predictors have an equal effect on the outcome. That is, the day being windy does not have more importance in deciding to play golf or not.

According to this example, Bayes theorem can be rewritten as:

![image](https://user-images.githubusercontent.com/11299574/134663607-f9fff6f9-c01d-4ce0-bc57-51de9b595119.png)

The variable y is the class variable(play golf), which represents if it is suitable to play golf or not given the conditions. Variable X represent the parameters/features.
X is given as,

![image](https://user-images.githubusercontent.com/11299574/134663729-9718106a-967a-484e-86e0-228cc4814cae.png)

Here x_1,x_2….x_n represent the features, i.e they can be mapped to outlook, temperature, humidity and windy. By substituting for X and expanding using the chain rule we get,

![image](https://user-images.githubusercontent.com/11299574/134663851-ac4db228-5f31-4055-8a50-882883718ac5.png)

Now, you can obtain the values for each by looking at the dataset and substitute them into the equation. For all entries in the dataset, the denominator does not change, it remain static. Therefore, the denominator can be removed and a proportionality can be introduced.

![image](https://user-images.githubusercontent.com/11299574/134663882-cea89d00-6d91-4967-b939-1f27c09151ea.png)

In our case, the class variable(y) has only two outcomes, yes or no. There could be cases where the classification could be multivariate. Therefore, we need to find the class y with maximum probability.

![image](https://user-images.githubusercontent.com/11299574/134663906-664aadbe-6652-4e1a-b91c-01d21262997c.png)

Using the above function, we can obtain the class, given the predictors.

### Types of Naive Bayes Classifier:

### Multinomial Naive Bayes:
This is mostly used for document classification problem, i.e whether a document belongs to the category of sports, politics, technology etc. The features/predictors used by the classifier are the frequency of the words present in the document.

### Bernoulli Naive Bayes:
This is similar to the multinomial naive bayes but the predictors are boolean variables. The parameters that we use to predict the class variable take up only values yes or no, for example if a word occurs in the text or not.

#### Gaussian Naive Bayes:
When the predictors take up a continuous value and are not discrete, we assume that these values are sampled from a gaussian distribution.

![image](https://user-images.githubusercontent.com/11299574/134663977-eadb7fab-af6d-447e-8c79-4456fc6ce8c1.png)

Gaussian Distribution(Normal Distribution)

Since the way the values are present in the dataset changes, the formula for conditional probability changes to,

![image](https://user-images.githubusercontent.com/11299574/134664008-26cec70a-5dd2-4c92-9ffb-9507395be705.png)

### Conclusion:

Naive Bayes algorithms are mostly used in sentiment analysis, spam filtering, recommendation systems etc. They are fast and easy to implement but their biggest disadvantage is that the requirement of predictors to be independent. In most of the real life cases, the predictors are dependent, this hinders the performance of the classifier.


### Sources 

* [Naive Bayes Classifier](https://towardsdatascience.com/naive-bayes-classifier-81d512f50a7c) 
