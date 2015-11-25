---
course: NGS for evolutionary biologists: from basic scripting to variant calling
title: organizing the space
author: Enza Colonna, Chiara Batini, Pille Hallast
time: 6 hours  
---

# Workspace

## Where

We will be hosted for this course on the CINECA machine [PICO](http://www.cineca.it/en/news/pico-cineca-new-platform-data-analytics-applications). This machine is in [Bologna](https://en.wikipedia.org/wiki/Bologna) a nice city in north Italy.

As you might have already heard, the machine is organized into spaces. Let's look a little bit closer to those we will use

**$CINECA_SCRATCH**

This is a huge "temporary" space (all file not used for 30 days are removed)
For this course we will work here, starting with copying all the big data files (e.g. `.fastq`)

To access this space:

```
cd $CINECA_SCRATCH
```

Be well organized:  make a folder called `data` or  `mydata` or `projectname_data`; make sure you will be able to identify the folder the day after.
