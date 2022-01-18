---
title: 'Assessment of mutation susceptibility in DNA sequences with word vectors'
date: 2020-03-20
authors: 
  - Alper Yilmaz

publication_types:
  - 2
  
abstract: |
  With the advent of natural language processing (NLP) techniques empowered with deep learning approaches, more detailed relationships between words have been unraveled. Word2Vec is quite robust in discovering contextual and semantic relationships. Genome being a long text, is subject to similar studies to unravel yet to be discovered relationships between DNA k-mers. Dna2vec applies Word2Vec approach to whole genome so that DNA k-mers are represented as vectors. The cosine similarity queries on DNA vectors reveal unusual relationships between DNA k-mers. |
  In this study, we examined DNA sequence based prediction of mutation susceptibility. Initially, we generated word vectors for human and mouse genome via dna2vec. On the other hand, we retrieved coordinates of common and all mutations from dbSNP. For each coordinate, we extracted 8 nucleotide k-mers intersecting mutations and results are aggregated such a way that number of mutations for each 8-mer has been tabulated. These results are incorporated with dna2vec cosine similarity data. Our results showed that for a given k-mer, k-mers with highest cosine similarity coincide with highest mutation count k-mer. In other words, the neighbor with the highest cosine similarity for a k-mer was also seen to be the neighbor overlapping the mutation count. As a result of our studies, human and mouse, dna2vec vs. mutation overlap is 80% and 70%, respectively. In conclusion, dna2vec and other word embedding approaches can be used to reveal mutation or variation characteristics of genomes without sequencing or experimental data, solely using the genome sequence itself. This might pave the way for understanding the underlying mechanism or dynamics of mutations in genomes.
  
featured: false
publication: "*Journal of Intelligent Systems: Theory and Applications*"
tags: 
  - Mutation
  - Word2vec
  - Dna2vec
  - k-mer
  - Cosine-similarity 
url_pdf: "https://dergipark.org.tr/en/pub/jista/article/674910"
doi: 10.38016/jista.674910
---

