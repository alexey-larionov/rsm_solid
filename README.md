This is a pipeline to process whole exome sequencing data from fastq to annotated vcf. 

The main steps include:
- Source FASTQ import, trimming withCutadapt and assessing with FastQC, 
- Alignment against b37 using BWA MEM or backtrack,
- BAM files merging, preprocessing and QC (samtools, picard, GATK, Qualimap etc)
- Variants calling by GATK using GVCF and HC 
- Variants assessment (custom R scripts and samtools vcfstats) 
- Variants filtering by VQSR and a set of hard filters 
- Variants annotation by VEP
- Export of annotated variants to plain text fils for downstream analysis in R.

Code is split into steps (modules), located in folders with self-explanatory names.  
It is assumed that after each step the user assess the results (metrics produced by fastQC, 
picard, qualimap, vqsr, vcfstats, vep etc) before taking analysis to the next step.  
The steps are started by the launcher script with a job description file 
(see folder with the job description templates).  

The pipeline is deployed on a local university cluster.  
This repository is intended for the author's pesonal use.  
However, as long as it is kept public, everyone may have a look.  
