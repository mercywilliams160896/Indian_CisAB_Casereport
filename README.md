# Indian_CisAB_Casereport

This repository comprises a list of data files elaborating the methodology and data analysis of a rare cis-AB blood group identified in Indian subcontinent

The sample used in the study was subjected to whole exome sequencing. Computational analysis of the sequencing data duly invloved the alignment of the raw sequencing output files to GRCh37/hg19 human reference genome. This was followed by systematic compilation of genetic variations in Variant Call Format (VCF) file. The variants were annotated for their functional consequences using ANNOVAR.

For ease of analysis the alignment and variant call files were subsetted (including chromosome 9 data exclusively). The subsetted files were further used to analyse the phasing of genetic variants using Plink and SHAPEIT tools. 

<h2>Tools/Packages used for analysis</h2><br/>
1. FastQC<br/>
2. Illumina DRAGEN Bio-IT platform<br/>
3. ANNOVAR<br/>
4. Samtools<br/>
5. Awk scripting<br/>
6. PLINK<br/>
7. SHAPEIT <br/>
<h2>Steps followed in the analysis of data
<h3> Input files </h3>
Raw sequencing outfiles (.fastq files - paired end). Samples underwent Whole Exome Sequencing (WES).
<h3> Quality Control, Alignment and Variant Calling </h3>
Read files were checked for their quality using FastQC and were subjected to alignment to reference genome (GRCh37/hg19) and variant calling using Illumina DRAGEN v3.4 Bio-IT platform <br/>
<h5> <i>Commands used</i> <br/>
<i>$ fastqc Sample_R1.fastq.gz</i> <br/>
<i>$ fastqc Sample_R2.fastq.gz</i> <br/>
<i>$ dragen -r {hg19 reference genome} -1 {Sample_R1.fastq.gz} -2 {Sample_R2.fastq.gz} --enable-variant-caller true --output-file-prefix {outfilename} --output-directory {outfilefolder}</i> </h5>
<h3> Variant annotation and filtering </h3>
Compiled list of genetic variants were systematically annotated for their functional consequences from a range of computational tools using ANNOVAR
<h5> <i>Commands used</i> <br/>
<i>$ table_annovar.pl {Sample.avinput} Annovar/humandb --buildver hg19 --outfile {outfilename-prefix} --protocol refGene,cytoBand,genomicSuperDups,dbnsfp33a,avsnp147,exac03,1000g2015aug_all --operation g,r,r,f,f,f,f --nastring NA  --otherinfo</i> <br/>
<h3> BAM and VCF subsetting </h3>
A smaller subset of the alignment (.bam) file comprising chromosome 9 information was created using SAMTOOLS. Similarly, variants spanning chromosome 9 were subsetted from the ouput VCF using bespoke AWK commands/scripts
<h5> <i>Commands used</i> <br/>
<i>$ samtools view {Sample.bam} chr9 -b > Sample_chr9.bam</i> <br/>
<i>$ awk -F'\t' '{if($1 == "chr9") print $0}' {Sample.vcf} > Sample_chr9.vcf</i> <br/>
<h3> File preprocessing and variant phasing </h3>
The subsetted vcf file was preprocessed to .ped and .map file formats using PLINK tool. The obtained PLINK output files were further used to perform variant phasing using SHAPEIT tool utilizing the publicly available refrence panel of haplotypes provided by the 1000 Genomes Project. THe files can be downloaded at https://mathgen.stats.ox.ac.uk/impute/impute_v2.html#reference
