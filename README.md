# CODE-ACCORD: A Corpus of Building Regulatory Data for Rule Generation towards Automatic Compliance Checking

## Data Collection
The CODE-ACCORD corpus contains annotated sentences from the building regulations of England and Finland, and has been developed as part of the Horizon European project for Automated Compliance Checks for Construction, Renovation or Demolition Works (ACCORD). The corpus is in English, and it consists of both the English Building Regulations and the English translation of the Finnish National Building Code. 

In both England and Finland, text regulations are published in PDF documents and available online to the public. There is a combined total of 33 documents, consisting of 23 documents for English regulations, which span 1455 pages, and 10 documents for Finnish regulations, covering 140 pages. All PDF documents sourced from both English and Finnish data repositories were converted into plain text. Following this, a gold standard was developed following a semi-automated methodology. Initially, an automated sentence filtering task was conducted to retain only those sentences that met regulatory criteria, including quantitative requirements, subjective requirements, and deontic logic. 

For each country, a data folder is created. More specifically, for England, a folder named [English Regulations](https://github.com/Accord-Project/CODE-ACCORD/tree/main/English%20Regulations) is created. Similarly, for Finland, a folder named [Finnish Regulations](https://github.com/Accord-Project/CODE-ACCORD/tree/main/Finnish%20Regulations) is created. Each data folder hierarchy is structured as follows: Within the main data folder, there are two primary sub-folders. The first sub-folder, *_"PDF"_* contains the original PDF files of the regulations documents. The second sub-folder, *_"Text and CSV"_* is where the text and CSV versions of these PDF files are stored after undergoing various pre-processing stages. This *_"Text and CSV"_* sub-folder consists of eight sub-folders, each corresponding to a specific pre-processing step. They are meticulously organised in sequential order to facilitate systematic data handling. Starting with *_"Raw Text Data_"*, it contains the initial raw text data obtained through PDF-to-text conversion. The subsequent sub-folder, *_"Cleaned Data-Raw Text"_*, holds the cleaned data derived from the previous folder. *_"All Sentences_"* sub-folder contains all sentences extracted from the previous step. Next, *"_AutoFilteredSentences_"* comprises sentences that have been automatically filtered, following the specific criteria described above. *_"ManuallyFilteredSentences"_* contains sentences that were manually curated to ensure consistency and to remove any unnecessary content. The *_"FinalFilteredSentences"_* sub-folder stores the ultimate raw text of the semi-automatically filtered sentences after eliminating empty lines and redundant information. Moving on, *_"CSV-FinalFilteredSentences"_* presents the sentences from the previous folder in csv format, preparing the data for the final sub-folder, *_"Classification"_* which categorises the sentences as either self-contained or categorised under 'others', where only the self-contained sentences will be further considered for this research. This structured hierarchy streamlines the data processing and analysis of regulations documents, ensuring an organised and efficient workflow.

## Data Annotation
Our work is mainly focused on extracting information from text to support rule generation. 
There are two key types of information found in the text: named entities and relations, which are essential for 
comprehending the ideas conveyed in natural language. Hence, our primary focus was on annotating entities and relations.

More details about our annotation strategy with sample annotations are available in [Annotation_Strategy_V1.0.0.pdf](https://github.com/Accord-Project/CODE-ACCORD/blob/main/annotated_data/Annotation_Strategy_V1.0.0.pdf).

All our annotated data are available within [annotated_data](https://github.com/Accord-Project/CODE-ACCORD/tree/main/annotated_data) folder. Within the subfolders entities and relations, 
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
