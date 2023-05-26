# Paper Recommender System

An application that recommends you a paper to read based on a text prompt

## Experiment Logs and Motivation

Consider this a humble foray into building in public, here's what I want to do, and what I've done so far.

### Data

The dataset I have the [arXiv Paper Abstracts](https://www.kaggle.com/datasets/spsayakpaul/arxiv-paper-abstracts) hosted on Kaggle, it's not the official [arXiv Dataset](https://www.kaggle.com/datasets/Cornell-University/arxiv), which I discovered exists recently, the dataset I'm using is miniscule at around 56k paper abstracts, but it's a start. I'm using this dataset because it's a lot smaller and I can train a model on my laptop, the official dataset is 1.7 million papers, and I don't have the resources to train a model on that (YET).

### Preprocessing

My humble contribution was going to be embedding a text string that contains a detailed description of the tags, from the dataset, I evaluated terms column using Python's ast standard library which resulted in 780 unique tags, digging deeper, I divided them into MSC, ACM and arXiv classifications, I used some basic web scraping to get the descriptions, I found older versions of the ACM and MSC classification descriptions on The Comprehensive R Archive Network as well as wikidata, god bless whoever is maintaining these, but I chose the hard way because of course,
so I got the PDF for the 2020 version of the MSC classification system and parsed it using the [unstructured](https://github.com/Unstructured-IO/unstructured) library, I also ran a failed experiment using langchain to fetch the text descriptions of the tags.

### Model

Current plan for embeddings is sentence-transformers from HuggingFace

### Vector Search

I'm looking into Chroma, weviate, pinecone and pgvector to host my text embeddings.
