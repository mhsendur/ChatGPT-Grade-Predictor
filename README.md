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

## OVERVIEW OF THE REPOSITORY: (_Link different script and code pieces used and explain their function for the project_)

1. Preprocessing:
  1. link:
  2. function: cleans, transforms, and organizes raw data into a suitable format, ensuring it's free of inconsistencies and optimized for analysis
2. Feature engineering:
  1. link:
  2. function: selects, manipulates, and transforms raw data into meaningful and relevant features that enhance the performance and accuracy of the model
3. Results:
  1. link:
  2. function: the performance and accuracy of the model

## METHODOLOGY: (_High-level explanation of things considered and solutions offered_.)

### A. Preprocessing:

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

### B. Feature Engineering:

1. **Sentiment Analysis:**

- **Emotion Analysis (disgust, fear, joy, sadness, surprise, trust, anticipation, positive, negative):** Utilizing tools for automated sentiment analysis to determine the emotional tone of user messages. Detected "highest\_emotions" and "affect\_frequencies" using the NRC Lexicon. Our hypothesis was to find a link between negative emotions such as disgust, sadness and fear and being confused or frustrated, which will have an effect on the grade of the homeworks.
- **Friendliness Level (??):** Average friendliness of the users were assessed by analyzing greetings and polite expressions. We assumed a more friendlier tone could change the effectiveness of ChatGPT's tendency to solve questions. Word2Vec converts words into vectors in a high-dimensional space. Words with similar meanings have similar vector representations. This model is used to transform both the user text and a predefined set of friendly words into their vector representations. The mean vector of these words is computed using the Word2Vec model, resulting in a vector representation of "friendliness". The friendliness score is calculated by measuring the cosine similarity between the user text vector and the predefined "friendly" vector.
- **Polarity and Subjectivity Scores (total\_subjectivity, avg\_subjectivity, total\_polarity, avg\_ polarity):** Quantifying the sentiment of user messages in terms of positivity/negativity (polarity) and objectivity/subjectivity. TextBlob library is used and insights about the overall sentiment and subjectivity of user interactions are provided.

2. **User Interaction Patterns and Language Use:**

- **Inclusion of Specific Words (user\_clarify\_point, gpt\_clarify\_point):** Identifying the presence of words indicating correctness or errors in user prompts including "no, misunderstood, incorrect, sorry" to identify clarifying done by both the user and ChatGPT.
- **Use of uppercase letters (gpt\_caps\_rate, user\_caps\_rate)**  **:** Counting the number of words in all caps to infer emphasis or strong emotion.
- **Message Similarity Analysis (?? ):** Examining the similarity between user messages to identify repetitive queries, which might correlate with lower performance of the student due to confusion.

3. **Conversational Dynamics and Responsiveness:**

- **Frequency of Question and Exclamation Marks (question\_marks, exclamation\_marks):** Analyzing punctuation usage to understand query types and emphasis.
- **ChatGPT Response Analysis (??):** Studying the similarity in ChatGPT's responses and looking for correction indicators (like "apologies ") to gauge the user's understanding and ChatGPT's guidance.
- **Readability Score (flesch\_readibility):** Evaluating the complexity of the text in the conversation.
- **Code and Mathematical Expression Patterns (math\_expressions, math\_expressions\_gpt):** Analyzing the structure and occurrence of code snippets or mathematical expressions in the conversation.

4. **Question-Answering Behavior and Sequence:**

- **Resolution Time for Questions (Q1, Q2…):** Tracking how many prompts were needed to resolve each question, indicating the depth and complexity of the inquiry.
- **Retroactive Check (Q1\_count, Q2\_count…):** Identifying if and how often users return to previous topics, suggesting review or confusion.
- **Order of Questioning (solve\_one\_by\_one) :** Assessing whether the user followed a logical flow or jumped between questions in a disorganized manner.

# RESULTS: (_Experimental findings supported by figures, tables etc.__)_

# TEAM CONTRIBUTIONS: (_List all team members by their names and how they contributed to the project_)

1. İsmail Çakmak:
2. Göktuğ Gökyılmaz:
3. Mustafa Harun Şendur:
4. Pınar Şen:
