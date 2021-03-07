## Alzheimer's Disease Blood Analysis


# Abstract

Alzheimer’s Disease (AD) is an irreversible, progressive neurodegenerative disorder that slowly destroys a person's cognitive and physical abilities. The cause of AD is unclear, but is believed to be a combination of genetic, environmental and lifestyle factors. Because the only way to definitely diagnose AD is post mortem, the search for earlier definitive detection is crucial. One way of doing this is by analyzing blood samples to detect biomarkers and microRNAs, a biomarker itself. A biomarker is defined as a characteristic that is objectively measured as an indicator of normal biological processes, while microRNAs (miRNAs) are non-coding RNA molecules that are involved in the regulation of gene expression. Utilizing influences from various other studies, we examined 70 blood samples of AD and controlled patients through our custom genetics pipeline in hopes of a breakthrough in understanding the pathology of the disease. We then implemented two different statistical tests, a non-parametric hypothesis test (Wilcoxon-Mann-Whitney Test) and a parametric hypothesis t-test (DESeq2). From these tests we were able to isolate nine significant samples to perform further analysis on its relationship and effect to AD.

# Introduction

### Background

AD is an age-related neurodegenerative disease that currently affects more than 5.5 million Americans and is considered the 6th leading cause of death in the United States[1]. It is an irreversible disease that causes declines in both mental and physical abilities as a result of rapidly declining brain function. The pathological features of AD include amyloid plaques, neurofibrillary tangles, chronic inflammation, vascular contributions and the loss of neural connections and cell death[1]. These features contribute to symptoms like confusion, difficulty speaking and severe memory loss. The disease itself can be diagnosed at all age levels; however, it is generally more common with individuals 65 years of age or older. Current treatments can help manage the symptoms, but neither a cure nor a cause for the disease has yet to be identified.  

### Biomarkers

A biomarker is defined as a characteristic that is objectively measured and evaluated as an indicator of normal biological processes, pathogenic processes, or pharmacologic responses to a therapeautic intervention[6]. They assist in understanding what happens inside a living body and assist doctors and researchers in diagnosing and monitoring diseases. For Alzheimer's Disease, measurements of the brain image scans, cerebrospinal fluid and blood are common biomarkers associated with the disease as well as other neurological diseases. Both the cerebrospinal fluid and blood biomarkers are involved with identifying the proteins, beta-amyloid 42 and tau, which revolve around the brain and its functions[5]. 

### miRNA in Relation to Alzheimer's Disease

MicroRNAs (miRNAs) are non-coding RNA molecules that are involved in the regulation of gene expression[9]. How miRNA regulates gene expression is by binding to Messenger RNA (mRNA) and preventing mRNA from producing protiens. Although the complete understanding of miRNA is still to be discovered, it is believed they play a crucial role in being able to control metablloic and cellular pathways[9]. The role of miRNA is important in the project, not only because our data is comprised of blood samples that contain miRNA information, but the ability of miRNA to be considered its own biomarker as well. Specifically, circulating miRNAs are believed to be an additional measurement aside from protein levels, that could lead to increased effectiveness in diagnosing AD in patients[10]. 

# Methods

The data utilized for this project is from SRA study SRP022043. This dataset includes 44 blood samples from Alzheimer’s Disease patients and 22 blood samples from control patients. We utilized the wget function to obtain the data and store it in our database. Afterwards, we ran FastQC to all of the files to ensure the quality of each file. We then ran cutadapt to remove the adapter sequences for the files, and then ran fastqc again to check the quality of each read sequence again. If the reads did not pass, we decided to remove them before running kallisto. Kallisto allowed us to generate the quantification of non-coding RNA of each sample. We then ran a python script to combine all of the individual tsv’s into a counts matrix that will be used for DESeq2, and a Wilcoxon Test. After getting the significant values from DESeq2, we then generated graphs and figures while also trying to identify various biomarkers that may be significant between Alzheimer’s patients and control patients (markers that have a difference in quantification between the two groups). We then researched more regarding the functions of those biomarkers and how it relates to Alzheimer’s.

# Results

### EDA
### Analysis


# Discussion

# Appendix

# Reference

[1] NIH Alzheimer’s Facts URL:
https://www.nia.nih.gov/health/alzheimers-disease-fact-sheet

[2] NIH Alzheimer Brain Impact URL:
https://www.nia.nih.gov/health/what-happens-brain-alzheimers-disease

[3] NCBI Biomarkers Definition URL:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3078627/

[4] Biomarker Types URL:
https://www.ncbi.nlm.nih.gov/books/NBK326791/

[5] NIH Biomarkers Definition URL: 
https://www.nia.nih.gov/health/biomarkers-dementia-detection-and-research 

[6] MicroRNA Definition URL:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3048316/

[7] miRNA and Alzheimer’s Disease URL: 
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053843/

[8] Main Article/Project Inspiration URL: 
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053778/

[9] Introduction to NGS: 
https://www.illumina.com/science/technology/next-generation-sequencing.html

[10] WGET Function Description URL:
https://www.gnu.org/software/wget/

[11] Andrews, S. Babraham Bioinformatics URL: 
https://www.bioinformatics.babraham.ac.uk/projects/fastqc/

[12] Martin, Marcel Bioinformatics in Action (2011) URL: 
http://journal.embnet.org/index.php/embnetjournal/article/view/200/479

[13] kallisto description URL:
https://pachterlab.github.io/kallisto/about

[14] Pandas read_csv capabilities URL:
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html 

[15] ensembl file type description URL:
https://uswest.ensembl.org/index.html

[16] DESeq2 Application description URL:
https://bioconductor.org/packages/release/bioc/html/DESeq2.html 

[17] Wilcoxon Test Description URL:
https://en.wikipedia.org/wiki/Wilcoxon_signed-rank_test 

18] miRNA-26B description URL:
https://www.ncbi.nlm.nih.gov/gene/407017 

[19] mirRNA-142 Brain Trauma URL:
https://pubmed.ncbi.nlm.nih.gov/32751105/

[20] mirRNA-182 description URL:
https://www.ncbi.nlm.nih.gov/gene/406958 

[21] miRNA-21 description URL:
https://en.wikipedia.org/wiki/MIRN21

[22] mirRNA-451B description URL:
https://www.ncbi.nlm.nih.gov/gene/100616273 

[23] mirRNA-142 description URL:
https://www.ncbi.nlm.nih.gov/gene/406934

[24] miRNA LET7 Gene Group URL:
https://www.genenames.org/data/genegroup/#!/group/1697 

[25] mirRNA-let-7b description URL:
https://www.ncbi.nlm.nih.gov/gene/406884 

[26] mirRNA-let-7f-1 description URL:
https://www.ncbi.nlm.nih.gov/gene/406888  

[27] mirRNA-let-7a-3 description URL:
https://www.ncbi.nlm.nih.gov/gene/406883 

[28] mirRNA-766 description URL:
https://www.ncbi.nlm.nih.gov/gene/768218 

[29] mirRNA-1248 description URL:
https://www.ncbi.nlm.nih.gov/gene/100302143




