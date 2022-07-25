# Indian_CisAB_Casereport

This repository comprises a list of data files elaborating the methodology and data analysis of a rare cis-AB blood group identified in Indian subcontinent

The sample used in the study was subjected to whole exome sequencing. Computational analysis of the sequencing data duly invloved the alignment of the raw sequencing output files to GRCh37/hg19 human reference genome. This was followed by systematic compilation of genetic variations in Variant Call Format (VCF) file. The variants were annotated for their functional consequences using ANNOVAR.

For ease of analysis the alignment and variant call files were subsetted (including chromosome 9 data exclusively). The subsetted files were further used to analyse the phasing of genetic variants using Plink and SHAPEIT tools. 


<h2>Steps followed in the analysis of data
<h3> Input files 
Raw sequencing outfiles (.fastq files - paired end). Samples underwent Whole Exome Sequencing (WES).
<h3> Quality Control, Alignment and Variant Calling
Read files were checked for their quality using FastQC and were subjected to alignment to reference genome (GRCh37/hg19) and variant calling using Illumina DRAGEN v3.4 Bio-IT platform
<h3> Variant annotation and filtering
Compiled list of genetic variants were systematically annotated for their functional consequences from a range of computational tools using ANNOVAR
