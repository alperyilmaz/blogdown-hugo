---
title: "Top ten occurrences with perl one-liner"
date: 2010-03-30T13:56:19+00:00
tags:
  - one-liner
  - perl
---
Very nice perl one-liner using map, sort and array range to show top ten occurrences

Taken from [Tech@Sakana blog](http://www.sakana.fr/blog/2010/03/02/perl-counting-occurences-of-ip-addresses-in-apache-logs/)

```bash
perl -ane '$c{$F[0]}++; END {print map {$_ . "\t->\t" . $c{$_} . "\n"} (sort {$c{$b} <=> $c{$a}} keys %c)[0..9]}' filename
```

Same thing can be achieved by:

```bash
sort filename | uniq -c | sort -nr | head
```

But the perl one-liner demonstrates the nice combination of sort and map.