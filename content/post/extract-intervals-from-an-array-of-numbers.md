+++
title = "Extract intervals from an array of numbers"
date = 2011-06-27T06:58:02+00:00
tags = ["commandline","one-liner","perl"]
+++

Let's assume you have an array of numbers and you want to extract intervals from this array. For example, from such an array: 2,3,4,5,8,9,10,11,12,15,18,19,20 you should be getting (2-5), (8-12), (18-20) as intervals.

More bioinformatic case: Let's assume you ran samtools pileup format and want to extract intervals from the genomic coordinates that has at least one hit.

<!--more-->

The following one-liner will give you what you want: (I used `seq` to generate array of numbers and concatenated multiple seq)

```bash
cat <(seq 3 23) <(echo 25) <(seq 40 50) | perl -ne 'BEGIN{our $i=1}; chomp ; if(($_ - (${$hash->{$i-1}}[-1]))==1){push @{$hash->{$i-1}},$_}else{push @{$hash->{$i++}},$_}; END {print join"\n", map {${$hash->{$_}}[0]."\t".${$hash->{$_}}[-1]} grep { scalar(@{$hash->{$_}}) > 1} sort {$a <=> $b} keys %$hash; print "\n"}'
```

And the result is:

```txt
3	23
40	50
```

`map` was used to get first and last element of array, `grep` is used to filter out arrays that has less than 2 elements.
