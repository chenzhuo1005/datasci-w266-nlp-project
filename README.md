# DATASCI 266 NLP Project

## Introduction
This project explores the impact of retrieval-augmented generation on the performance of large language models (LLMs) in Open Domain Question Answering (ODQA). Our approach incorporates an external knowledge augmentation system using the PAQ dataset, which provides LLMs like Flan-T5 and Llama-2-13B with real-time access to over 1.4 million question-answer pairs. This system allows dynamic retrieval of pertinent information, addressing the inherent limitations of LLMs related to fixed knowledge bases and context length constraints. We assess the enhancement in accuracy with metrics such as Exact Match (EM), F1, and Rouge scores. Our findings show that retrieval-augmented techniques notably enhance the quality of answers across various LLMs (e.g., an increase from 8.45 to 35.48 EM on Flan-T5-large), underscoring the potential of integrating these systems to augment the capabilities and applicability of traditional neural language models in complex question-answering tasks.

## Research Paper

The research paper associated with this project, titled "Retrieval-Augmented Generation for Enhancing Open-Domain Question Answering Systems with External Knowledge," is available in two formats: the LaTeX source version and the compiled PDF version. 

- **LaTeX Source**: The LaTeX source files for the paper can be found in the `./paper/overleaf` [overleaf](./paper/overleaf)

- **PDF Version**: For convenience, a compiled PDF version of the paper is also available. It can be accessed directly at `./paper/datasci_266_project_zhuochen.pdf` [datasci 266 project](./paper/datasci_266_project_zhuochen.pdf)


## Datasets
### RAG Knowledge Source: PAQ-L1
The primary dataset used as a knowledge source in our retrieval-augmented generation system is PAQ-L1, which consists of over 1.4 million automatically generated question-answer pairs. It is designed to provide a comprehensive and diverse set of data points to support and enhance the retrieval capabilities of our models.

- **Access the dataset**: [PAQ Dataset](https://github.com/facebookresearch/PAQ) [PAQ-L1 Dataset Download](https://dl.fbaipublicfiles.com/paq/v1/PAQ_L1.tar.gz)
- **Preprocessing Steps**: Before integration, the dataset undergoes cleaning to remove any duplicates and formatting errors. The data is then indexed using an efficient search algorithm to facilitate rapid retrieval during the question-answering process.

### Validation Dataset: NQ-Open
The NQ-Open dataset is utilized for validating the model's performance. It consists of questions derived from the Natural Questions dataset, providing a realistic benchmark for open-domain question answering.

- **View the dataset**: [NQ-Open Validation Data](https://huggingface.co/datasets/nq_open/viewer/nq_open/validation)
- **Integration**: This dataset is employed to evaluate the accuracy and effectiveness of our models, particularly focusing on the Exact Match (EM) and F1 metrics. The questions from NQ-Open are posed to our models to assess their ability to retrieve and generate accurate answers based on the external knowledge augmented from the PAQ-L1 dataset.

## Notebooks

The `./notebooks` directory contains a collection of Jupyter notebooks that are integral to the project. These notebooks contain detailed codes and visualizations for knowledge building, various experiments conducted, and the analysis of the results.

All notebooks are fully annotated to ensure clarity and ease of understanding, enabling others to replicate the experiments or build upon the work done in this project.

You can explore these notebooks by navigating to the [notebooks](./notebooks)

## Evaluation

The evaluation of the models is performed using a set of metrics that are critical for assessing the effectiveness of question answering systems. These metrics include Exact Match (EM), F1, and several Rouge metrics (Rouge1, Rouge2, RougeL, RougeLSum).

- **Location of Evaluation Files**: [eval](./eval)
- **Data Description**: The evaluation directory contains CSV files with the predicted answers generated by different LLM configurations, both with and without the retrieval-augmented generation feature.

### Evaluation Metrics
The following table encapsulates the performance metrics for the evaluated models:

| Model                     | EM    | F1    | Rouge1 | Rouge2 | RougeL | RougeLSum |
|---------------------------|-------|-------|--------|--------|--------|-----------|
| flan-t5-base              | 4.52  | 7.84  | 5.78   | 0.99   | 5.78   | 5.78      |
| flan-t5-base+RAG          | 27.59 | 32.27 | 24.65  | 12.90  | 24.61  | 24.59     |
| flan-t5-large             | 8.45  | 12.63 | 9.72   | 3.31   | 9.72   | 9.70      |
| flan-t5-large+RAG         | 35.48 | 39.95 | 30.48  | 17.06  | 30.50  | 30.49     |
| llama-2-13B-chat-GGUF     | 35.96 | 40.16 | 30.4   | 14.9   | 30.22  | 30.23     |
| llama-2-13B-chat-GGUF+RAG | 37.62 | 40.73 | 30.97  | 17.22  | 30.95  | 30.94     |
| gpt-3.5-turbo-0125        | 34.07 | 39.02 | 30.99  | 18.07  | 30.82  | 30.8      |
| gpt-3.5-turbo-0125+RAG    | 37.89 | 42.64 | 33.01  | 18.35  | 32.91  | 32.91     |

Our experimental results indicate a clear improvement when RAG is applied, which is consistent across all the evaluated models, thereby affirming the advantages of retrieval-augmented strategies for enhancing LLM performance in ODQA tasks.
