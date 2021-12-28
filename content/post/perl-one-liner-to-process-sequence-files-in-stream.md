---
title: "perl one-liner to process sequence files in stream"
date: 2010-04-01T02:43:57+00:00
tags:
  - bioinformatics
  - one-liner
  - perl
---
Need a practical way to process fasta files with Bio::SeqIO module ? Below code will print sequence id and sequence length with tab per line.

```bash
perl -MBio::SeqIO -e '$seq=Bio::SeqIO->new(-fh => \*STDIN);while ($myseq=$seq->next_seq){print $myseq->id,"\t",$myseq->length,"\n";}' < filename 
```

**OR**

```bash
cat filename | perl -MBio::SeqIO -e '$seq=Bio::SeqIO->new(-fh => \*STDIN);while ($myseq=$seq->next_seq){print $myseq->id,"\t",$myseq->length,"\n";}'
```

There are many more methods to use from [Bio::Seq](http://doc.bioperl.org/releases/bioperl-current/bioperl-live/Bio/Seq.html), such as revcom, translate, subseq(start,end), primary_id, desc, etc.

Piped file does not need to be in Fasta format, there are many other formats (listed [here](http://www.bioperl.org/wiki/HOWTO:SeqIO)) which SeqIO can parse successfully.

> *UPDATE*: If you are using this one-liner in a pipe, you might need to declare the format so that the stream is processed correctly. Also, in order to retrieve Bio::Seq methods, please use "->seq" to access the final sequence.
>
> Considering all these updates, the one-liner should look like this:

```bash
perl -MBio::SeqIO -e '$seq=Bio::SeqIO->new(-fh => \*STDIN,-format=>"fasta");while ($myseq=$seq->next_seq){print $myseq->id,"\t",$myseq->length,"\t",$myseq->seq,"\t",$myseq->translate->seq,"\n";}'
```