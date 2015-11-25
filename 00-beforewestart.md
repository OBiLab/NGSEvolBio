---
course: NGS for evolutionary biologists: from basic scripting to variant calling
title: organizing the space
author: Enza Colonna
credits: Tiziana Castrignano
time: 6 hours  
---

# Projects
The  projects are

Team work


# PICO

## Get there

We will be hosted for this course on the CINECA machine [PICO](http://www.cineca.it/en/news/pico-cineca-new-platform-data-analytics-applications). This machine is in [Bologna](https://en.wikipedia.org/wiki/Bologna) a nice city in north Italy.

![pico](/img/pico.png)


To **connect** to PICO
```
ssh username@login.pico.cineca.it

```

## Modules

Bioinformatics applications, public databases and annotations are pre-installed on PICO.
The work environment is organized in modules, a set of installed libs,
tools and applications available for all users.

To to list the installed modules:

```
module available
```


**“Loading”** a module means that a series of (useful) shell environment variables
wil be set. To load a module two  steps are required:


1. Initialize the module environment:
```
module load profile/advanced
```

2. load a module program:
```
module load name_program
```

**Other useful module commands**

Full list of the modules available in your profile divided by: environment, libraries, compilers, tools, applications
```
module available
```

Unloads a specific module
```
module unload module_name
```

Shows the environment variables set by a specific module
```
module show module_name
```

Gets all informations about how to use a specific module
```
module help module_name
```

Gets rid of all the loaded modules
```
module purge
```


## Workspace

As you might have already heard, PICO is organized into spaces. Let's look a little bit closer to them:  

### $CINECA_HOME

This is your "home" directory, that is not super big but files are kept here for long time.
Home is permanent, backed-up, and local.
● Quota = 5GB.
● For source code or important input files.

To access this space:

```
cd $HOME
```

If you check where you are using the shell command `pwd` you will see something like this:

```
pwd

/pico/home/userexternal/someuser

```


### $CINECA_SCRATCH

This is a huge "temporary" space (all file not used for 30 days are removed)
Scratch is a large, parallel filesystem (GPFS) with no back-up.
● No quota max but a cleaning procedure removes files older than 30 days
● For temporary files


**For this course we will work here**, starting with copying all the big data files (e.g. `.fastq`)

To access this space:

```
cd $CINECA_SCRATCH
```

If you check where you are using the shell command `pwd` you will see something like this:

```
pwd

/pico/scratch/userexternal/someuser

```


### $WORK

This is a space assigned to a project. While every user has its own $HOME, many users can share the same $WORK.  Work is permanent, backed-up and project specific.
● 1 TB quota by default
● For temporary files

To access this space:
```
cd $WORK
```

If you check where you are using the shell command `pwd` you will see something like this:

```
pwd

/gpfs/work/someprojectname

```


## How to

### Be very well organized:  

- make a project folder: you can be work on many project at the same time!
- make project sub-folders: make a folder where to store the data and call it with a reasonable name (e.g. `projectname_data`) ; make sure you will be able to identify folders the day after.
- make a README file where you note main changes and list folder and file content
- give to files reasonable names :)

![folder](/img/foldertree.png)
