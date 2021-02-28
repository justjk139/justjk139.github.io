## Website URL: 
https://justjk139.github.io

# Abstract

Alzheimer’s Disease (AD) is an irreversible, progressive neurodegenerative disorder that slowly destroys a person's cognitive and physical abilities. The cause of AD is unclear, but is believed to be a combination of genetic, environmental and lifestyle factors. Because the only way to definitely diagnose AD is post mortem, the search for earlier definitive detection is crucial. One way of doing this is by analyzing blood samples to detect biomarkers and microRNAs. A biomarker is defined as a characteristic that is objectively measured as an indicator of normal biological processes, while microRNAs (miRNAs) are non-coding RNA molecules that are involved in the regulation of gene expression. Recent studies show miRNAs and biomarkers as possible tools for AD diagnosis, thus, leading us to analyze blood miRNA data for our study. Utilizing influences from various other studies, we examined 70 blood samples of AD and controlled patients through our custom genetics pipeline in hopes of a breakthrough in understanding the pathology of the disease. We then implemented two different statistical tests, a non-parametric hypothesis test (Wilcoxon-Mann-Whitney Test) and a parametric hypothesis t-test (DESeq2). From these tests we were able to isolate nine significant samples to perform further analysis on its relationship and effect to AD.

# Introduction

### Background

Alzheimer’s is an age-related neurodegenerative disease that currently affects more than 5.5 million Americans and is considered the 6th leading cause of death in the United States[1]. It is an irreversible disease that causes declines in both mental and physical abilities as a result of rapidly declining brain function. The pathological features of Alzheimer’s associated with the loss in proper brain function include amyloid plaques, neurofibrillary tangles, chronic inflammation, vascular contributions and the loss of neural connections and cell death[1]. As a result, Alzheimer’s patients undergo symptoms that generally include confusion, difficulty speaking and severe memory loss. The disease itself can be diagnosed at all age levels; however, it is generally more common with individuals 65 years of age or older. At this time, current treatments can help manage symptoms, but neither a cure nor a cause for the disease has been identified, despite the ongoing research. What is clear, however, is that genetics, the environment, an individuals lifestyle, and age, are factors for an Alzheimer’s diagnosis. 

Drawing inspiration from similar projects[7], we set out to elucidate biomarkers that exist for Alzheimer's Disease (AD) by observing blood miRNA sample data from 44 patients diagnosed with Alzheimer's and a separate control group consisting of 22 patients. There are currently several biomarkers for AD that have been identified to help diagnose the diease[7]. With this project we make the attempt isolate those same biomarkers, such as miRNA, and describe in detail their impact in the biological processes that of AD, within the constraints of the data available for this project. In the end, we believe new information about the disease could be discovered to aid in the development of new possible treatments and maybe even contribute in identifying the exact causes of the disease. The intentions of the project are to supplement the world's current understanding of the disease in order to help the millions that are currently affected.

### Biomarkers

There are currently several different types of biomarkers that have been defined for various context uses after a need for establishing a clear and unambigous translation for biomarkers within the medical and scientific community was required[8]. According to the National Institutes of Health Biomarkers Definitions Working Group, a biomarker is defined as a characteristic that is objectively measured and evaluated as an indicator of normal biological processes, pathogenic processes, or pharmacologic responses to a therapeautic intervention[6]. Observing such biomarkers assist in understanding what is going on inside a living body and can help doctors and researchers in diagnosing diseases as well as monitor how a persons conditions change over time. Examples of these biomarkers include Pharmacodynamic or Response Biomarkers, which is a biomarker that shows whether or not an individual has a biological response after exposure to medical or environmental agents, and Prognastic Biomarkers, which are biomarkers that indicate the progression or recurrence of a particular disease or condition[8]. For the purposes of this project, Diagnostic Biomarkers, which are used to detect the presence of a particular disease or condition, would be what we are most interested in, however, we would not limit ourselves to just observing one particular biomarker. 

When it comes to Alzheimer's specific biomarkers, the most common biomakers derive from taking measurements of the brain, from its function to its size. These measurements can be taken from brain imaging technology such as Computerized Topography (CT) scans and from Magnetic Resonance Imaging (MRI) scans[5]. Cerebrospinal Fluid and blood are additional biomarkers associated with AD and other similar dementias as well. Both are involved with identifying the proteins that are produced that revolve around the brain and its functions such as beta-amyloid 42 and tau[5]. Due the serious implications AD has to the brain and overall brain function, being able to identify symptoms or signs of the disease early on in the diagnostic process is crucial[5]. This is in large part on why biomarkers are a useful tool in the fight against the disease as it allows medical professionals to monitor brain changes of a patient that they themselves may not realize. 

