# 🧪 Week 3 - Lab Exercise and Assignment

---

# 📑 Table of Contents

- [Section 1: Lab Exercise](#section-1-lab-exercise)
  - [Tasks](#tasks)
- [Section 2: Lab Assignment](#section-2-lab-assignment)
  - [Dataset](#datasets)
  - [Tasks 1](#text-preprocessing)
  - [Tasks 2](#text-representation)
  - [Tasks 4](#visualization-2-relationship-between-review-scores-and-word-usage)
  - [Submission Guidelines](#submission-guidelines)
  
  
---

# 🏋 Section 1: Lab Exercise

## 📌 Objective

In this lab, you will use spaCy to process and clean text data, then visualise word frequencies and word clouds using Seaborn and WordCloud libraries.

## ✅ Prerequisites:
- Jupyter Notebook is set up and running.
- The following Python libraries are installed: spacy, seaborn, matplotlib, and wordcloud.
- Note: spacy may not work with Python 3.13, so you may need to downgrade to 3.12
- The en_core_web_sm model is downloaded for spaCy using the command:
```python
!python -m spacy download en_core_web_sm
```

---

---

## 📜 Instructions

### Step 1: Load spaCy Model and Process Text
Insert the code below into your Jupyter Notebook to load the spaCy English model and process two sample texts.

```python
import spacy

# Load the spaCy English model
nlp = spacy.load("en_core_web_sm")

# Sample text 1
text1 = "Hanoi is a beautiful city with a rich culture. The traffic can be overwhelming, but the food is amazing!"

# Process text with spaCy
doc = nlp(text1)
tokens = [token.text for token in doc]

print(len(tokens), " tokens")
print(tokens)

# Sample text 2
text2 = "Okay, so, like, you know, today—well, actually, uh, I mean, technically, it's, um, February 18th, 2025, right? And, well, Mo, yeah, that’s Mo El-Haj, uh, is, you know, kinda showing us, or, well, more like trying to show us how to, um, I guess, properly visualize, or should I say analyse, text, you know, like, online, at, umm, the, uh, VinUniversity, which, by the way, is in, uh, Hanoi, Vietnam, you know? I mean, honestly, I didn’t even realise, but, well, here we are, sitting, listening, and watching, kinda waiting for something, and then, boom! He’s like, ‘Hey, let’s clean some text,’ and, I mean, obviously, you know, we have to do it right, otherwise, well, it just doesn’t make sense, right? But, like, I dunno, there’s, like, a lot of unnecessary words and, um, extra spaces, and also, weird punctuation—like this! Or… maybe this? You know what I mean? And, uh, that’s why, well, uh, stopwords, yeah, those have to go, and lemmas, too, like, totally important. So, yeah, here we are, watching Mo, at VinUniversity, doing his thing, and, uh, yeah, that’s what’s happening, I guess?"

# Process text with spaCy
doc = nlp(text2)
tokens = [token.text for token in doc]

print(len(tokens), " tokens")
print(tokens)

```

### Step 2: Visualise Word Frequencies and Word Clouds


```python
from collections import Counter
import seaborn as sns
import matplotlib.pyplot as plt

# Function to plot word frequencies
def plot_word_frequencies(tokens, top_n=10):
    word_freq = Counter(tokens)
    sns.barplot(x=list(word_freq.keys())[:top_n], y=list(word_freq.values())[:top_n])
    plt.xticks(rotation=45)
    plt.show()

from wordcloud import WordCloud

# Function to generate a word cloud
def generate_wordcloud(text):
    wordcloud = WordCloud().generate(text)
    plt.figure(figsize=(6, 6))
    plt.imshow(wordcloud, interpolation="bilinear")
    plt.axis("off")
    plt.show()

# Generate visualisations for text1
generate_wordcloud(text1)
plot_word_frequencies(tokens)

```

### Step 3: Remove Stopwords and Punctuation


```python
tokens_no_stop_no_punct = [token.text for token in doc if not token.is_stop and not token.is_punct]

print(len(tokens_no_stop_no_punct), " tokens")
print(tokens_no_stop_no_punct)

# Clean text for visualisation
clean_text = " ".join(tokens_no_stop_no_punct)
generate_wordcloud(clean_text)
plot_word_frequencies(tokens_no_stop_no_punct)

```


### Step 4: Filter Tokens by Length


```python
tokens_no_stop_no_punct = [token.text for token in doc if not token.is_stop and not token.is_punct and len(token.text) > 2]

print(len(tokens_no_stop_no_punct), "tokens")
print(tokens_no_stop_no_punct)

clean_text = " ".join(tokens_no_stop_no_punct)
generate_wordcloud(clean_text)
plot_word_frequencies(tokens_no_stop_no_punct)


```


### Step 5: Custom Stopwords and Number Removal


```python
custom_stopwords = {"know", "like"}

tokens_no_stop_no_punct = [
    token.text for token in doc
    if not token.is_stop and not token.is_punct and len(token.text) > 3 and token.text.lower() not in custom_stopwords and not token.like_num
]

print(len(tokens_no_stop_no_punct), "tokens")
print(tokens_no_stop_no_punct)

clean_text = " ".join(tokens_no_stop_no_punct)
generate_wordcloud(clean_text)
plot_word_frequencies(tokens_no_stop_no_punct)

```
## 📋 **Tasks**: 

1.	Run each code block sequentially.
2.	Observe how the number of tokens decreases as you remove stopwords, punctuation, and short words.
3.	Compare the visualisations and analyse how cleaning the text improves the clarity of key words.


✅ Lab complete! If you haven’t changed the code by trying different examples, please do so. If you have done that, now move to the Lab Assignment.


---

# 🏋 Section 2: Lab Assignment

### 🗒️ NOTES:
1. ✅ **Before you start:** Complete the exercises in Week 3 - Lab Exercise.  
2. 📤 **Submission:** Upload your Jupyter Notebook (`.ipynb` file) to Canvas **before the end of this week**.

---

### 📌 Assignment Details

#### 🟡 Rules:

- 💬 The code must be fully commented.  
-	📝 Print all outputs so results are clearly visible.
-	🐍 Use appropriate libraries to complete the tasks. E.g. SpaCy.
-	🚫 Do not use NaN values—filter or replace missing data where necessary.
-	✅ Your final script should run without errors when executed.


#### 📂 Datasets:
Use the 🔗 [Amazon Fine Food Reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews) dataset from Kaggle: Reviews.csv. Or you can access and download the dataset from this 🔗 [link](https://vinuniversity-my.sharepoint.com/:f:/g/personal/22dang_kh_vinuni_edu_vn/EtnaG0444TBPgrrJTriAUKoBiN44H4UGs3QO1Uen6MSSxQ?e=nt9191)


---

### 📖 Lab Assignment Outline
### 📌 Objective:
The goal of this assignment is to apply advanced techniques for representing text as numbers and visualising the results. You will process and analyse the Amazon Fine Food Reviews dataset using Bag of Words (BoW), TF-IDF, and Word Embeddings (Word2Vec or GloVe), culminating in visualisations to extract insights from the reviews.

### 🗒Dataset:
Use the Amazon Fine Food Reviews dataset, which contains over 500,000 reviews. The dataset is available on Kaggle. Focus on the Text and Score columns. Amazon Fine Food Reviews (You may need to truncate the data if your machine is unable to process the entire dataset, e.g. top 10,000 reviews …etc)


## 📋 **Tasks**: 


#### 1️⃣ Text Preprocessing
🧹 Clean and prepare the text by applying:

- Tokenisation
-	Lowercasing
-	Stopword removal
-	Lemmatization

⚙️ Use Python libraries such as spaCy or NLTK for these steps.

---

#### 2️⃣ Text Representation
Represent the text using:

-	**BoW**: Create a sparse matrix and visualise word frequency distribution.
-	**TF-IDF**: Generate vectors, highlighting the most important words in each document.
-	**Word Embeddings**: Use either Word2Vec or GloVe to capture semantic relationships.

✅ Ensure each method outputs numerical representations for further analysis.

---

#### 3️⃣ Visualization 1: Comparison of Text Representations
**Compare and contrast visual representations of the text using different methods:**

☁️ Word clouds for BoW and TF-IDF:

-	Generate separate word clouds using the Bag of Words and TF-IDF techniques.
-	The word clouds should represent the frequency or importance of words, with larger words indicating higher frequency or importance.
-	Use the WordCloud library to create these visuals.

📊 Heatmaps or bar charts showing the top 20 most frequent or important words:

-	Extract the 20 most frequent words from the BoW model and the 20 most important words from the TF-IDF model.
-	Create bar charts to display the frequency or importance scores of these words.
-	Alternatively, use heatmaps to show the intensity of word occurrences across different reviews.

⚙️ Use libraries such as Matplotlib and Seaborn to generate these visualizations. Ensure that all visualizations are clear, labelled, and easy to interpret.

---


#### 4️⃣ Visualization 2: Relationship Between Review Scores and Word Usage
🔍 Investigate how word usage changes with review scores. Focus on two categories:

- Positive Reviews: Scores of 4 and 5.
- Negative Reviews: Scores of 1 and 2.

🔍 Identify the words that appear frequently in both categories, as well as those that are unique to each category.

🔠 Use word embeddings to visualize clusters of words with similar meanings in each category. For example:

- Generate word embeddings using Word2Vec or GloVe.
- Apply dimensionality reduction techniques such as PCA or t-SNE to reduce the embeddings to 2D space.
- Plot these word clusters using scatter plots, clearly differentiating between positive and negative words.
- Highlight words that are common to both categories using a distinct colour or marker.

🎯 The goal is to visually demonstrate the similarities and differences in language used in positive and negative reviews.

---

#### 5️⃣ Visualization 3: Sentiment Analysis and Temporal Trends
📝 Perform sentiment analysis on the reviews using either TF-IDF or Word Embeddings.

🏷️ Assign sentiment scores to each review based on the words used. For example:

- Use pre-trained sentiment lexicons or machine learning models to classify each review as positive, neutral, or negative.

📊 Visualize sentiment trends over time:

- If the dataset includes review dates, group reviews by month or year and calculate the average sentiment score for each time period.
- Plot these scores using line charts to show how sentiment has changed over time.

📊 Visualize sentiment distribution:
- Use heatmaps or scatter plots to show the distribution of positive, neutral, and negative reviews within the embedding space.
- Ensure that visualisations are clear, with appropriate labels and legends.

🔍

### 🚀 Submission Guidelines

📌 Ensure your Jupyter Notebook includes **all required charts and explanations**  
📂 **File Format:** `Week3_lab_assignment_YourID.ipynb`  
📤 **Upload to:** Canvas **before the deadline**.  

---

🎯 **Good luck and happy coding!** 🚀📊  

