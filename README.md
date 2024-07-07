# COUPLE MOVIES RECOMMENDER

# 📗 Table of Contents
- [🚀 Subject](#subject)
- [🛠 Dependencies](#dependencies)
- [🧪 Methodology and Experiments](#methodology)
- [🎞️ Conclusion](#conclusion)
- [👥 Author](#author)

## 🚀 Subject <a name="subject"></a>
The objective of this project is to develop a sophisticated movie recommendation system tailored specifically for couples. By analyzing and integrating the preferences of both individuals in the couple, the system aims to recommend movies that are likely to be enjoyed by both partners. 

## 🛠 Dependencies <a name="dependencies"></a>
- pandas
- scikit-surprise
- scipy
- numpy

## 🧪 Methodology and Experiments <a name="methodology"></a>
The first step of the creation of this recommender system was to load the dataset. The data used in this project are:
- MovieLens ml-1m
- IMDb dataset

In order to make recommendations to a couple, we will first make movies recommendations for each user and then combine them using the mean, creating a `couple score`. This ensures that when one person will probably hate a movie, it won't be the most recommended. We also remove movies that were by at least one user. 

After loading the dataset and taking a look at the data, an important step was to take into account the common problems we face in recommender systems. 
- Popularity bias: some systems disproportionately favors popular items, leading to recommendations that often include only the most well-know items. 
- Cold start: it is difficult to generate accurate recommendations when a new user or a new item joins the system. Indeed there is insufficient data about preferences and similarities.
- Scalability issue: the system must be able to process and generate recommendations in a reasonable time frame, requiring efficient algorithms and computational resources
- Data sparsity: dealing with a sparse matrix make it challenging to find patterns and similarities to generate accurate recommendations
- Fairness: it is important to make sure that recommendations are fair and unbiased

However, there is one method that is the state-of-the-art solution for sparse data problem, which is matrix factorisation. 

Which is why, in order to solve those problems the first system built was a SVD. Indeed, Singular Value Decomposition is a matrix factorisation algorithm that breaks down a matrix into core components. 

However, the predicted ratings determined by the algorithm were not really satisfying. The sparse interaction matrix contained lots of NaN number which were replaced by 0. However when reconstructing this matrix using the components found by the algorithm, these values were replaced by very small values close to 0. So the algorithm just predicts that unseen films are disliked by the user, which is not true. 

Which is why, the second model implemented is a variant of SVD, the Funk SVD, which is designed to work with sparse matrix. It is also very efficient and has a computational efficiency. 

After the implementation, the model was evaluated on the test set, using RMSE metrics, to check if the recommendations were fair and logic.


## 🎞️ Results and Conclusion <a name="conclusion"></a>
As can be seen in the notebook, the final version of the recommender system model is pretty decent. The RMSE score is very low, less than one which means that the average prediction error is less than one rating point. Moreover, the result obtained when doing a cross-validation is stable. 

Furthermore, with the example chosen at the end of the notebook, we can easily understand why the system recommended these films, since the predicted scores of both users for this movie are pretty high.

## 👥 Author <a name="author"></a>
Léa Margery