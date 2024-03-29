
# ChatGPT Grade Predictor
![WhatsApp Image 2024-01-19 at 19 31 54](banner4.png) <br>
### Project Overview
The ChatGPT Grade Predictor is a Machine Learning project for the CS 412: Machine Learning course at Sabanci University. The project is aimed at exploring the correlation between student interactions with ChatGPT and their assignment scores. Leveraging various techniques and numerous machine learning models, this project seeks to predict grades with a focus on creative and innovative approaches.

### Dataset
The dataset includes a collection of ChatGPT interaction logs in HTML format and corresponding assignment scores. Each log file is uniquely identified, enabling a match with the respective scores. These HTML files can be located at the `project-material/dataset` folder.

### Objectives
- To preprocess and analyse ChatGPT interaction data through the HTML files in our dataset.
- To engineer features that effectively capture the essence of the interactions, and understand the patterns to predict the respective score for the homework for each student.
- To develop and evaluate models capable of predicting assignment scores.
- To explore creative and novel approaches in data handling and model creation regarding grade prediction for homework through students' ChatGPT interaction.

## OVERVIEW OF THE REPOSITORY: 

**1. Preprocessing:** During our preprocessing sections in our project we have taken action to clean, transform, and organize raw data into a suitable format, ensuring it is free of inconsistencies and optimized for analysis. <br> 
<img width="721" alt="Screenshot 2024-01-19 at 18 53 42" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/162c50ef-3e33-4089-8b03-e4659c112531"> <br> 
As a part of our preprocessing for the project can be seen above, we have worked on several approaches. These approaches during our preprocessing procedure have been explained in detail in our methodology section below. 

**2. Feature engineering:** For our Feature Engineering section in our project we have aimed to select, manipulate, and transform raw data into meaningful and relevant features that enhance the performance and accuracy of the model. We have decided to display some of the actions that we have taken through images and brief explanations below.
   
<img width="724" alt="Screenshot 2024-01-19 at 18 59 45" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/32762329-08bd-4473-9bed-64dd6e4db398"> <br> 
- Gives sentimental value of the user prompts by emotion analysis

<img width="855" alt="Screenshot 2024-01-19 at 19 01 05" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/8047ac16-9bc0-4648-84ad-9b6312b75344"> <br> 
- Checks for the similarity of the question asked with the actual question

<img width="986" alt="Screenshot 2024-01-19 at 19 01 16" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/23d06cf1-30a3-4ee4-9d2b-c0fdba543ada"> <br> 
- Checks if the questions were solved one by one or in a disorganized way

                                **There are many more features implemented which can be seen in the ipynb file**

**3. Results:** shows the performance of the model
<img width="483" alt="Screenshot 2024-01-19 at 19 17 35" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/417c7793-fdfc-41c8-be29-1b917926d845"><br> 
	Average R^2 and MSE values of the model with cross-validation and scalar

## METHODOLOGY: 

### A. Preprocessing:

To explain the actions taken in the preprocessing part of our project we have aimed to work on several approaches: 

1. Removing the HTML tags
2. Converting text to lowercase
3. Removing special characters and punctuation
4. Tokenization
5. Removing stop words
6. Lemmatization

Then we continued on our preprocessing procedure, being more considerate and careful after further examining the dataset. After this examination, we have decided to move on with the added preprocessing actions:

7.  Removing further non-ASCII characters (Irrelevant letters were not preserved)
8.  Removing words that include numbers
9.  Removing words that include less than 3 characters or more than 25 characters
    (Unnecessarily short or long words were not preserved due to their irrelevancy in the analysis)
10. Removing numbers
11. Removing user data with less than 5 prompts

After this procedure of preprocessing, we then moved on to work on feature engineering.

### B. Feature Engineering:

In the feature engineering part of the project, we have worked on producing creative, and effective features that aimed to better predict the scores for the homework. These features that were developed and used to predict scores can be categorised as below.

1. **Sentiment Analysis:**

- **Emotion Analysis (disgust, fear, joy, sadness, surprise, trust, anticipation, positive, negative):** Utilizing tools for automated sentiment analysis to determine the emotional tone of user messages. Our hypothesis was to find a link between negative emotions such as disgust, sadness and fear and being confused or frustrated, which will affect the grade of the homework.
- - **Polarity and Subjectivity Scores (total\_subjectivity, avg\_subjectivity, total\_polarity, avg\_ polarity):** Quantifying the sentiment of user messages in terms of positivity/negativity (polarity) and objectivity/subjectivity. TextBlob library is used and insights about the overall sentiment and subjectivity of user interactions are provided.
  
2. **User Interaction Patterns and Language Use:**

- **Inclusion of Specific Words (user\_clarify\_point, gpt\_clarify\_point):** Identifying the presence of words indicating correctness or errors in user prompts including "no, misunderstood, incorrect, sorry" to identify clarifying done by both the user and ChatGPT.
- **Use of uppercase letters (gpt\_caps\_rate, user\_caps\_rate)**  **:** Counting the number of words in all caps to infer emphasis or strong emotion.

3. **Conversational Dynamics and Responsiveness:**

