Classification Model Pros and Cons (Generalized)

* Logistic Regression
	* Pros
		* low variance
		* provides probabilities for outcomes
		* works well with diagonal (feature) decision boundaries
		* NOTE: logistic regression can also be used with kernel methods
	* Cons
		* high bias
		* Categorical data needs to be changed to binary / ordinal

* Decision Trees
	* Regular (not bagged or boosted)
		* Pros
			* easy to interpret visually when the trees only
				contain several levels
			* Can easily handle qualitative (categorical) features
			* Works well with decision boundaries parellel to the feature axis
		* Cons
			* prone to overfitting
			* possible issues with diagonal decision boundaries or complex decision boundaries
			* can change a lot due to just adding couple of new points (so very sensitive to noise!)  
			
	* Bagged Trees : train multiple trees using bootstrapped data
		to reduce variance and prevent overfitting 
		* Pros
			* reduces variance in comparison to regular decision trees
			* Can provide variable importance measures
				* classification: Gini index
				* regression: RSS
			* Can easily handle qualitative (categorical) features
			* Out of bag (OOB) estimates can be used for model validation
			* Can form complex decision boundaries (unlike regular decision tree)
		* Cons
			* Not as easy to visually interpret
			* Does not reduce variance if the features are correlated    
			
	* Random Forest (improvement over bagging - only choose split from randomly selected subset of all features)
		* Pros
			* Decorrelates trees (relative to bagging trees)
				* important when dealing with mulitple features which may be correlated
			* reduced variance (relative to regular trees)
			* Can form complex decision boundaries (unlike regular decision tree)
			* almost all pros of bagged trees apply here.
		* Cons
			* Not as easy to visually interpret


	* Boosted Trees : Similar to bagging, but learns sequentially and builds off
		previous trees - trying to minimize error previous ones had
		* Pros
			* Somewhat more interpretable than bagging trees/random forest
				as the user can define the size of each tree resulting in 
				a collection of stumps (1 level) which can be viewed as an additive model
			* Can easily handle qualitative (categorical) features
			* Performs very well on the training data
		* Cons
			* Unlike bagging and random forests, can overfit if number of trees is too large
			* Slower than bagging / Random forest since trees are made sequentially and they're not independent

* SVM
	* Pros
		* Performs similarly to logistic regression when linear separation
		* Performs well with non-linear boundary depending on the kernel used
		* Handle high dimensional data well
	* Cons
		* Susceptible to overfitting/training issues depending on kernel
		* Categorical data needs to be changed to one hot or binary or ordinal


* Neural Network (This section needs further information based on 
	different types of NN's)


* Naive Bayes
	* Pros
		* Computationally fast
		* Simple to implement
		* Works well with high dimensions
		* Handles categorical data easily
	* Cons
		* Relies on independence assumption and will perform 
			badly if this assumption is not met
