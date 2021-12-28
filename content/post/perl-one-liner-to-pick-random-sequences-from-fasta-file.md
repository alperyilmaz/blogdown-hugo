---
title: "perl one-liner to pick random sequences from fasta file"
date: 2010-07-15T08:03:53+00:00
tags:
  - bioinformatics
  - one-liner
  - perl
---
In an earlier [post]({{ ref "post/perl-one-liner-to-process-sequence-files-in-stream.md" }}) we learned how to use Bio::SeqIO module to process fasta files with one-liner. Let's do more with this capability. What about selecting random sequences from a fasta file?

To achieve that, we'll load the fasta file contents into a hash and then utilize the fact that `rand(@array)` returns index of a random element from that array.

Let's pick 100 random sequences from a fasta file with one-liner:

```bash
.. fasta file stream .. | perl -MBio::SeqIO -e '$seq=Bio::SeqIO->new(-fh => \*STDIN);while ($myseq=$seq->next_seq){ $hash{$myseq->id}=$myseq->seq }; END{@ids = keys %hash; foreach (1..100){my $index=rand(@ids); print ">",$ids[$index],"\n",$hash{$ids[$index]},"\n" } }'
```

**UPDATE**: If this one-liner throws problem about first sequence, please indicate the format of the input. Since read ahead is not possible in a pipe, the format might not be guessed correctly. So, please update the one-liner with this: `$seq=Bio::SeqIO->new(-fh => \*STDIN, -format=>"fasta")`