
# Readme For Study GSE58455, GSE56890 Prep
###### 9/14/2014
###### By: Calvin D. Cox
###### Clemson University 2014 

Summary: This is an NGS Workflow that I constructed to evaluate expression levels in select genes from Mouse Samples.

# Methods For GSE58455: 

###### **All procedures listed take place in /feltus/calvinc/USCMouse1_58455/ unless specified otherwise in code or comments.
1. Downloaded Accession Data from NCBI Database
  Experiment URL: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE58455
2. Input *.sra into Fastq Dump
3. Input SRR1391033.sra into fastqc for a base comparison post-trim
4. Input *.fastq into Trimmomatic (v .30)
5. Input SRR1391033.sra into fastqc for post-trim analysis
6. Run *.fastq through Tophat (v?)
7. Ran treatment .bam outputs through cuffdiff (Cufflinks v 2.1.1)
8. Extracted relevant gene data.



## Treatment Key

##### Embryo 13.5 Week
SRR1391033.sra  
SRR1391036.sra  
SRR1391034.sra  
SRR1391038.sra  
SRR1391039.sra  
SRR1391035.sra  
SRR1391037.sra  

##### 16 Week Adult
SRR1391051.sra  
SRR1391050.sra  
SRR1391049.sra  
SRR1391048.sra  
SRR1391047.sra  
SRR1391046.sra  

##### Sham 12 Week Adult
SRR1391052.sra  
SRR1391053.sra  
SRR1391054.sra  
SRR1391055.sra  

##### 6 Week Adult
SRR1391040.sra  
SRR1391041.sra  
SRR1391042.sra  
SRR1391043.sra  
SRR1391044.sra  
SRR1391045.sra  

Files were stored in tophat (/feltus/calvinc/USCMouse1_58455/tophat) used the script below to move them to bambin and rename them with unique names.
**
for i in SRR*trimTop; do cp /common1/feltus/calvinc/USCMouse1_58455/tophat/$i/accepted_hits.bam ../$i.accepted_hits.bam; done
**


##### Bam Output with Matching Treatments 
(Directory: /common1/feltus/calvinc/Mouse_Study_First/trimbin/bambin) 

E13.5 
SRR33trimTop.accepted_hits.bam 
SRR34trimTop.accepted_hits.bam 
SRR35trimTop.accepted_hits.bam 
SRR36trimTop.accepted_hits.bam 
SRR37trimTop.accepted_hits.bam 
SRR38trimTop.accepted_hits.bam 
SRR39trimTop.accepted_hits.bam 

16 wk 
SRR46trimTop.accepted_hits.bam 
SRR47trimTop.accepted_hits.bam 
SRR48trimTop.accepted_hits.bam 
SRR49trimTop.accepted_hits.bam 
SRR50trimTop.accepted_hits.bam 
SRR51trimTop.accepted_hits.bam 

Sham_12wk 
SRR52trimTop.accepted_hits.bam 
SRR53trimTop.accepted_hits.bam 
SRR54trimTop.accepted_hits.bam 
SRR55trimTop.accepted_hits.bam 

Adult 6wk 
SRR40trimTop.accepted_hits.bam 
SRR41trimTop.accepted_hits.bam 
SRR42trimTop.accepted_hits.bam 
SRR43trimTop.accepted_hits.bam 
SRR44trimTop.accepted_hits.bam 
SRR45trimTop.accepted_hits.bam 
