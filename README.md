# Computational Pipeline: Understanding a Narrative Structure from a Collection of Topical Images
MLOPs and LLMOPs for dissertation analysis workflow

**Using Multimodal Sentiment Analysis for Knowledge Retrieval in Structured Graphs: Understanding Social Movement Messaging from a Collection of Topical Images**

*Research Question: Can we identify a narrative from a collection of toipical images using computational methods?*
The use of computational methods on real world data to understand narrative messaging of social movements online as a way to monitor the social evolution of how a narrative can change over time, is seen across different mediums. The analysis models the communication messaging system of a social movement on a social media platform by building a narrative structure representative of the local semantics of image groups and an overall global summarization of the narrative structure as a whole.

These quantitative findings are used in conjunction with a theoretical analysis of how the media has framed the anti-feminicide movement in Mexico since the 1990’s, and implements a review of the network’s local and global semantics creating narrative structure for the collection of topical images.


### Implementation

1. Download/clone the repository and save to your desired folder 
2. Create a new virtual environment


## [Data Collection and Evaluation](https://github.com/lwdozal/Dissertation_AI_Workbench/tree/main/data_collection)
- *Data Collection:* A customized image and metadata collector script using Selenium, Beautiful Soup and Python packaged. Collected 19,000+ images and metadata from Instagram. Cleaned and processed data with an output of ~16,000 images and metadata in the collection of topical images.\
- *Data Annotation:* Label Studio to annotate 3,020 images based on labels identified duing visual content analysis of the images.

#### Resources
Instagram Account,
Label Studio,
Selenuim,
Beautiful Soup,
Some HTML knowledge


## [Pattern Detection and Theme Building](https://github.com/lwdozal/Dissertation_AI_Workbench/tree/main/Step1_Pattern_Detection)

### Image Label and Caption Generation
Training and fine-tuning on a subset of data to track performance, identify errors, and optimize models.\
Clean post comments i.e. lemmetize, translate emojies, rename hashtags, lowercase sentences, etc \
Multlingual sentence transformers

#### Image Feature Feature, Cluster Embeddings, Human in the Loop Analysis
**The first step** pulls feature embedding from a collection of 16,657 Instagram images pertaining to the anti-feminicide movement in Mexico; and clusters them to identify common vector embeddings within the data. Compared ResNet50, CLIP, and BLIP-2 embedder; UMAP and HDBSCAN are used for visualization and analysis. A Human-in-the-Loop (HITL) content analysis is applied to provide a qualitative understanding of the images within each cluster and to get insight on the classification aspects of the images for downstream tasks.

Evaluation Metrics: 
- Silhouette Score
- calinski-harabasz index
- davies bouldin index

##### Resources
Hugging Face Access, Access to LLM, GPU Access

### Identify Semantic similarities
Get structured output from prompt engineering and hyperparameter tuning. 

#### M-LLM Image to Text Generation (JSON Output), BERTSCORER and SentenceTransformer Evaluation
**The second step** takes the images and runs them through foundational vision transformer models, along with generative Multimodal Large Language Models (M-LLMs) that generate two labels and a description of each of the images; and are compared and analyzed against each other using multi-label classification metrics along with HITL discourse analysis of the categorization process - M-LLMs include: BLIP-2, Qwen 2.5VL, Llama3, Llama4 Scout, and phi4.

Evaluation Metrics: 
- Acuracy, Precision, Recall, F1-Score, Hamming Loss
- Confusion Matrix (Visuallization)
- BERTScore, Sentence Transformer Cosine Similarities

Ongoing monitoring of security and ethical risks 

##### Resources
Hugging Face Access, Access to large LLMs, GPU Access

<!-- Torch, Torchvision, \
transformers, sentence transformers,  \
PIL, Requests, pydantic, open-cv, os \
langchain core and openai, \ -->


### Network Structure

#### Network Analysis and GNNs
**The third step** uses the top labels created from the model with the best overall quantitative and HITL discourse evaluation metrics to build multiple graphs representing the various stages of semantics found within the image and its attributes. The graph is analyzed to identify structural patterns of the network using traditional centrality measures and modularity models (Leidan algorithm) to understand the semantic connections within and across the network. The overall graph structure is compared to benchmark datasets in a Graph Attention Network (GAT) model that uses a variational autoencoder (VAE) on the graph to compare classifications of the collected annotated image data.

Create Structural graph (content-based knowledge representation) 
- generated label & weights
- generated label & weights + generated captions
- generated label & weights + generated captions & original post comments

Community Detection (Evaluation of Network Structure):
- Centraility Measures
- Modularity: Leidan algorithm

Graph Analysis
- Graphical Attention Network (GAT)
- Variational Autoencoder

##### Resources
Hugging Face Access, Access to large LLMs, GPU Access

