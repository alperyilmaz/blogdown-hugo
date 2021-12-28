---
title: "One line statistics"
date: 2010-04-02T13:05:52+00:00
tags:
  - one-liner
  - perl
---
Let's assume we have a file with five columns where first column is text and rest of the columns are numeric. How can we calculate the standard deviation (or other statistical functions) with a perl one-liner?

We'll use [Statistics::Descriptive](http://search.cpan.org/~shlomif/Statistics-Descriptive-3.0100/lib/Statistics/Descriptive.pm) module.

```bash
perl -MStatistics::Descriptive -ane 'BEGIN{our $stat = Statistics::Descriptive::Full->new}; $stat->add_data(@F[1..4]); print $stat->standard_deviation,"\n"; $stat->clear' filename
```

`$stat->clear` at the end was needed since data is added not assigned to $stat each time, so in order to prevent cumulative calculation, `$stat` variable should be cleared each time.