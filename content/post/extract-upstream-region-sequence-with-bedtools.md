---
title: "Extract upstream region sequence with bedtools"
date: 2011-03-06T08:40:36+00:00
tags:
  - bioinformatics
  - one-liner
  - perl
---

Soon after SAM/BAM format became standard for short-read alignment softwares, high caliber tools have been emerging that can process the widely accepted format. [bedtools](http://code.google.com/p/bedtools/) is one of them and it's easy to use and flexible. Most importantly you can integrate it with commandline pipes.

In this post, I'll be describing how to extract upstream region sequences with the help of bedtools. I'll be using the following files in my sample:

File1: small-chr-genes.bed (holds locations of genes)

```txt
1	10	20	gene1	0	+
1	40	50	gene2	0	-
```

File2: small-chr.fa (genome sequence file)

```txt
>1
GCGACTACGACTACAGCACTACGACATCAGCACTACGACT
ACGACTACGACATCACGACACACGACGACATCACGACTAC
```

File3: small-chr.genome (genome file which contains name and length of each chromosome)

```txt
1	80
```

The one-liner below extracts 5 basepairs upstream region for each gene and slopBed takes care of strand issues (reverse complement of extracted sequence if gene is on negative strand) and genome size issues (trim the extracted sequence if gene is close to beginning or end of chromosome).

```bash
slopBed -i small-chr-genes.bed -g small-chr.genome -l 5 -r 0 -s | perl -ane '($F[5] eq "+")? $F[2]=$F[1] : $F[1]=$F[2]; print join"\t",@F;print"\n"'  | slopBed -i stdin -g small-chr.genome -l 0 -r 5 -s | fastaFromBed -fi small-chr.fa -bed stdin -fo stdout -name -s
```

The output looks like this:

```txt
>gene1
TACGA
>gene2
TGATG
```

Let me try to explain how it works, first I extend each gene 5 basepair to its upstream. Then I mark the beginning of the extended region by converting it into single nucleotide region. I use slopBed again, to extend from the mark in opposite direction for 5 basepairs. Now we have the upstream region start and end coordinates, and by the help of fastaFromBed, the upstream region sequence was extracted from genome sequence.

bedtools has a tool named subtractBed and I was thinking that combination of slopBed, subtractBed and fastaFromBed should be the solution. However, probably due to genes that are overlapping, subtracting gene region from extended region didn't work as well as I expected. That's why I integrated a perl one-liner to take care of subtracting the gene region from extended region.

**Update** : bedtools developer [Aaron Quinlan](http://obx.cphg.virginia.edu/quinlan/) was kind enough to develop a new tool to accomplish the task described above. "flankBed" does exactly what is described above and it's much simpler. Here's the flankBed equivalent of extracting upstream regions:

```bash
flankBed -i small-chr-genes.bed -g small-chr.genome -l 5 -r 0 -s | fastaFromBed -fi small-chr.fa -bed stdin -fo stdout -name -s
```