### miRNA in Relation to Alzheimer's Disease

MicroRNAs (miRNAs) are non-coding RNA molecules that are involved in the regulation of gene expression[9]. How miRNA regulates gene expression is by binding to Messenger RNA (mRNA) and preventing mRNA from producing protiens. It is believed that over 30 percent of protein coding genes are regulated by miRNAs and that it counts for roughly 5 percent of the entire human genome[9]. miRNA themselves are 19-20 nucleotides in length and have a 3"-hydroxyl and 5"-phosphate end and although the complete understanding of miRNA is still to be discovered, it is believed they play a crucial role in being able to control metablloic and cellular pathways[9]. 

The role of miRNA is important in the project, not only because our data is comprised of blood samples that contain miRNA information, but the ability of miRNA to be considered its own biomarker as well. Specifically, circulating miRNAs are believed to be an additional measurement aside from protein levels, that could lead to increased effectiveness in diagnosing AD in patients[10]. Looking at miRNA as biomarkers would allow researchers to not only take note of physical observations provided by brain images, but observations on a gene expression level more so than just the proteins involved with AD, but the biological processes that lead the creation of such proteins in the first place. Within the context of the project, being able to analyze the road map that leads to AD specific pathology is a goal for the team.

# Methods

### Pipeline

The data utilized for this project is from SRA study SRP022043. This dataset includs 44 blood samples from Alzheimer’s Disease patients and 22 blood samples from control patients. We utilized the wget function to obtain the data and store it in our database. Afterwards, we ran fastqc to all of the files to ensure the quality of each file. We then ran cutadapt to remove the adapter sequences for the files, and then ran fastqc again to check the quality of each read sequence again. If the reads did not pass, we decided to remove them before running kallisto. Kallisto allowed us to generate the quantification of non-coding RNA of each sample. We then ran a python script to combine all of the individual tsv’s into a counts matrix that will be used for DESeq2. After running DESeq2, we plan to then generate graphs and figures while also trying to identify various biomarkers that may be significant between Alzheimer’s patients and control patients (markers that have a difference in quantification between the two groups). We hope to then research more regarding the functions of those biomarkers and how it relates to Alzheimer’s.

CITE SOFTWARE

### FastQC

Once we have access to the fastq.qz files, we were then able to run FastQC on our files to ensure that the quality of the data was in a matter that allowed us to analyze our date without the fear of the data's quality affecting the outcomes. Several analyses are performed during a FastQC implementation and we were able to determine the quality of each file by looking at the provided analysis such as sequence length distribution, which measures sequence fragment sizes, duplicate sequences, which counts for each sequence their degree of duplication, and contents found in adapters[12]. Similar to our replication project, we ran FastQC twice: once prior to cutadapt and again after cutadapt was performed on the data. The necessity to perform FastQC twice comes down to whether implementing cutadapt within our pipeline is necessary to ensure quality data. If its found that the quality of the data did not have any significant differences made after implmenting cutadapt, then it may not be necessary to include it as part of the final pipeline process.

### Cutadapt

Similar to the project implementation from last quarter, we used cutadapt as part of our project pipeline. During sequencing procedures, cutadapt allows one to remove adapter sequences found in RNA and DNA molecules[11]. This is an important tool within the pipeline as it allowed us to negate any unnecessary information from our data prior to additional analysis being performed on the data. How it does this is by removing adapter sequences attached to molecules as a result of the molecules length during sequencing processes[11]. Additional changes were made prior to our implementation of it as our data did not involve gene expression data. For the adapter sequence, we used the standard Illumina Sequence of "AGATCGGAAGAGC". 

### Kallisto

We utilized kallisto to generate our quantifications due to its speed with reliable accuracy. Kallisto utilizes a pseudo alignment system that is effective at getting accurate counts quickly. We obtained a reference file from the Ensembl reference transcriptomes. We used a homo sapiens non coding RNA file as the reference as miRNA is considered a ncRNA. For the kallisto settings, because our reads were single ended reads, we had to supply the length (in this case, 50 base pairs), and standard deviation (we used 10). We also decided to make the bootstrap length 8 and number of threads 8 (so that it runs faster). Kallisto generates a runinfo.json, abundance.tsv, and abundance.h5 file report. 

### For the Future

# Results

### Patient Analysis
### EDA
### Analysis


# Discussion

# Appendix

# Reference
