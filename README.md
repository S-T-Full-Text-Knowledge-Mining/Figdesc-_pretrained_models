#  Deep learning-based recognition of figure description sentences in academic full-text

## Introduction

Within the realm of academic full-texts and employing deep learning techniques, this research primarily tackles the following three issues. 
* Firstly, in the rapidly evolving field of multimodal research, constructing datasets of figures and their corresponding descriptive sentences not only determines the overall performance of multimodal large language models but also plays a significant role in advancing the study of intelligent systems within the multimodal domain. In the context of academic full-texts, a large-scale dataset of academic images and descriptive sentences is still lacking. The construction of such a dataset is an issue that this research aims to investigate. 

* Secondly, in the context of the burgeoning deep learning technology, the integration of this advanced approach into academic full-text informetrics, knowledge discovery, and information retrieval is of paramount importance for augmenting the overall efficacy of academic full-text research. A fundamental research question in this research pertains to the potential disparities in the performance of sequential deep learning algorithms and pre-trained models concerning figure description sentence recognition. 

* Finally, distinct from the investigation of pure model performance, a critical aspect of applied research is the application of the constructed models to specific research questions. In the context of this study, this entails examining the performance of the models in recognizing image description sentences within authentic domain-specific academic full-texts.

## Datasets

### Journal screening
The data for this research were collected from 8,481 annotated academic papers published in six international journals in the domain of library and information between 2010 and 2022. There were 446 articles from the Journal of the Association for Information Science and Technology (JASIST), 547 articles from SAGE, 550 articles from Journal of Enterprise Information Management (JEIM), 1033 articles from Journal of Knowledge Management (JKM), 1,815 articles from Qualitative Health Research (QHR), and Scientometrics has 4,090 articles. 

|Journal name|Number of papers|Number of figures|
|:--:|:--:|:--:|
|JASIST|446|1,000|
|Journal of Enterprise Information Management|550|1,522|
|Journal of Knowledge Management|1,033|2,391|
|Qualitative Health Research|1,815|1,275|
|SAGE|547|1,196|
|Scientometrics|4,090|18,397|
|ALL|8,481|25,781|

### Sentence acquisition and annotation

In the data processing part of this reserach, the construction process of corpus will be introduced respectively. The <FD>content</FD> symbol is used to mark the semantic description sentences of the figure in the annotation process. 

* Firstly, on the six identified journals, a special web crawler is designed to obtain the academic full-text content of the six journals. The work of data cleaning and processing is completed, such as removing garbled characters, cleaning non-standard descriptions and converting formats. 
* Secondly, The position of the figure is mainly located through Fig., and the position of the text describing the Fig. is determined based on the position of the figure. 
* Finally, the sentences are manually evaluated which might describe the figures, and the confirmed figure description sentences are labelled with <FD>content</FD>.
 * A total of 859,221 sentences are included in the figure descriptive text corpora.

##  How to use

### Huggingface Transformers 

