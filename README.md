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

The `from_pretrained` method based on [Huggingface Transformers](https://github.com/huggingface/transformers) can directly obtain Journal_BERT serise models and Journal-GPT model online. 


- Jour_BERT

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
- [KM4STfulltext/Journal-BERT](https://huggingface.co/KM4STfulltext/Journal-BERT)
- [KM4STfulltext/Journal-RoBERTa](https://huggingface.co/KM4STfulltext/Journal-Roberta)
- [KM4STfulltext/Journal-SCIBERT](https://huggingface.co/KM4STfulltext/Journal-SCIBERT)
- [KM4STfulltext/Journal-SSCIBERT](https://huggingface.co/KM4STfulltext/Journal-SSCIBERT)
- [KM4STfulltext/Journal-GPT](https://huggingface.co/KM4STfulltext/Journal-GPT)


## Cited

- If our content is helpful for your research work, please quote our research in your article. 
- This study has not yet been published, if you want to quote our research,, you can use this website to make a reference 

## Disclaimer

- The experimental results presented in the report only show the performance under a specific data set and hyperparameter combination, and cannot represent the essence of each model. The experimental results may change due to random number seeds and computing equipment. 
- **Users can use the model arbitrarily within the scope of the license, but we are not responsible for the direct or indirect losses caused by using the content of the project.** 


##  Acknowledgment

- Journal-BERT was trained based on [BERT-Base-Cased]([google-research/bert: TensorFlow code and pre-trained models for BERT (github.com)](https://github.com/google-research/bert)).
- Journal-RoBERTa was trained based on [RoBERTa]([google-research/bert: TensorFlow code and pre-trained models for BERT (github.com)](https://github.com/google-research/bert)).
- Journal-SCIBERT was trained based on [scibert-scivocab-cased]([google-research/bert: TensorFlow code and pre-trained models for BERT (github.com)](https://github.com/google-research/bert)).

- Journal-SSCIBERT was trained based on [SSCIBERT]([SsciBERT: A pretrained language model for social scientific textl for social scientific text. (github.com)](https://github.com/S-T-Full-Text-Knowledge-Mining/SSCI-BERT))

