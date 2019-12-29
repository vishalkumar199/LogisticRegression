# Logistic Regression
**Objective**: The primary objective is to implement the Logistic Regression on the DonorChoose Dataset and Classify whether the project will get approved (1) or not (0) and measure the accuracy on the Test dataset.

## Dataset
The DonorsChoose Data Set contains train.csv and resources.csv files.

**train.csv** contains
* project_id (A unique identifier for the proposed project)
* project_title (Title of the project)
* project_grade_category (Grade level of students for which the project is targeted)
* project_subject_categories (One or more (comma-separated) subject categories for the project from enumerated list of values)
* school_state (State where school is located (Two-letter U.S. postal code))
* project_subject_subcategories (One or more (comma-separated) subject subcategories for the project)
* project-resource_summary (An explanation of the resources needed for the project.)
* project_essay_1 (First application essay)
* project_essay_2 (second application essay)
* project_essay_3 (third application essay)
* project_essay_4 (fourth application essay)
* project_submitted_datetime (Datetime when project application was submitted)
* teacher_id (A unique identifier for the teacher of the proposed project)
* teacher_prefix (Teacher's title)
* teacher_number_of_previously_posted_projects (Number of project applications previously submitted by the same teacher)
* project_is_approved (A binary flag indicating whether DonorsChoose approved the project. A value of 0 indicates the project was not approved, and a value of 1 indicates the project was approved)

**Additionally, the resources.csv data set provides more data about the resources required for each project**

Each line in this file represents a resource required by a project:

* id (A project_id value from the train.csv)
* description (Desciption of the resource)
* quantity (Quantity of the resource required)
* price (Price of the resource required)

## Sampling Techniques (Stratified Sampling)

If the number of values belonging to each class are unbalanced, using stratified sampling is a good thing. We are basically asking the model to take the training and test set such that the class proportion is same as of the whole dataset, which is the right thing to do.
## Test,Train and CV Size
  * Test Size(33%)
  * Cv Size(22%)
  * Train Size(45%)
## Features not used in Training
  * project_id
  * project_essay_1,project_essay_2,project_essay_3,project_essay_4(combined and replaced with column 'essay')
  * project_submitted_datetime
  * teacher_id
## vectorizing Method for Text(used)
* Bow
  * We convert text to a numerical representation called a feature vector.
  * A feature vector can be as simple as a list of numbers.
* TFIDF
  * tf-idf stands for Term frequency-inverse document frequency.
  * tf-idf is a weighting scheme that assigns each term in a document a weight based on its term frequency (tf) and inverse document frequency (idf)
* AVG W2VEC(google pretrained model)
  * It’s 1.5GB! It includes word vectors for a vocabulary of 3 million words and phrases that they trained on roughly 100 billion words from a Google News dataset. 
  * The vector length is 300 features.
* TFIDF using google pretrained model
  * tf-idf is a weighting scheme that assigns each term in a document a weight based on its term frequency (tf) and inverse document frequency (idf)
## Normalization of numerical features
  * MinMaxScaler from scikit-learn.
  * StandardScaler from scikit-learn.
## Logistic Regression(Features used)
* set 1(BOW):
  * All numerical features (Standardized)
  * Categorical features (CountVectorizer)
  * Text features (CountVectorizer)
* set 2(TFIDF):
  * All numerical features (Standardized)
  * Categorical features (CountVectorizer)
  * Text features (TfidfVectorizer)
* set 3(AVGW2VEC):
  * All numerical features (Standardized)
  * Categorical features (CountVectorizer)
  * Text features (Google Pretrained Model)
* set 4(TFIDF Using Avgw2vec):
  * All numerical features (Standardized)
  * Categorical features (CountVectorizer)
  * Text features (Tfidf Using Avgw2vec)
* set 5(Polarity Scores of `essay` features):
  * All numerical features (Normalized)
  * Categorical features (CountVectorizer)
  * Text features (Polarity Scores)
  * Count of words in `essay` features.
## Python Library (required)
* prettytable (**pip install prettytable**)
  * to present result in a tabular format.
* tqdm (**pip install tqdm**)
  *  add progress bars to Python code.

## Conclusion
  
  |    Vectorizer   |        Model        | Hyperparameter(C) | Train Auc | Test AUC |
  | --------------- | ------------------- | ----------------- | --------- | -------- |
  |       BoW       | LOgistic Regression |        0.1        |   0.746   |  0.681   |
  |      Tf-idf     | LOgistic Regression |         1         |   0.794   |  0.633   |
  |    avg-w2vec    | LOgistic Regression |         1         |   0.734   |  0.705   |
  |   tf-avg-w2vec  | LOgistic Regression |        0.5        |   0.729   |  0.698   |
  | Polarity scores | LOgistic Regression |        0.5        |   0.635   |  0.629   |

## Dataset link: 
**(https://www.kaggle.com/donorschoose/io)**
