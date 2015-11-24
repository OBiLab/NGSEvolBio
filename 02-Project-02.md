---
course: NGS for evolutionary biologists: from basic scripting to variant calling
title: Project 01 - BAESIAN SKYLINE PLOT
requires: knowledge of basic shell commands, basic concept of Phylogenetics
author: Enza Colonna, Chiara Batini  
time: 6 hours  
---
------------
> #### Learning Objectives
------------


### Outline:

[Analyse sex-specific demographic changes in a European population](#main)

1. [The biological question](#sec1)

2. [The software required](#sec2)

      -[From raw data to variants](#sec2.1)

      -[Task specific](#sec2.2)

3. [Project tasks](#sec3)

  -[Download the fastq files](#sec3.1)

  -[Process the NGS data ](#sec3.2)

  -[Prepare input files for BEAST](#sec3.3)

  -[Run BEAST](#sec3.4)

  -[Interpret the output and prepare a report](#sec3.5)

4. [Recap](#sec4)

5. [References](#sec5)

__________________________________________________________

############################################

# Analyse sex-specific demographic changes in a European population




## The biological question
We have sequenced the whole mitochondrial genome and 2.2Mb of the Y chromosome in 20 individuals from the CEU population included in the [HapMap](http://hapmap.ncbi.nlm.nih.gov/) project. We want to compare how the male and female effective population sizes changed through time and understand the role of sex-biased processes in the evolution of a **NE CHIARA ??????** European population.

We will use a Bayesian method, Bayesian Skyline Plot, that co-estimates the genealogy, the demographic history and the substitution-model parameters from aligned sequences. Take some time to read this [review](https://pgl.soe.ucsc.edu/ho11.pdf) about the methods.

**Bayesian inference CHIARA**

############################################

## The software required

############################


### From raw data to variants

As the course will cover in very detail this part we will skip and talk only about more specific software.
In summary you will have to follow the pipeline we have applied during the practicals.

############################
### Task specific

#### BEAST
[BEAST](http://beast.bio.ed.ac.uk/) is a program for Bayesian analysis of molecular sequences based on the construction of [phylogenetic trees](https://en.wikipedia.org/wiki/Phylogenetic_tree).   BEAST uses [Markov chain Monte Carlo (MCMC)](https://en.wikipedia.org/wiki/Markov_chain_Monte_Carlo) to average over the tree space. This allows to test evolutionary hypothesis by weighing each tree on its posterior probability and avoiding fixing the tree topology.

Take some time to read one of the **[BEAST tutorials](http://beast.bio.ed.ac.uk/Tutorials) CHI quale tutorial?**. We recommend you read the *Influenza BEAST Practical.zip*, but any other will be good as well. Download the tutorial and take time to go through the files.

BEAST  produces outputs like this:

>![CHIARA CHE IMMAGINE]()

>This plot is form the [1000 Genomes Nature's paper](http://www.nature.com/nature/journal/v526/n7571/full/nature15393.html). Every vertical line correspond to one individual and colors represent subdivisions in clusters according to genetic similarities. Each individual is colored with  one or more colors according to the likelihood of belonging to one or more clusters.

>Three-letters codes indicate population within continents. In some populations (e.g. JPT) individuals are very genetically similar and only one color is observed. In others (e.g. PUR) individuals belong to several clusters, some of which (e.g. dark blue) shared among different populations. This indicate admixture between these popuations.



############################################

## Project tasks

############################

### 1. Download the fastq files

The Fastq files we will use here were extracted from a custom enrichment experiment. Agilent SureSelect was used to capture 26Mb of the human genome, and paired-end libraries were run on a HiSeq 2000 sequencer with 100bp read length (Hallast et al, 2015).


############################

### 2. Process the NGS data
You will align the reads to the reference genome, refine the BAM and make **QC ??? abbreviazioni?**, do the variant calling and filtering.

############################

### 3. Prepare input files for BEAST

BEAST take as **input** aligned DNA sequences in two options
1. `.nex`: [NEXUS](http://hydrodictyon.eeb.uconn.edu/eebedia/index.php/Phylogenetics:_NEXUS_Format) file format. This is a traditional file format for storing sequence information to be used in phylogenetic analyses.
The `.nex` file is subdivided in blocks of information.

2. `.xml`: this is an equivalent of the NEXUS format written in the [Extensible Markup Language (XML)](https://en.wikipedia.org/wiki/XML) style. While the `.xml` file format might seem complicated at first sight, it can be easily read by considering that it is subdivided in blocks containing the sequences and the information for BEAST about (a) the parameters of the demographic model, and (b) the parameters of the MCMC.  

Take some time to look at samples file in the tutorial To generate the input file for BEAST  we will use a routine of BEAST called [BEAUTI](http://beast.bio.ed.ac.uk/beauti).

#####  3.1 Convert `.vcf` in `.fasta` files

BEAUTI take as input files in the [`.fasta` format](https://en.wikipedia.org/wiki/FASTA_format), so our first step is to convert the `.vcf` in `fasta`. As usual there are several ways to do this among which the useful [PDGSpider](http://www.cmpg.unibe.ch/software/PGDSpider/)

**CHIARA DOWNLOAD?**


```
**CHIARA**

```
> comments to explainthe command line ??


This command line will generate a `.fasta`  file in your work directory

```
ls

-rw-rw-r-- 1 user user        676 19 nov 12:17 myfile.fasta

***CHIARA****

```


############################

#####  Submit a job to job scheduler  

If we are using a very small file, the command line described above can be very fast with and run interactively. However in reality files are large and we might want to submit jobs instead.

If we are using a machine with a [PBS](https://en.wikipedia.org/wiki/Portable_Batch_System) job scheduler we might want to embed the command line in a PBS script as described in the [instructions](00-beforewestart.md) to run jobs with PBS.

The PBS script will look like:

```
#!/bin/bash
#PBS -q workq
#PBS -N myname   # this will be visible in the scheduler queue
#PBS -l nodes=1:ppn=1
#PBS -o outerr/????????
#PBS -e outerr/????????????

???????????????????????????

```
If the job is successful, you will see three new files in your data folder

```
ls


-rw-rw-r-- 1 user user        676 19 nov 12:17 myfile.fasta

```

#####  3.2 Generate `.xml` file

To generate a BEAST `.xml` file we use the BEAUTI. BEAUTI has a graphical interface and we will use this??????
You will go through a number of steps all guided by the interface.

a) Loading the NEXUS/FASTA  file
b) Setting the [substitution model](https://en.wikipedia.org/wiki/Substitution_model)
c) Setting the ‘molecular clock’ model
d) Setting the tree prior
e) Setting up the priors
f) Setting up the operators
g) Setting the MCMC options

```
***CHIARA******

-rw-rw-r-- 1 user user        676 19 nov 12:17 myfile.xml

```
>

As usually, rather than run the command line interactively we might want to embed the command line in a bash script and submit a job. If the job is successful we will see new files in our data directory:

```
****CHIARA***

```


### 3.4 Run BEAST

We are now ready to run BEAST. This is a simple step and will produce
 - `.log` file.
 - `.trees` file (NEXUS format): trees  (either phylogenies or geneologies) sampled  at the same time  during the MCMC


Once we are sure about this let's run the **BEAST interface??? or command line???** (or [embed it in a script](#sec3.3.1) to be submitted to a job scheduler):

```
?????????????????

```
> comments

If all works fine, there will be two new files in your data folder:

```
ls

-rw-rw-r-- 1 user user     27054 19 nov 14:06 myfile.log
-rw-rw-r-- 1 user user     27054 19 nov 14:06 myfile.trees
```

Take time to go through the heading and understand the content of each column.
BEAST will produce ... little explanation ...
This output is not directly interpretable.. you need...


############################

### 5. Interpret the output and prepare a report

To analyze the results of running BEAST we are going to use [Tracer](http://tree.bio.ed.ac.uk/software/tracer/), a program for analysing the trace files generated by Bayesian MCMC runs. It is also distributed with BEAST [here](http://beast.bio.ed.ac.uk/tracer).
Tracer provides summary statistics of the MCMC runs  but it also produces an estimates of the marginal posterior distributions of parameters of our model.

Tracer produces graphical outputs but you can also decide to export Trace output to a file and make your own graphs using R


############################################
## Recap

To summarize, below a list of all the task-specific software that we need to use. We will run some of them and use only file format from others.

  -PDGSpider
  -BEAUTI
  -BEAST
  -Tracer

![Pipeline](img/beastpipe.png)


############################################
## References
