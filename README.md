
# Readme For Study GSE58455, GSE56890 Prep
######9/14/2014
######By: Calvin D. Cox
######Clemson University 2014

#Methods For GSE58455: 

######**All procedures listed take place in /feltus/calvinc/USCMouse1_58455/ unless specified otherwise in code or comments.
1. Downloaded Accession Data from NCBI Database
  Experiment URL: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE58455
2. Input *.sra into Fastq Dump
3. Input SRR1391033.sra into fastqc for a base comparison post-trim
4. Input *.fastq into Trimmomatic (v .30)
5. Input SRR1391033.sra into fastqc for post-trim analysis
6. Run *.fastq through Tophat (v?)
7. Ran treatment .bam outputs through cuffdiff (Cufflinks v 2.1.1)
8. Extracted relevant gene data.



###*******************************************
### Treatment Key
###
### Embryo 13.5 Week
### SRR1391033.sra
### SRR1391036.sra
### SRR1391034.sra
### SRR1391038.sra
### SRR1391039.sra
### SRR1391035.sra
### SRR1391037.sra
###
### 16 Week Adult
### SRR1391051.sra
### SRR1391050.sra
### SRR1391049.sra
### SRR1391048.sra
### SRR1391047.sra
### SRR1391046.sra
###
### Sham 12 Week Adult
### SRR1391052.sra
### SRR1391053.sra
### SRR1391054.sra
### SRR1391055.sra
###
### 6 Week Adult
### SRR1391040.sra
### SRR1391041.sra
### SRR1391042.sra
### SRR1391043.sra
### SRR1391044.sra
### SRR1391045.sra
###
###******************************
###Downloaded SRA files from NCBI (Downloaded to /feltus/calvinc/USCMouse1_58455/download directory)
###******************************
#!/bin/bash
#PBS -N MDOWNLOAD
#PBS -l select=1:ncpus=1:mem=8gb,walltime=168:00:00
#PBS -j oe
#PBS -q feltus

cd $PBS_O_WORKDIR

#Downloading files from ftp list

wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391059/SRR1391059.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391058/SRR1391058.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391057/SRR1391057.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391056/SRR1391056.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391055/SRR1391055.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391054/SRR1391054.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391053/SRR1391053.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391052/SRR1391052.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391051/SRR1391051.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391050/SRR1391050.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391049/SRR1391049.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391048/SRR1391048.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391047/SRR1391047.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391046/SRR1391046.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391045/SRR1391045.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391044/SRR1391044.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391043/SRR1391043.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391042/SRR1391042.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391041/SRR1391041.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391040/SRR1391040.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391039/SRR1391039.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391038/SRR1391038.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391037/SRR1391037.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391036/SRR1391036.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391035/SRR1391035.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391034/SRR1391034.sra
wget ftp://ftp-trace.ncbi.nlm.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR139/SRR1391033/SRR1391033.sra


###********************
### Fastqdump of all SRA files in working directory. (/feltus/calvinc/USCMouse1_58455/fastqdump)
###********************

#!/bin/bash
#PBS -N FASTDUMP
#PBS -l select=1:ncpus=1:mem=12gb,walltime=72:00:00
#PBS -j oe

cd $PBS_O_WORKDIR

#Dumping SRA

