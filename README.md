# NER-from-HTML
extract and evaluate NER extraction from HTML news pages

This notebook provides an implementation of Named Entity Recognition (NER) using both transformer-based models and statistical models. 

## Data Handling 
* We need clean (html-free) data but when I tried to clean the data directly with regular expressions this caused all the data to have the following problems 
  * have much of the metadata for every article which is noise and actually did not have any data or entities 
  * the text now cannot be splitted into sentences or paragraphs because fullstops is also in the end of every abbreviation
* The idea is to use the HTML tags to extract to correct data and annotations before removing them; the input data as HTML pages to be splitted into paragraphs using the `<PREAMBLE>`, `<TEXT>`, and `<P>` tags respectively as shown in the code. this extracts clean html free and correct paragraphs.  
The named entities are extracted from the `<ENAMEX>` tag and the data is used to compare the performance of transformer-based models and statistical models from spaCy. 
* There are some entities that came into multiple words not single word or token so the format of the data to be words or exact full entity was crucial and greatly influenced the results, I have tried both but finally used the tokens format as this gives much more details at the evaluation step as provided by the pip package 'nerevaluate' that we used for evaluation. 

## Requirements

- Python 3.x
- spaCy
- transformers
- BeautifulSoup
- nerevaluate

## How to run

1. you can run the a copy of the notebook on colab with drive mounting as I did
2. or you can download it to run it locally

## Model Comparison

The notebook compares the performance of transformer-based models and statistical models from spaCy on the extracted named entities. The results of the comparison are presented in the form of a confusion matrix and F1 score for every possible way of evaluation as shown in the nerevaluate docs.

## Note

The notebook uses a small dataset for demonstration purposes. In order to improve the performance of the models, a larger dataset should be used. Additionally, the pre-processing of the HTML data and the extraction of named entities can be improved to enhance the performance of the models.

