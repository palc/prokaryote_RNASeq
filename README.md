# prokaryote_RNASeq

This repository is a usable, publicly available tutorial for analyzing differential expression data and creating topological gene networks. All steps have been provided for the UConn CBC Xanadu cluster here with appropriate headers for the Slurm scheduler that can be modified simply to run.  Commands should never be executed on the submit nodes of any HPC machine.  If working on the Xanadu cluster, you should use sbatch scriptname after modifying the script for each stage.  Basic editing of all scripts can be performed on the server with tools such as nano, vim, or emacs.  If you are new to Linux, please use <a href="https://bio Informatics.uconn.edu/unix-basics/">this</a> handy guide for the operating system commands.  In this guide, you will be working with common bio Informatic file formats, such as <a href="https://en.wikipedia.org/wiki/FASTA_format">FASTA</a>, <a href="https://en.wikipedia.org/wiki/FASTQ_format">FASTQ</a>, <a href="https://en.wikipedia.org/wiki/SAM_(file_format)">SAM/BAM</a>, and <a href="https://en.wikipedia.org/wiki/General_feature_format">GFF3/GTF</a>. You can learn even more about each file format <a href="https://bio Informatics.uconn.edu/resources-and-events/tutorials/file-formats-tutorial/">here</a>. If you do not have a Xanadu account and are an affiliate of UConn/UCHC, please apply for one <a href="https://bio Informatics.uconn.edu/contact-us/">here</a>.


<h2 id="Header_1">Introduction and programs</h2>
This tutorial will serve as an introduction to analysis of prokaryote RNASeq data with an associated reference genome. The tools used for this analysis strictly consist of freeware and open-source software - any bioinformatician can perform the following analysis without any licenses!

<strong>Software download links:</strong>

<a href="https://github.com/ncbi/sra-tools">SRA Toolkit</a>
<a href="http://www.bioinformatics.babraham.ac.uk/projects/fastqc/">FastQC</a>
<a href="https://github.com/najoshi/sickle">Sickle</a>
<a href="http://ccb.jhu.edu/software/EDGE-pro/">EDGE-pro</a>
<a href="http://www.r-project.org/">R</a>
<a href="https://www.rstudio.com/">RStudio</a>
<a href="http://bioconductor.org/packages/release/bioc/html/DESeq2.html">DESeq2</a>


<h2 id="Header_2"> Download raw reads in fastq format: SRA Toolkit</h2>
The first step is to retrieve the biological sequence data from the <a href="https://www.ncbi.nlm.nih.gov/sra">Sequence Read Archive</a>. The data that we will be using is from this <a href="https://www.ncbi.nlm.nih.gov/bioproject/PRJNA116667">experiment</a>, which analyzes two strains of Listeria monocytogenes (10403S and DsigB) with two replicates per strain, resulting in a total of four raw read files. We will use the <span style="color: #339966;">fastq-dump</span> utility from the SRA toolkit to download the raw files by accession number into fastq format. This format is necessary because the software used to perform quality control, Sickle, requires fastq files as input.

<pre style="color: silver; background: black;">module load sratoolkit/2.8.1
fastq-dump SRR034450
fastq-dump SRR034451
fastq-dump SRR034452
fastq-dump SRR034453</pre>
