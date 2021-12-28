---
abstract: |
  As the cost of sequencing is decreasing the number of next generation sequenc- ing studies is increasing at a rapid pace. Staggering amount of sequencing data accumulated over the years are kept at publicly available databases such as Short Read Archive (SRA) and European Nucleotide Archive (ENA). The truly enormous amount of sequencing data provides opportunity for mining gene expression and genome variant studies. However, such a mining task not only requires extensive computational resources but also orchestration of analysis steps at a large scale. The latter challenge is due to the fact that the analysis of sequencing data comprises of multiple steps each carried by different software. If the overall goal can be summarized as ”setting up multiple computers and distributing the workload and processes”, achieving this manually is clearly impractical. However, by the help of various tools and technologies, setting up such an environment is much easier than before. ”Setting up computer” part is taken care by containerization technology in which Docker is the leading platform. ”Multiple computers” part is taken care by cloud services where CPU, RAM and harddisk space can be used with hourly fee. In this talk, Amazon AWS EC2 will be demonstrated. Finally, ”distributing workload and processes” part can be taken care by bioinformatic pipeline frameworks. In this talk, Nextflow [1] framework will be demonstrated which is able use containers and run in cloud. Containerization not only eases the pain of software installation and configura- tion but also supports reproducible research [2]. Combining containerization with cloud computing allows rapid and affordable bioinformatic analysis at scale [3]. Con- tainerization also allows integrative analysis by mixing and matching tools from dif- ferent fields of bioinformatics. This talk will briefly introduce the aforementioned tools and technologies and then provide an example batch analysis where human RNA-Seq data from multiple sequencing projects were used in order to get with preliminary results related to trans-splicing and non-aligned reads.
authors:
- Alper Yilmaz
date: "2018-07-01T00:00:00+03:00"
doi: ""
featured: true
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ""
links:
- name: Custom Link
  url: http://example.org
projects:
- internal-project
publication: In *ICAMLS 2018 International Conference on Applied Mathematics, Modeling and Life Science Problems*
publication_short: ""
publication_types:
- "4"
slides: example
summary: .
tags:
- Source Themes
title: Batch Analyis of RNA-Seq Data with Docker in AWS Cloud
url_code: '#'
url_dataset: '#'
url_pdf: http://eprints.soton.ac.uk/352095/1/Cushen-IMV2013.pdf
url_poster: '#'
url_project: ""
url_slides: ""
url_source: '#'
url_video: '#'
---

{{% callout note %}}
Supplementary notes can be added here, including [code and math](https://sourcethemes.com/academic/docs/writing-markdown-latex/).
{{% /callout %}}
