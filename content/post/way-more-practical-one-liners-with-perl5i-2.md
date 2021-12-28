---
title: "Way more practical one-liners with perl5i"
date: 2010-04-26T23:48:05+00:00
tags:
  - one-liner
  - perl
---
[perl5i](http://search.cpan.org/dist/perl5i/lib/perl5i.pm) project explains itself as "Perl 5 has a lot of warts, fix as much of it as possible in one pragma". You can run your scripts with it by including perl5i (ie, use perl5i;). Best part is, it can be run at commandline with `$ perl5i -e` .

perl5i includes [Autobox module](http://search.cpan.org/~swalters/autobox-Core-1.2/) which lets you call methods on primitive datatypes such as scalars and arrays (eg. "hello world"->print). This feature allows constructing very compact one-liners as shown below:

```bash
perl5i -e 'my @arr = ( 1 .. 10 ); @arr->map(sub {$_ ** 4 })->grep(sub { $_ > 3 })->sum->say'
```

Explanation: calculate to the 4th power for each element of @arr. Of those 4th power numbers, filter out the ones smaller than 3. Then sum up the new array and print the result.

```bash
perl5i -e 'my @test=(1,2,3,4); my @compare=(2,4,6); @test->intersect(\@compare)->size->concat("\t")->print'
```

Explanation: Find the intersection of two arrays (assigned to new array) and add tab character to size of (intersection) array and then print it.

```bash
perl5i -e ' my $hashref = { foo => 10, bar => 20, baz => 30, quux => 40 }; $hashref->values->sort->join("-")->say'
```

Explanation: sort the values of hash and print them by joining with "-" character.