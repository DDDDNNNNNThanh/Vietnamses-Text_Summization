# Code KeyBert

This code is a keyword extraction tool called "KeyBert" that uses Natural Language Processing (NLP) techniques to extract relevant keywords from a given document. The code uses the VnCoreNLP library for word and sentence segmentation in Vietnamese text and the SentenceTransformer library to encode the document and candidate keywords into embeddings.

## Related Documents
- [Keyword Extraction Methods from Documents in NLP](https://www.analyticsvidhya.com/blog/2022/03/keyword-extraction-methods-from-documents-in-nlp/#:~:text=Keyword%20extraction%20is%20commonly%20used,and%20phrases%20from%20text%20input.)
- [py_vncorenlp library](https://github.com/vncorenlp/VnCoreNLP#install)

### Code Description:

The code performs the following steps:

1. **Document Preprocessing**: The Vietnamese document is preprocessed, including word and sentence segmentation, using the VnCoreNLP library.

2. **Candidate Keyword Generation**: Candidate keywords are generated using the CountVectorizer from scikit-learn. The n-gram range is set to (1, 1) to consider single words, and English stop words are removed.

3. **Embedding Generation**: The SentenceTransformer library is used to encode the document and candidate keywords into embeddings using the 'distilbert-base-nli-mean-tokens' model.

4. **Keyword Extraction with max_sum_sim**: The `max_sum_sim` function is used to select the top N keywords with the least similarity to each other. It finds the combination of words with the lowest overall similarity among them, ensuring that the selected keywords are diverse and cover different aspects of the document.

5. **Keyword Extraction with mmr**: The `mmr` function (Maximal Marginal Relevance) is used to select the top N keywords with a balance of relevance and diversity. It calculates a score based on relevance and diversity for each candidate keyword and iteratively selects the keywords that maximize the balance between these two aspects.

6. **Print Selected Keywords**: The final selected keywords are printed for both methods, `max_sum_sim` and `mmr`.

The code provides two different approaches for keyword extraction, allowing users to choose between maximizing diversity (using `max_sum_sim`) or finding a balance between relevance and diversity (using `mmr`) based on their specific requirements.

Note: The code assumes that the Vietnamese text has already been loaded into the 'doc' variable. Additionally, the 'py_vncorenlp' and 'SentenceTransformer' libraries need to be installed to run the code successfully.
