# CODE-ACCORD: A Corpus of Building Regulatory Data for Rule Generation towards Automatic Compliance Checking

## Data Collection

## Data Annotation
Our work is mainly focused on extracting information from text to support rule generation. 
There are two key types of information found in the text: named entities and relations, which are essential for 
comprehending the ideas conveyed in natural language. Hence, our primary focus was on annotating entities and relations.

More details about our annotation strategy with sample annotations are available in [Annotation_Strategy_V1.0.0.pdf]().

All our annotated data are available within [annotated_data]() folder. Within the subfolders entities and relations, 
there are three .csv files named *all.csv*, *train.csv* and *test.csv*. *all.csv* contains the full dataset. 
*train.csv* has 80% of the full dataset, which can be used to train machine learning models and *test.csv* has the 
remaining 20\%, which can be used for models' performance testing. More details about the file formats are described below.

### Entities

The format of an entity data file available within the annotated_data/entities folder is as follows:

| Attribute         | Description                                                                    |
|-------------------|--------------------------------------------------------------------------------|
| example_id        | Unique ID assigned for each sentence                                           |
| content           | Original textual content of the sentence                                       |
| processed_content | Tokenised (using NLTK's word_tokenize package) textual content of the sentence |
| label             | Entity labelled sequence in IOB format                                       |
| metadata          | Additional information of sentence (i.e. original approved document from which the sentence is extracted)                                       |


### Relations

The format of a relation data file available within the annotated_data/relations folder is as follows:


| Attribute       | Description                                                                    |
|-----------------|--------------------------------------------------------------------------------|
| example_id      | Unique ID assigned for each sentence                                           |
| content         | Original textual content of the sentence                                       |
| metadata        | Additional information of sentence (i.e. original approved document from which the sentence is extracted) |
| tagged_sentence | Sentence with tagged entity pair                                       |
| relation_type   | Category of the relation in between the tagged entity pair                     |
