# bnaug (Bangla Text Augmentation)
__bnaug__ is a text augmentation tool for Bangla text.

## Installation
```
pip install bnaug
```
- Dependencies
    - pytorch >=1.7.0
    
## Sentence Augmentation
### Token Replacement
- Mask generation based augmentation

    ```py
    from augban.sentence import TokenReplacement

    tokr = TokenReplacement()
    text = "আমি ঢাকায় বাস করি।"
    output = tokr.masking_based(text)
    ```

- Word2Vec based augmentation

    ```py
    from augban.sentence import TokenReplacement

    tokr = TokenReplacement()
    text = "আমি ঢাকায় বাস করি।"
    model = "msc/bangla_word2vec/bnwiki_word2vec.model"
    output = tokr.word2vec_based(text, model=model)
    print(output)
    ```

- Glove based augmentation

    ```py
    from augban.sentence import TokenReplacement

    tokr = TokenReplacement()
    text = "আমি ঢাকায় বাস করি।"
    vector = "msc/bn_glove.300d.txt"
    output = tokr.glove_based(text, vector_path=vector)
    print(output)
    ```

### Back Translation
Back translation based augmentation fist translate Bangla sentence to English and then again translate the English to Bangla.

```py
from bnaug.sentence import BackTranslation

bt = BackTranslation()
text = "বাংলা ভাষা আন্দোলন তদানীন্তন পূর্ব পাকিস্তানে সংঘটিত একটি সাংস্কৃতিক ও রাজনৈতিক আন্দোলন। "
output = bt.get_augmented_sentences(text)
print(output)

```