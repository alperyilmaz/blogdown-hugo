+++
title = "List of terminals with working folder names"
date = 2016-09-15T12:00:00+03:00
tags = ["commandline"]
+++

From time to time, I had many terminal tabs open and wanted to see the list of terminals along with working folder names. Finally, I fed up with the issue tried to find a solution. After fiddling with some code, here's the function that I added to `.bashrc` file

```bash
tty-list() { ps aux --sort=start_time | grep "pts/" | grep [b]ash | awk -F" +" '{print $2"\t"$7}' | while read PID PTS; do echo -n -e "$PTS""\t"; readlink -f /proc/$PID/cwd; done ; }
```

In terminal, tty-list command lists the pts number and working folder name as shown below:

```txt
pts/3	/home/alper
pts/6	/home/alper
pts/7	/home/alper/.logs
pts/8	/home/alper/tmp
pts/9	/home/alper/Documents/blog-github/website
pts/9   /home/alper/Documents/blog-github/website
```

The list is in order of opening the tabs. As you notice, last two lines are duplicate because when you issue the function there's while loop and I'm guessing it's running in a subshell so the terminal you run the function is counted twice.






