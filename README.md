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

### Pipeline

The data utilized for this project is from SRA study SRP022043. This dataset includs 44 blood samples from AD patients and 22 blood samples from control patients. We utilized the wget function to obtain the data and store it in our database (DSMLP). Afterwards, we ran fastqc to all of the files to ensure the quality of each file. We then ran cutadapt to remove the adapter sequences for the files, and then ran fastqc again to check the quality of each read sequence again. If the reads did not pass, we decided to remove them before running kallisto. Kallisto allowed us to generate the quantification of non-coding RNA of each sample. We then ran a python script to combine all of the individual tsv’s into a counts matrix that will be used for DESeq2. After running DESeq2, we plan to then generate graphs and figures while also trying to identify various biomarkers that may be significant between Alzheimer’s patients and control patients (markers that have a difference in quantification between the two groups). We hope to then research more regarding the functions of those biomarkers and how it relates to Alzheimer’s.

CITE SOFTWARE

### FastQC

Once we have access to the fastq.qz files, we were then able to run FastQC on our files to ensure that the quality of the data was in a matter that allowed us to analyze our date without the fear of the data's quality affecting the outcomes. We were able to determine the quality of each file by observing the analysis provided by FastQC such as sequence length distribution, which measures sequence fragment sizes, duplicate sequences, which counts for each sequence their degree of duplication, and contents found in adapters[12]. We ran FastQC twice: once prior to cutadapt and again after cutadapt was performed on the data. The necessity to perform FastQC twice comes down to whether implementing cutadapt within our pipeline is necessary to ensure quality data. 

### Cutadapt

During sequencing procedures, cutadapt allows one to remove adapter sequences found in RNA and DNA molecules[11]. This is an important tool within the pipeline as it allowed us to negate any unnecessary information from our data prior to additional analysis being performed on the data. How it does this is by removing adapter sequences attached to molecules as a result of the molecules length during sequencing processes[11]. Additional changes were made prior to our implementation of it as our data did not involve gene expression data. For the adapter sequence, we used the standard Illumina Sequence of "AGATCGGAAGAGC". 

### Kallisto

We utilized kallisto to generate our quantifications due to its speed with reliable accuracy. Kallisto utilizes a pseudo alignment system that is effective at getting accurate counts quickly. We obtained a reference file from the Ensembl reference transcriptomes. We used a homo sapiens non coding RNA file as the reference as miRNA is considered a ncRNA. For the kallisto settings, because our reads were single ended reads, we had to supply the length (in this case, 50 base pairs), and standard deviation (we used 10). We also decided to make the bootstrap length 8 and number of threads 8 (so that it runs faster). Kallisto generates a runinfo.json, abundance.tsv, and abundance.h5 file report. 

### For the Future

# Results

### EDA
### Analysis


# Discussion

# Appendix

# Reference

Main Article/Project Inspiration URL:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053778/

miRNA in Alzheimer's URL:
https://pubmed.ncbi.nlm.nih.gov/23889814/

Alzheimer's Biomarkers URL:
https://pubmed.ncbi.nlm.nih.gov/30051512/

[1] NIH Alzheimer’s Facts URL: https://www.nia.nih.gov/health/alzheimers-disease-fact-sheet 

[2] NIH Alzheimer Brain Impact URL: https://www.nia.nih.gov/health/what-happens-brain-alzheimers-disease 

[3] NIAGADS Data (Main) URL: 
https://www.niagads.org/datasets/ng00038 

[4] ArrayExpress Data (Backup) URL:
https://www.ebi.ac.uk/arrayexpress/experiments/E-GEOD-53697/?keywords=alzheimer%27s+&organism=Homo+sapiens&exptype%5B%5D=%22rna+assay%22&exptype%5B%5D=&array= 

[5] NIH Biomarkers Definition URL:
https://www.nia.nih.gov/health/biomarkers-dementia-detection-and-research#:~:text=The%20most%20widely%20used%20CSF,tau%20tangles%20in%20the%20brain)

[6] NCBI Biomarkers Definition URL:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3078627/

[7] NCBI Project Inspiration URL
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053778/

[8] Biomarker Types URL:
https://www.ncbi.nlm.nih.gov/books/NBK326791/

[9] MicroRNA Definition:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3048316/

[10] miRNA and Alzheimer’s Disease:
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053843/

[11] Martin, Marcel Bioinformatics in Action (2011) URL:
http://journal.embnet.org/index.php/embnetjournal/article/view/200/479

[12] Andrews, S. Babraham Bioinformatics URL: 
https://www.bioinformatics.babraham.ac.uk/projects/fastqc/



