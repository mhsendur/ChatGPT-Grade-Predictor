![WhatsApp Image 2024-01-19 at 19 31 54](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/61429361-58a5-4b04-9b11-d64865fcc11d) <br> 
(Image created by DALL-E, 2024)

# ChatGPT Grade Predictor

### Project Overview
The ChatGPT Grade Predictor is a Machine Learning project aimed at exploring the correlation between student interactions with ChatGPT and their assignment scores. Leveraging various techniques and numerous machine learning models, this project seeks to predict grades with a focus on creative and innovative approaches.

### Dataset
The dataset includes a collection of ChatGPT interaction logs in HTML format and corresponding assignment scores. Each log file is uniquely identified, enabling a match with the respective scores.

### Objectives
- To preprocess and analyse ChatGPT interaction data.
- To engineer features that effectively capture the essence of the interactions.
- To develop and evaluate models capable of predicting assignment scores.
- To explore creative and novel approaches in data handling and model creation.

### OVERVIEW OF THE REPOSITORY: 

**1. Preprocessing:** cleans, transforms, and organizes raw data into a suitable format, ensuring it's free of inconsistencies and optimized for analysis <br> 
<img width="276" alt="Screenshot 2024-01-19 at 18 52 48" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/441666e7-4503-4fe4-8afe-6782fb79a989"> <br> 
some cells need preprocessing and some do not
<img width="721" alt="Screenshot 2024-01-19 at 18 53 42" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/162c50ef-3e33-4089-8b03-e4659c112531"> <br> 
preprocessing steps

**3. Feature engineering:** selects, manipulates, and transforms raw data into meaningful and relevant features that enhance the performance and accuracy of the model
   
<img width="941" alt="Screenshot 2024-01-19 at 18 55 50" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/e12b76d2-35cc-487f-a7ec-c0808667e36b"> <br> 
looks for keywords and mathemetical expressions

<img width="724" alt="Screenshot 2024-01-19 at 18 59 45" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/32762329-08bd-4473-9bed-64dd6e4db398"> <br> 
gives sentimental value of the user prompts by emotion analysis

<img width="855" alt="Screenshot 2024-01-19 at 19 01 05" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/8047ac16-9bc0-4648-84ad-9b6312b75344"> <br> 
checks for the similarity of the question asked with the actual question

<img width="986" alt="Screenshot 2024-01-19 at 19 01 16" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/23d06cf1-30a3-4ee4-9d2b-c0fdba543ada"> <br> 
checks if the questions were solved one by one or in a disorganized way

                                AND THERE ARE MANY MORE FEATURES!!!

**4. Results:** shows the performance of the model
<img width="483" alt="Screenshot 2024-01-19 at 19 17 35" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/417c7793-fdfc-41c8-be29-1b917926d845"><br> 
	Average R^2 and MSE values of the model with cross-validation and scalar

### METHODOLOGY: 

## A. Preprocessing:

1. Removing user data with less than 5 prompts
2. Removing html tags
3. Converting text to lowercase
4. Removing special characters and punctuation
5. Tokenization
6. Removing stop words
7. Stemming
8. Stratification: since the dataset is highly skewed, stratification ensures that each split (eg. training and testing sets) has a proportionate representation of the different classes or categories present in the dataset.
9. Splitting the dataset into training and test.
10. Feature scale normalization: ensures that all features contribute equally to the model training
11. Cross-validation: assesses the performance of the model.

## B. Feature Engineering:

1. **Sentiment Analysis:**

- **Emotion Analysis (disgust, fear, joy, sadness, surprise, trust, anticipation, positive, negative):** Utilizing tools for automated sentiment analysis to determine the emotional tone of user messages. Detected "highest\_emotions" and "affect\_frequencies" using the NRC Lexicon. Our hypothesis was to find a link between negative emotions such as disgust, sadness and fear and being confused or frustrated, which will have an effect on the grade of the homeworks.
- - **Polarity and Subjectivity Scores (total\_subjectivity, avg\_subjectivity, total\_polarity, avg\_ polarity):** Quantifying the sentiment of user messages in terms of positivity/negativity (polarity) and objectivity/subjectivity. TextBlob library is used and insights about the overall sentiment and subjectivity of user interactions are provided.
- - ** Categorization of Question Types: Checked whether the questions asked by the user are "conceptual", "factual" or "problem solving" questions.
- **Friendliness Level:** Average friendliness of the users were assessed by analyzing greetings and polite expressions. We assumed a more friendlier tone could change the effectiveness of ChatGPT's tendency to solve questions. The mean vector of these words is computed using the Word2Vec model, resulting in a vector representation of "friendliness". The friendliness score is calculated by measuring the cosine similarity between the user text vector and the predefined "friendly" vector. We ended up deleting this feature because it did not improve the model and dowloaded 1.5 GB everytime the cell ran.
  
