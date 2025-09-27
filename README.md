# Text Cleaning and Preprocessing with NLTK

## Introduction


This repository contains a comprehensive text cleaning function implemented in Python, utilizing the NLTK library. It is designed for preprocessing textual data, especially user reviews or social media content, by removing noise such as URLs, mentions, hashtags, emojis, punctuation, numbers, and stopwords. Additionally, it supports stemming and can return either tokenized output or clean plain text, depending on your needs.

This notebook is ideal for data scientists, NLP practitioners, and researchers looking for a straightforward yet effective preprocessing pipeline for Spanish and English texts.


## Function Description: clean_text

The core of this repository is the `clean_text` function, which performs the following steps:

- **Lowercases** the input text to ensure case-insensitive processing.
- **Removes URLs** to eliminate web links that often do not contribute to semantic meaning.
- **Strips mentions and hashtags**, commonly found in social media data.
- **Eliminates emojis** to reduce noise.
- **Deletes punctuation and numbers** for cleaner tokenization.
- **Replaces line breaks and tabs** with spaces for consistent formatting.
- **Tokenizes** the text into words using NLTK’s tokenizer.
- **Filters out stopwords** depending on the selected language (`'spanish'` or `'english'`).
- Optionally applies **stemming** to reduce words to their root forms.
- Returns either a list of cleaned tokens or a concatenated string of clean text.



## Getting Started

### Requirements
- Python 3.6+
- Libraries:
  - `nltk`
  - `pandas`

You can install dependencies using:

```bash
pip install nltk pandas
```

### Setup NLTK Data

The function requires certain NLTK datasets. Run the following commands (already included in the code) to download the necessary resources:

```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('punkt_tab')  # Optional, for enhanced tokenization
```


## How to Use?
1. Clone the repository (if applicable):

```bash
git clone https://github.com/yourusername/text-cleaning-nltk.git
cd text-cleaning-nltk
```

2. Run the notebook or copy the clean_text function into your own script or Jupyter notebook.
3. Apply the function to your textual data.

Example Usage:

```bash
# Example: English text, no stemming, tokenized output
text = "This is a test tweet with @user, #hashtags, and a link https://example.com!"
cleaned_tokens = clean_text(text, language='english', stemming=0, tokenize_output=1)
print(cleaned_tokens)
```

Output:
``` css
['test', 'tweet', 'hashtags', 'link']
```

---

## Simulated Dataset Example

A simulated dataset of user reviews is included to demonstrate how to apply clean_text in bulk:

```python
import pandas as pd

data = {
    "user": ["Ana", "Luis", "María", "Carlos", "Elena", "Jorge", "Lucía", "Sofía", "Pedro", "Marta"],
    "class": ["Yoga", "Spinning", "HIIT", "Zumba", "Pilates", "Crossfit", "Yoga", "HIIT", "Zumba", "Spinning"],
    "score": [5, 4, 3, 2, 5, 1, 4, 3, 2, 5],
    "review": [
        "I loved the yoga class 😍. Very relaxing and professional.",
        "What a rhythm in spinning! Although the music was way too loud. 🙉",
        "Too intense for me, but effective. 💪💥 #fitness",
        "Zumba was fun, but the room was too crowded 😓",
        "Perfect for stretching muscles and disconnecting from stress.",
        "I didn't like crossfit, too demanding and no explanations.",
        "Good class, but I would have liked more variety in poses.",
        "HIIT was brutal. I'm exhausted, but I’d definitely do it again!",
        "The instructor was great, but the sound system wasn't working properly.",
        "Spinning top! Although the bike seat was uncomfortable 😬"
    ]
}

df = pd.DataFrame(data)
df["cleaned_review"] = df["review"].apply(lambda x: clean_text(x, language='english', stemming=1, tokenize_output=1))

print(df[["user", "class", "score", "review", "cleaned_review"]])
```

To see the results of the simulated DataFrame, please refer to the included Python notebook.

## License
This project is released under the MIT License.



## Contact
For questions or suggestions, please contact:

Email: cesc.blanco98@gmail.com
LinkedIn: https://www.linkedin.com/in/cescblanco

