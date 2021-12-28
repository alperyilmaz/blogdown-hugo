---
title: "Most used commands in history"
date: 2010-04-08T09:11:53+00:00
tags:
  - linux
  - one-liner
  - perl
---
Most of the "most used commands" approaches does not consider pipes and other complexities.

This approach considers pipes, process substitution by backticks or `$()` and multiple commands separated by `;`

Perl regular expression breaks up each line using `|` or `<(` or `;` or \` or `$(` and picks the first word (excluding "do" in case of for loops) 

```bash
history | perl -F"\||<\(|;|\`|\\$\(" -alne 'foreach (@F) { print $1 if /\b((?!do)[a-z]+)\b/i }' | sort | uniq -c | sort -nr | head
```

Let's generate a fake history file which looks like this:

```txt
1  command file | command file | command | command
2  command <(command file) <(command file)
3  command file > file
4  for i in `command file`; do command file; command file; done | command
5  for i in $(command file); do command file; command file | command; done
```

This approach successfully counts 16 occurrences of "command" and 2 occurrences of "for".

Note: if you are using lots of perl one-liners, the perl commands/functions will be counted as well in this approach, since semicolon is used as a separator