The `from_pretrained` method based on [Huggingface Transformers](https://github.com/huggingface/transformers) can directly obtain SSCI-BERT and SSCI-SciBERT models online. 



- SSCI-BERT

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained("KM4STfulltext/SSCI-BERT-e2")

model = AutoModel.from_pretrained("KM4STfulltext/SSCI-BERT-e2")
```

- SSCI-SciBERT

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained("KM4STfulltext/SSCI-SciBERT-e2")

model = AutoModel.from_pretrained("KM4STfulltext/SSCI-SciBERT-e2")
```


3. Datasets for Identifying Abstract Structures 

SSCI journal abstracts published between 2008 and 2020 obtained a total of 1378276 construction notes according to the functional structure of the sentence-by-sentence annotation abstracts in the five categories of background, purpose, methodology, results and conclusions (BPMRC).

4. Datasets for Software Entities Recognition in Scientometrics 

Using full-text data published in Scientometrics from 2010 to 2020, software entities in the dataset were manually annotated, and a total of 13,269 software entities were identified.
> dataset examples can be find in 'datasets/examples'
> if you want all datasets for researches, please email us and we will provide for free.()
### Download Models

- The version of the model we provide is `PyTorch`. 

### From Huggingface 

- Download directly through Huggingface's official website. 
- [KM4STfulltext/SSCI-BERT-e2](https://huggingface.co/KM4STfulltext/SSCI-BERT-e2)
-  [KM4STfulltext/SSCI-SciBERT-e2](https://huggingface.co/KM4STfulltext/SSCI-SciBERT-e2)
- [KM4STfulltext/SSCI-BERT-e4 ](https://huggingface.co/KM4STfulltext/SSCI-BERT-e4)
- [KM4STfulltext/SSCI-SciBERT-e4](https://huggingface.co/KM4STfulltext/SSCI-SciBERT-e4)

### From Google Drive

We have put the model on Google Drive for users. 

| Model                                                        | DATASET(year) | Base Model             |
| ------------------------------------------------------------ | ------------- | ---------------------- |
| [SSCI-BERT-e2](https://drive.google.com/drive/folders/1xEDnovlwGO2JxqCaf3rdjS2cB6DOxhj4?usp=sharing) | 1986-2021     | Bert-base-cased        |
| [SSCI-SciBERT-e2](https://drive.google.com/drive/folders/16DtIvnHvbrR_92MwgthRRsULW6An9te1?usp=sharing) (recommended) | 1986-2021     | Scibert-scivocab-cased |
| [SSCI-BERT-e4](https://drive.google.com/drive/folders/1sr6Av8p904Jrjps37g7E8aj4HnAHXSxW?usp=sharing) | 1986-2021     | Bert-base-cased        |
| [SSCI-SciBERT-e4](https://drive.google.com/drive/folders/1ty-b4TIFu8FbilgC4VcI7Bgn_O5MDMVe?usp=sharing) | 1986-2021     | Scibert-scivocab-cased |

##  Evaluation & Results

- We use SSCI-BERT and SSCI-SciBERT to perform Text Classificationon different social science research corpus. The experimental results are as follows. Relevant data sets are available for download in the  **Verification task datasets** folder of this project.

#### JCR Title Classify Dataset

| Model                  | accuracy | macro avg | weighted avg |
| ---------------------- | -------- | --------- | ------------ |
| Bert-base-cased        | 28.43    | 22.06     | 21.86        |
| Scibert-scivocab-cased | 38.48    | 33.89     | 33.92        |
| SSCI-BERT-e2           | 40.43    | 35.37     | 35.33        |
| SSCI-SciBERT-e2        | 41.35    | 37.27     | 37.25        |
| SSCI-BERT-e4           | 40.65    | 35.49     | 35.40        |
| SSCI-SciBERT-e4        | 41.13    | 36.96     | 36.94        |
| Support                | 2300     | 2300      | 2300         |

#### JCR Abstract Classify Dataset

| Model                  | accuracy | macro avg | weighted avg |
| ---------------------- | -------- | --------- | ------------ |
| Bert-base-cased        | 48.59    | 42.8      | 42.82        |
| Scibert-scivocab-cased | 55.59    | 51.4      | 51.81        |
| SSCI-BERT-e2           | 58.05    | 53.31     | 53.73        |
| SSCI-SciBERT-e2        | 59.95    | 56.51     | 57.12        |
| SSCI-BERT-e4           | 59.00    | 54.97     | 55.59        |
| SSCI-SciBERT-e4        | 60.00    | 56.38     | 56.90        |
| Support                | 2200     | 2200      | 2200         |

#### JCR Mixed Titles and Abstracts Dataset

| **Model**              | **accuracy** | **macro  avg** | **weighted  avg** |
| ---------------------- | ------------ | -------------- | ----------------- |
| Bert-base-cased        | 58.24        | 57.27          | 57.25             |
| Scibert-scivocab-cased | 59.58        | 58.65          | 58.68             |
| SSCI-BERT-e2           | 60.89        | 60.24          | 60.30             |
| SSCI-SciBERT-e2        | 60.96        | 60.54          | 60.51             |
| SSCI-BERT-e4           | 61.00        | 60.48          | 60.43             |
| SSCI-SciBERT-e4        | 61.24        | 60.71          | 60.75             |
| Support                | 4500         | 4500           | 4500              |

#### SSCI Abstract Structural Function Recognition (Classify Dataset)

|              | Bert-base-cased            | SSCI-BERT-e2        | SSCI-BERT-e4        | support     |
| ------------ | -------------------------- | ------------------- | ------------------- | ----------- |
| B            | 63.77                      | 64.29               | 64.63               | 224         |
| P            | 53.66                      | 57.14               | 57.99               | 95          |
| M            | 87.63                      | 88.43               | 89.06               | 323         |
| R            | 86.81                      | 88.28               | **88.47**           | 419         |
| C            | 78.32                      | 79.82               | 78.95               | 316         |
| accuracy     | 79.59                      | 80.9                | 80.97               | 1377        |
| macro avg    | 74.04                      | 75.59               | 75.82               | 1377        |
| weighted avg | 79.02                      | 80.32               | 80.44               | 1377        |
|              | **Scibert-scivocab-cased** | **SSCI-SciBERT-e2** | **SSCI-SciBERT-e4** | **support** |
| B            | 69.98                      | **70.95**           | **70.95**           | 224         |
| P            | 58.89                      | **60.12**           | 58.96               | 95          |
| M            | 89.37                      | **90.12**           | 88.11               | 323         |
| R            | 87.66                      | 88.07               | 87.44               | 419         |
| C            | 80.7                       | 82.61               | **82.94**           | 316         |
| accuracy     | 81.63                      | **82.72**           | 82.06               | 1377        |
| macro avg    | 77.32                      | **78.37**           | 77.68               | 1377        |
| weighted avg | 81.6                       | **82.58**           | 81.92               | 1377        |

## Cited

- If our content is helpful for your research work, please quote our research in your article. 
- If you want to quote our research, [https://link.springer.com/article/10.1007/s11192-022-04602-4](https://link.springer.com/article/10.1007/s11192-022-04602-4)

## Disclaimer

- The experimental results presented in the report only show the performance under a specific data set and hyperparameter combination, and cannot represent the essence of each model. The experimental results may change due to random number seeds and computing equipment. 
- **Users can use the model arbitrarily within the scope of the license, but we are not responsible for the direct or indirect losses caused by using the content of the project.** 


##  Acknowledgment

- SSCI-BERT was trained based on [BERT-Base-Cased]([google-research/bert: TensorFlow code and pre-trained models for BERT (github.com)](https://github.com/google-research/bert)).
- SSCI-SciBERT was trained based on [scibert-scivocab-cased]([allenai/scibert: A BERT model for scientific text. (github.com)](https://github.com/allenai/scibert))

