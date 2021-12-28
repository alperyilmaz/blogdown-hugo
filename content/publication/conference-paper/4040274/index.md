---
abstract: | 
K-mer frequency of any DNA sequence is calculated by counting occurrences of all
possible substrings of length k. The k-mer frequency of genome or next generation
sequencing data is an invaluable tool to gain insights about the DNA sequence and
its grammar. For genomes, k-mer counts can be used for motif discovery,
classification and alignment-free comparison of multiple genomes. For short reads,
k-mer counts are used for quality check, diagnosis, error correction and assembly.
The initial step k-mer counting requires storage of frequency tables which tend to get
bigger by increasing length of k. In this study we propose a method for lossless
compression of k-mer data which is expected to simplify and facilitate storage and
analysis of k-mer data. In a raster image, such as PNG, each pixel has two
components; coordinate and color. We implemented Chaos Game Representation
(CGR) to map k-mers to coordinates and k-mer occurrence was mapped to RGB color
via bit-level operations. CGR maps can be divided and labeled according to the
corresponding substring, each substring is mapped onto a sub-square, creating a
fractal-like structure. Basically, the whole set of frequencies of the k-mers found in
each genomic sequence are displayed in the form of a single image in which each
pixel is associated with a specific k-mer and its occurrence. As result, file size has
been reduced by approximately 10 times compared to plain text and reduced 5 times
compared to binary storage (Jellyfish). Storage of k-mer data as image will not only
save storage space but also facilitate genomic analysis in a manner previously not
implemented. Image related algorithms can be used to process, analyze and
manipulate collection of images representing genomic or next-generation sequencing
data k-mer signatures.

authors:
- Hatice Busra Konuk
- Alper Yilmaz
date: "2017-07-01T00:00:00+03:00"
doi: 
featured: false
image:
  caption: 
  focal_point: 
links:
- name: 
  url: 
projects:
- genome-grammar
publication: In *International Congress on Advances in Bioscience and Biotechnology*
publication_short: 
publication_types:
- "1"
slides: 
summary: 
tags:
  - K-mer
  - Fractal
  - Genome
title: Generating Lossless Compression Of Genome Scale K-Mer Frequency Table As Raster Image
url_code: 
url_dataset: 
url_pdf: https://www.icabb.eu/sites/default/files/icabb_2017_book_of_abstracts_v3.pdf
url_poster: 
url_project: 
url_slides: 
url_source: 
url_video: 
---
