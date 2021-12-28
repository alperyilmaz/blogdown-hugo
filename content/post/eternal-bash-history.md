+++
title = "Eternal bash history"
date = 2016-09-27T00:26:05+03:00
draft = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["commandline"]
categories = []

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = ""
caption = ""
preview = true

+++

After starting to use the bash, you quickly realize bash history is an invaluable asset. You can quickly search and find a previous command in order to remember when and what you have done. I was using a primitive way to archive the history with which I accumulated history of commands since 2008. The primitive setup has two parts. First part is a cron job:

```
0 13 3,11,24 * *   /bin/cat ~/.bash_history > ~/.history_backup_`date +\%Y\%m\%d`
```

This cron job line means: on 3rd, 11th and 24th of each month at 1pm dump contents of `.bash_history` file to history backup file. By time, I ended up with 1-2 files per month.

Second part is couple bash functions to merge the archive.

```bash
oldhistory(){ for file in /home/alper/.history_backup_20*; do cat $file; echo; done | perl -ne 'if (/^#([0-9]{10}$)/){my $nextline=<>; $hash{$1}=$nextline }else{next}; END{print map { $hash{$_} } sort keys %hash}'; }

oldhistory-time(){ for file in /home/alper/.history_backup_20*; do cat $file; echo; done | perl -ne 'if (/^#([0-9]{10}$)/){ my $nextline=<>; $hash{$1}=$nextline }else{next}; END{print map {scalar localtime($_)."\t".$hash{$_}} sort keys %hash}'; }
```

However, just recently I noticed that the bash history file is trimmed and contained only 10 days of worth commands. Luckily, I recovered a backup of `.bash_history` file and didn't lose much data. But, it was a wakeup call, my primitive system is prone to lose data without a notice. So, I started searching for a better solution to archive bash history.

When I search online I first came across [this post](https://lukas.zapletalovi.com/2013/03/never-lost-your-bash-history-again.html). And then carried on searching and didn't find anything that intrigues me. I also searched [Github](https://github.com/search?o=desc&q=bash+history&s=stars) after which I got couple of aha moments. [Bashhub](https://github.com/rcaloras/bashhub-client) can save your bash history in the cloud. That was very interesting and useful but I didn't like the third party keeping the commands. There were couple more projects offering nice UI or advanced features (sqlite database for instance), such as [history](https://github.com/autochthe/history), [hstr](https://github.com/dvorka/hstr), [bash-history-sqlite](https://github.com/thenewwazoo/bash-history-sqlite).

Finally, I got a good idea from [this blog](https://spin.atomicobject.com/2016/05/28/log-bash-history/). Now, I'm testing this method and hoping that it would work with less problems.

```bash
export PROMPT_COMMAND='history -a; history -n; if [ "$(id -u)" -ne 0 ]; then echo -e "$(date "+%Y-%m-%d.%H:%M:%S")\t$(hostname)\t$(pwd)\t$(history -p \!-1)" >> ~/.logs/bash-history-$(hostname)-$(date "+%Y-%m-%d").log; fi'
```

> **Update (2017-05-26):** This code causes problem with `screen`. Within `screen` the command is not printed out and written correctly into bash-history file.