fastq-dump /feltus/calvinc/USCMouse1_58455/download/*.sra

#Compression

gzip /feltus/calvinc/USCMouse1_58455/fastqdump/*.fastq

###***************
### Trimming Fastq files (Directory /feltus/calvinc/USCMouse1_58455/trimmomatic)
### Below is a sample of one of the trim files (created a trim file for each fastq.gz file.)
###***************
#!/bin/bash
#PBS -N TRIMMO33
#PBS -l select=1:ncpus=1:mem=16gb,walltime=168:00:00
#PBS -j oe
#PBS -q feltus

cd $PBS_O_WORKDIR

#Loading Sofware
PATH=$PATH:/feltus/calvinc/software/Trimmomatic-0.32

#Copy to localscratch
cp /feltus/calvinc/USCMouse1_58455/SRR1391033.fastq.gz /local_scratch

#Trim Job
java -jar /feltus/calvinc/software/Trimmomatic-0.32/trimmomatic-0.32.jar SE -phred33 /local_scratch/SRR1391033.fastq.gz trimSRR1391033.fastq.gz ILLUMINACLIP:illuminaClip-1.fa:2:30:10 LEADING:3 TRAILING:6 SLIDINGWINDOW:4:15 MINLEN:30
###***********
###Tophat Job Scripts(Directory excecuted /feltus/calvinc/USCMouse1_58455/tophat)
### Sample code below (individual tophat scripts)
###***********
#!/bin/bash
#PBS -N TOPHATSRR33
#PBS -l select=1:ncpus=1:mem=16gb,walltime=72:00:00
#PBS -j oe

cd $PBS_O_WORKDIR

#Loading Software
export PATH=$PATH:/feltus/calvinc/software/bowtie2-2.2.3
export PATH=$PATH:/feltus/calvinc/software/tophat-2.0.12.Linux_x86_64

#Adding working files to local_scratch
cp /feltus/calvinc/USCMouse1_58455/trimmomatic/trimSRR1391033.fastq.gz /local_scratch
cp /feltus/calvinc/USCMouse1_58455/bin/mm10* /local_scratch

#Running Tophat
tophat -G /feltus/calvinc/USCMouse1_58455/bin/Mus_musculus.GRCm38.76.gtf -o SRR45trimTop /local_scratch/mm10 /local_scratch/trimSRR1391033.fastq.gz
###**************************
### Files were stored in tophat (/feltus/calvinc/USCMouse1_58455/tophat) used the script below to move them to bambin and rename them with unique names.
###**************************

for i in SRR*trimTop; do cp /common1/feltus/calvinc/USCMouse1_58455/tophat/$i/accepted_hits.bam ../$i.accepted_hits.bam; done

###**************************
###Bam Output with Matching Treatments (Directory: /common1/feltus/calvinc/Mouse_Study_First/trimbin/bambin) 
###**************************
###
###E13.5
###SRR33trimTop.accepted_hits.bam
###SRR34trimTop.accepted_hits.bam
###SRR35trimTop.accepted_hits.bam
###SRR36trimTop.accepted_hits.bam
###SRR37trimTop.accepted_hits.bam
###SRR38trimTop.accepted_hits.bam
###SRR39trimTop.accepted_hits.bam
###
###16 wk
###SRR46trimTop.accepted_hits.bam
###SRR47trimTop.accepted_hits.bam
###SRR48trimTop.accepted_hits.bam
###SRR49trimTop.accepted_hits.bam
###SRR50trimTop.accepted_hits.bam
###SRR51trimTop.accepted_hits.bam
###
###Sham_12wk
###SRR52trimTop.accepted_hits.bam
###SRR53trimTop.accepted_hits.bam
###SRR54trimTop.accepted_hits.bam
###SRR55trimTop.accepted_hits.bam
###
###Adult 6wk
###SRR40trimTop.accepted_hits.bam
###SRR41trimTop.accepted_hits.bam
###SRR42trimTop.accepted_hits.bam
###SRR43trimTop.accepted_hits.bam
###SRR44trimTop.accepted_hits.bam
###SRR45trimTop.accepted_hits.bam
###
###****************
### Grepped output to find genes of intrest (wwp1 & gja1) These commands were used in either the shamcuff output folder or the E135_6 folder to get output. Data was manually copied and put in an external table (Mouse Study Summary).
### Executed Paths: /common1/feltus/calvinc/Mouse_Study_First/trimbin/bambin/shamcuff
### /common1/feltus/calvinc/Mouse_Study_First/trimbin/bambin/E135_6
###****************

cat gene_exp.diff | grep Gja1
cat gene_exp.diff | grep Wwp1
cat gene_exp.diff | grep Gapdh
cat gene_exp.diff | grep Gja5
cat gene_exp.diff | grep Actb

cat isoform_exp.diff | grep Gja1
cat isoform_exp.diff | grep Wwp1
cat isoform_exp.diff | grep Gapdh
cat isoform_exp.diff | grep Gja5
cat isoform_exp.diff | grep Actb

###******************************************************
###Study GSE56890 - FVB v TAC Mice
###******************************************************
### Directories:
###		USCMouse2_56890
###			bambin		#Bin for all treatments
###			download		#Initial download folder for SRA files
###			bin			#Container folder of extra software or reference files
###			fastqdump	#Fastqdump output folder and .pbs file container
###			tophat		#Tophat .pbs container and tophat output container
###			trimmomatic		#Contains Trim output for Trimmomatic
###******************************************************

###*********************
### Fastq Dump Script (Directory /feltus/calvinc/USCMouse2_56890/fastqdump)
###*********************

#!/bin/bash
#PBS -N FASTDUMP.0
#PBS -l select=1:ncpus=1:mem=12gb,walltime=24:00:00
#PBS -j oe

#source /etc/profile
#module add tophat/2.0.9
#module add bowtie2/2.1.0
#module add samtools/0.1.19

cd $PBS_O_WORKDIR

#Into TAC Treatment Folder
cd /feltus/calvinc/USCMouse2_56890
fastq-dump *.sra

#Compression

gzip *.fastq

###********************
###Trimmomatic Trim (Directory /feltus/calvinc/USCMouse2_56890/trimmomatic)
###Sample Code
###********************
#!/bin/bash
#PBS -N TRSRR138
#PBS -l select=1:ncpus=1:mem=16gb,walltime=168:00:00
#PBS -j oe
#PBS -q feltus

cd $PBS_O_WORKDIR

#Loading Sofware
PATH=$PATH:/feltus/calvinc/software/Trimmomatic-0.32

#Copy to localscratch
cp /feltus/calvinc/USCMouse2_56890/fastqdump/SRR1187138.fastq.gz /local_scratch

#Trim Job
java -jar /feltus/calvinc/software/Trimmomatic-0.32/trimmomatic-0.32.jar SE -phred33 /local_scratch/SRR1187138.fastq.gz trimSRR1187138.fastq.gz ILLUMINACLIP:illuminaClip-1.fa:2:30:10 LEADING:3 TRAILING:6 SLIDINGWINDOW:4:15 MINLEN:30

###********************
###Tophat Script (Directory /feltus/calvinc/USCMouse2_56890/tophat)
###Used the mm10 index from the Bowtie website. Gtf file was created by running the make_mm10.sh file provided in the index package. After the Gtf file was created we manually added the chromosome numbers.
### Code? 
###Sample Code Below of Tophat Script
###********************
#!/bin/bash
#PBS -N TOPHAT7137
#PBS -l select=1:ncpus=1:mem=16gb,walltime=168:00:00
#PBS -j oe
#PBS -q feltus

cd $PBS_O_WORKDIR

#Loading Software
export PATH=$PATH:/feltus/calvinc/software/bowtie2-2.2.3
export PATH=$PATH:/feltus/calvinc/software/tophat-2.0.12.Linux_x86_64

#Adding working files to local_scratch
cp /feltus/calvinc/USCMouse2_56890/trimmomatic/trimSRR1187137.fastq.gz /local_scratch
cp /feltus/calvinc/USCMouse1_58455/bin/mm10* /local_scratch

#Running Tophat
tophat -G /feltus/calvinc/USCMouse1_58455/Mus_musculus.GRCm38.76-rename.gtf -o SRR1187137trimTop /local_scratch/mm10 /local_scratch/trimSRR1187137.fastq.gz
###********************