2. **User Interaction Patterns and Language Use:**

- **Inclusion of Specific Words (user\_clarify\_point, gpt\_clarify\_point):** Identifying the presence of words indicating correctness or errors in user prompts including "no, misunderstood, incorrect, sorry" to identify clarifying done by both the user and ChatGPT.
- **Use of uppercase letters (gpt\_caps\_rate, user\_caps\_rate)**  **:** Counting the number of words in all caps to infer emphasis or strong emotion.
- **Message Similarity Analysis (?? ):** Examining the similarity between user messages to identify repetitive queries, which might correlate with lower performance of the student due to confusion.

3. **Conversational Dynamics and Responsiveness:**

- **Frequency of Question and Exclamation Marks (question\_marks, exclamation\_marks):** Analyzing punctuation usage to understand query types and emphasis.
- **ChatGPT Response Analysis:** Studying the similarity in ChatGPT's responses and looking for correction indicators (like "apologies ") to gauge the user's understanding and ChatGPT's guidance.
- **Readability Score (flesch\_readibility):** Evaluating the complexity of the text in the conversation.
- **Code and Mathematical Expression Patterns (math\_expressions, math\_expressions\_gpt):** Analyzing the structure and occurrence of code snippets or mathematical expressions in the conversation.

4. **Question-Answering Behavior and Sequence:**

- **Resolution Time for Questions (Q1, Q2…):** Tracking how many prompts were needed to resolve each question, indicating the depth and complexity of the inquiry.
- **Retroactive Check (Q1\_count, Q2\_count…):** Identifying if and how often users return to previous topics, suggesting review or confusion.
- **Order of Questioning (solve\_one\_by\_one) :** Assessing whether the user followed a logical flow or jumped between questions in a disorganized manner.

### RESULTS: 

<img width="877" alt="Screenshot 2024-01-19 at 18 48 13" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/15192c28-11ae-452f-b880-61ef938ee1f9"> <br> 

Distrubiution of homework scores show how uneven and skewed the data is.

<img width="901" alt="Screenshot 2024-01-19 at 18 48 55" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/e8d0151c-5f42-449c-b39d-dcbaff947ad9"> <br> 

Boxplot showing the distribution of grades given that "thanks" was used or not.

![heatmap_features](https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/f43dc6aa-8aa2-4974-8506-0772d7e082df) <br> 

Heatmap of the existing features and added engineered features and their correlations shown on a heatmap.

<img width="879" alt="Screenshot 2024-01-19 at 18 49 04" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/5681afa1-28db-4c98-b16a-6487d6229ec9"> <br> 

Code Patterns in GPT responses and the homework grades.

<img width="483" alt="Screenshot 2024-01-19 at 19 17 35" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/eb47a89a-3ec9-4102-9478-cf8ba27dcf20"> <br> 

Average R^2 and MSE values of the model with cross-validation and scalar

### TEAM CONTRIBUTIONS: 
1. İsmail Çakmak: Conversational dynamics and responsiveness, cross validation and normalization.
2. Göktuğ Gökyılmaz: Question answering behavior and responsiveness, testing the subsets of features.
3. Mustafa Harun Şendur: User interaction patterns and language usage, data visualization.
4. Pınar Şen: Sentiment analysis, question categorization and preparing the README file.

Brainstorming for new feature ideas, division of work and determining the preprocessing steps were done as a team. 


<img width="952" alt="Screenshot 2024-01-19 at 19 28 53" src="https://github.com/mhsendur/ChatGPT-Grade-Predictor/assets/91570013/c43eaca1-8bb6-4fa1-8ced-68d608656e41"> <br> 
(Image created by DALL-E, 2024)