- **Frequency of Question and Exclamation Marks (question\_marks, exclamation\_marks):** Analyzing punctuation usage to understand query types and emphasis.
- **ChatGPT Response Analysis:** Studying the similarity in ChatGPT's responses and looking for correction indicators (like "apologies ") to gauge the user's understanding and ChatGPT's guidance.
- **Readability Score (flesch\_readibility):** Evaluating the complexity of the text in the conversation.
- **Code and Mathematical Expression Patterns (math\_expressions, math\_expressions\_gpt):** Analyzing the structure and occurrence of code snippets or mathematical expressions in the conversation.

4. **Question-Answering Behavior and Sequence:**

- **Resolution Time for Questions (Q1, Q2…):**  Best cosine similarity according to specific question. (TFIDF was used in this procedure to create vectors which was then led to check the cosine similarity in our analysis. BoW and Word2Vec were also used yet TFIDF resulted in a better outcome hence we have then moved on with the implementation which made use of TFIDF.)
- **Question attempt count (Q1\_count, Q2\_count…):** The primary goal of these features (Q1_count, Q2_count, etc.) is to quantify the number of attempts or prompts made to solve each specific question in a dataset. 
- **Order of Questioning (solve\_one\_by\_one):** Assessing whether the user followed a logical flow or jumped between questions in a disorganized manner.

5. Other Features: All the included features that are not explained in detail above can be seen in the heatmap in the following section (promt\_avg\_char, respone\_avg\_char, smog\_index and the existing features).

6. Further Analysis - Model Training and Evaluation:

In this phase of the project, we focus on the following steps to train and evaluate our models:

- In the regression part of the project we have worked on our analysis by making use of RandomForest, Decision Tree, and Linear Regression. Comparatively, the best outcome was produced through the RandomForest implementation hence we have continued our project along with that implementation.
- Cross-validation: We have assessed the performance of the model and ensured its generalizability.
- Splitting the dataset into training and test: We have ensured that both datasets are representative of the overall distribution.
- Stratification: Since the dataset is highly skewed, stratification ensures that each split (e.g., training and testing sets) has a proportionate representation of the different classes or categories present in the dataset. Stratification was used togetherly along with Cross-validation implementation in our project.
- Feature scale normalization: Ensuring that all features contribute equally to the model training.
- Regularization: In this part of the project, features were penalized to have a better outcome in the prediction of grades for the homework. 
  
## RESULTS: 

Through our code where we have worked on the random selection of features automatically, we have aimed to get the best R^2 score. Through this implementation, we have produced the set of features that led us to get the best R^2 score in our project. We have also made use of other implementations to get better feature sets such as Information Gain. However, the result of these implementations did not lead to the sets of features to have a better R^2 score.

The already presented features that were displayed in the .ipynb file of the project were also tested to see if they resulted in a better outcome of prediction for the homework scores. However, this test result of prediction resulted in a negative R^2 score.

Here there is both base code R^2 and mean squared error and our best R^2 score both scores are preprocessed and cross-verified:

![grades](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/123778340/a886bfa3-d5f6-4728-8faa-f5a0359f1031)

Feature set we used to get the best result = ['code', '#hyperparameter', '#thanks', 'anger', 'Q_0', 'total_polarity', 'trust', 'smog_index', '#split', '#math_expressions_gpt', '#entropy', 'grade']

<img width="877" alt="Screenshot 2024-01-19 at 18 48 13" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/15192c28-11ae-452f-b880-61ef938ee1f9"> <br> 

The distribution of homework scores shows how uneven and skewed the data is.

![WhatsApp Image 2024-01-19 at 19 41 56](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/313d09fa-646e-48fd-b60f-077a974d8ad6) <br> 

Grade distribution after the outliers that have low grades and low prompt numbers are discarded.

<img width="901" alt="Screenshot 2024-01-19 at 18 48 55" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/e8d0151c-5f42-449c-b39d-dcbaff947ad9"> <br> 

Boxplot showing the distribution of grades given whether "thanks" was used or not.

![heatmap_features](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/f43dc6aa-8aa2-4974-8506-0772d7e082df) <br> 

Heatmap of the existing features and added engineered features and their correlations are shown on a heatmap.

<img width="879" alt="Screenshot 2024-01-19 at 18 49 04" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/5681afa1-28db-4c98-b16a-6487d6229ec9"> <br> 

Code Patterns in GPT responses and the homework grades.

<img width="483" alt="Screenshot 2024-01-19 at 19 17 35" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/eb47a89a-3ec9-4102-9478-cf8ba27dcf20"> <br> 

Average R^2 and MSE values of the model with cross-validation and scalar

![WhatsApp Image 2024-01-19 at 19 58 12](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/910f2d2f-aa49-4387-bc04-86aa92e9f2b4) <br> 

Comparison of R2 scores of different methods.

## TEAM CONTRIBUTIONS: 
1. İsmail Çakmak: Conversational dynamics and responsiveness, cross-validation and normalization.
2. Göktuğ Gökyılmaz: Question-answering behavior and responsiveness, testing the subsets of features.
3. Mustafa Harun Şendur: User interaction patterns and language usage, data visualization.
4. Pınar Şen: Sentiment analysis with subjectivity scores and emotion analysis, preparing the README file.

Brainstorming for new feature ideas, division of work and determining the preprocessing steps were done as a team. 


<img width="952" alt="Screenshot 2024-01-19 at 19 28 53" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/c43eaca1-8bb6-4fa1-8ced-68d608656e41"> <br> 
(Image created by DALL-E, 2024)
