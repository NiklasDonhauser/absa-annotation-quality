# ABSA Annotation Quality

<div align="center">

**Annotation Quality in Aspect-Based Sentiment Analysis: 
A Case Study Comparing Experts, Students, Crowdworkers, and Large Language Models**

Accepted at the Workshop **RESOURCEFUL-2026** (Co-located with LREC 2026) · Palma, Mallorca (Spain)

[![Paper](https://img.shields.io/badge/Paper_Download-RESOURCEFUL%202026-blue?style=for-the-badge&logo=googlescholar)](TBA)
[![Correspondence](https://img.shields.io/badge/Contact-Niklas%20Donhauser-darkred?style=for-the-badge&logo=minutemailer)](mailto:niklas.donhauser@ur.de)

---

**Niklas Donhauser¹* · Jakob Fehle¹ · Nils Constantin Hellwig¹ · Markus Weinberger¹ ·  Udo Kruschwitz² · Christian Wolff¹*

¹Media Informatics Group, University of Regensburg, Germany  
²Information Science Group, University of Regensburg, Germany

*✉ Correspondence to: [niklas.donhauser@ur.de](mailto:niklas.donhauser@ur.de)*  
`{niklas.donhauser, jakob.fehle, nils-constantin.hellwig, markus.weinberger, udo.kruschwitz, christian.wolff}@ur.de`
</div>

--- 
## Abstract
Aspect-Based Sentiment Analysis (ABSA) enables fine-grained opinion analysis by identifying sentiments toward specific aspects or targets within a text.
While ABSA has been widely studied for English, research on other languages such as German remains limited, largely due to the lack of high-quality annotated datasets.
This paper examines how different annotation sources influence the development of German ABSA. 
To this end, an existing dataset is re-annotated by experts to establish a ground truth, which serves as a reference for evaluating annotations produced by students, crowdworkers, Large Language Models (LLMs), and experts. 
Annotation quality is compared using Inter-Annotator Agreement (IAA) and its impact on downstream model performance for different ABSA subtasks.
The evaluation focuses on Aspect Category Sentiment Analysis (ACSA) and Target Aspect Sentiment Detection (TASD). 
We apply State-of-the-Art (SOTA) methods for ABSA, including BERT-, T5-, and LLaMA-based approaches to assess performance differences, spanning fine-tuning and in-context learning with instruction prompts. 
The findings provide practical insights into trade-offs between annotation reliability, and efficiency, offering guidance for dataset construction in under-resourced Natural Language Processing (NLP) scenarios.

<hr>

## Results:
### Aspect Category Sentiment Analysis (ACSA)

| **Dataset / Method** | **Crowd Micro** | **Crowd Macro** | **Students Micro** | **Students Macro** | **LLMs Micro** | **LLMs Macro** | **Experts Micro** | **Experts Macro** |
|-----------------------|-----------------|-----------------|---------------------|---------------------|----------------|----------------|-------------------|-------------------|
| **BERT-CLF**         | 76.99           | 74.04           | 77.81               | 74.75               | 77.44          | 74.65          | **78.26**         | 75.17             |
| **Hier-GCN**         | 79.66           | 77.28           | 78.97               | 77.53               | 79.13          | 77.17          | **79.78**         | 78.13             |
| **Gemma FS**         | 86.03           | 84.63           | **86.43**           | 84.50               | 85.60          | 83.83          | 86.29             | 84.62             |
| **LLaMA FT**         | 85.64           | 83.46           | 85.71               | 84.33               | 84.85          | 82.02          | **86.39**         | 83.12             |

*Table: Micro- and Macro-F1 scores for ACSA, averaged over five seeds across datasets. Highest values are shown in bold.*


### Target Aspect Sentiment Detection (TASD)

| **Dataset / Method** | **Crowd Micro** | **Crowd Macro** | **Students Micro** | **Students Macro** | **LLMs Micro** | **LLMs Macro** | **Experts Micro** | **Experts Macro** |
|-----------------------|-----------------|-----------------|---------------------|---------------------|----------------|----------------|-------------------|-------------------|
| **Paraphrase**        | 52.77           | 47.97           | 57.33               | 52.10               | 57.37          | 53.06          | **61.65**         | 56.24             |
| **MvP**               | 51.29           | 50.58           | 56.83               | 55.89               | 60.65          | 56.95          | **64.01**         | 59.42             |
| **Gemma FS**          | 58.56           | 56.41           | 62.28               | 59.06               | **65.58**      | **62.30**      | 63.38             | 58.74             |
| **LLaMA FT**          | 65.46           | 60.97           | 69.33               | 65.50               | 66.24          | 63.20          | **71.47**         | **67.40**         |

*Table: Micro- and Macro-F1 scores for TASD, averaged over five seeds across datasets. Bold indicates the highest values.*

<hr>

## Repository Structure  

- **01_Code**  
  Source code for model implementations, dataset generation, preprocessing, and evaluation.  

- **02_Datasets**  
  All created datasets and the individual annotations from participants and models.  

- **03_Annotations**  
  Annotation guidelines, interface materials, and instructional videos used in the annotation studies.  

- **04_Results**  
  Outputs of this work, including model evaluation results and inter-annotator agreement scores.  
 

> **Note:** Folder **03_Datasets** (except for a small dummy.jsonl file) remain empty because their contents cannot be distributed publicly for licensing reasons.
<hr>

## Related Work 

- BERT-CLF: Fehle, J., Münster, L., Schmidt, T., & Wolff, C. (2023). *Aspect-based sentiment analysis as a multi-label classification task on the domain of German hotel reviews.* KONVENS 2023. [PDF](https://aclanthology.org/2023.konvens-main.21.pdf)  

- Hier-GCN: Cai, H., Tu, Y., Zhou, X., Yu, J., & Xia, R. (2020). *Aspect-category based sentiment analysis with hierarchical graph convolutional network.* COLING 2020. [PDF](https://aclanthology.org/2020.coling-main.72/)

- MvP: Gou, Z., Guo, Q., & Yang, Y. (2023). *MvP: Multi-view Prompting Improves Aspect Sentiment Tuple Prediction.* ACL 2023. [DOI](https://doi.org/10.18653/v1/2023.acl-long.240)  

- Paraphrase: Zhang, W., Deng, Y., Li, X., Yuan, Y., Bing, L., & Lam, W. (2021). *Aspect sentiment quad prediction as paraphrase generation.* arXiv:2110.00796. [DOI](https://doi.org/10.48550/arXiv.2110.00796)  

- LLM-FT: Šmíd, J., Přibáň, P., & Král, P. (2025). *LLaMA-based models for aspect-based sentiment analysis.* arXiv:2508.08649. [PDF](https://aclanthology.org/2024.wassa-1.6/)

- LLM-FS: Simmering, P. F., & Huoviala, P. (2023). *Large language models for aspect-based sentiment analysis.* arXiv:2310.18025. [PDF](https://arxiv.org/abs/2310.18025)  

- GERestaurant: Hellwig, N. C., Fehle, J., Bink, M., & Wolff, C. (2024, September). GERestaurant: A German Dataset of Annotated Restaurant Reviews for Aspect-Based Sentiment Analysis. In Proceedings of the 20th Conference on Natural Language Processing (KONVENS 2024) (pp. 123–133). [PDF](https://doi.org/10.48550/arXiv.2408.07955)

- LLM Dataset Generation: Hellwig, N. C., Fehle, J., Kruschwitz, U., & Wolff, C. (2025, May). Do we still need human annotators? Prompting large language models for aspect sentiment quad prediction. arXiv. [PDF](https://doi.org/10.48550/arXiv.2502.13044)

- Model Parameters: Fehle, J., Donhauser, N., Kruschwitz, U., Hellwig, N. C., & Wolff, C. (2025, September). German Aspect-based Sentiment Analysis in the Wild: B2B Dataset Creation and Cross-Domain Evaluation. In 21st Conference on Natural Language Processing (KONVENS 2025)(Vol. 9, p. 213). [PDF](https://aclanthology.org/2025.konvens-1.19.pdf)

<hr>
 
## Citation  

If you use our work, please cite our paper and link this repository:  
*Citation available after 2026-05-11*
