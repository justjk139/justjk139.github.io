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

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/methods_flowchart.png?raw=true)

The data utilized for this project is from SRA study SRP022043. This dataset includes 44 blood samples from Alzheimer’s Disease patients and 22 blood samples from control patients. We utilized the wget function to obtain the data and store it in our database. Afterwards, we ran FastQC to all of the files to ensure the quality of each file. We then ran cutadapt to remove the adapter sequences for the files, and then ran fastqc again to check the quality of each read sequence again. If the reads did not pass, we decided to remove them before running kallisto. Kallisto allowed us to generate the quantification of non-coding RNA of each sample. We then ran a python script to combine all of the individual tsv’s into a counts matrix that will be used for DESeq2, and a Wilcoxon Test. After getting the significant values from DESeq2, we then generated graphs and figures while also trying to identify various biomarkers that may be significant between Alzheimer’s patients and control patients (markers that have a difference in quantification between the two groups). We then researched more regarding the functions of those biomarkers and how it relates to Alzheimer’s.

# Results

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/figure_3.png?raw=true)
Figure 1. DESeq2 Volcano plot of p_values

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/figure_4.png?raw=true)
Figure 2. Wilcox Volcano Plot of p_values

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/figure_5.png?raw=true)
Figure 3. DESeq Boxplot of most upregulated and downregulated miRNA

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/figure_6.png?raw=true)
Figure 4. Wilcox Test Boxplot of most upregulated and downregulated miRNA

![alt text](https://github.com/justjk139/alzheimers_gene_analysis/blob/main/references/ENST_conversions.png?raw=true)
Figure 5. The nine miRNA values that overlapped between our DESeq2 output, our Wilcoxon output, and the original study. ENST, miRNA label and HSA value for each miRNA is present.

### EDA
### Analysis


# Discussion

As seen on Figure 7, the control counts are nearly 4 times as large as the AD counts. This miRNA is known for gene silencing and a lack of that gene silencing could be a factor within AD. For figure 8, counts in AD are more than 10 times as much, leading us to conclude that it is possible that the lack of activation of mRNA upon binding of cap-binding complexes could be another factor. In Figure 9, there were no counts of miR6882 in Alzheimer Disease, while there are counts in the control. Nonexistent counts in this miRNA leads us to believe that patients are more likely to be diagnosed with AD. In Figure 10 we determined inconclusive findings when looking at the counts distribution for miRNA 26B!

Within our analysis, we were able to find 11 miRNA values that overlapped between the two tests we performed on our data. We went ahead and researched each miRNA value to obtain additional information about them and whether they had any direct association to AD. Out of the 11 entries, we were only able to determine miRNA 26B to have any direct association with AD based on its positive regulation of tau-protein kinase activity[18]. The remaining values were instead closely related to various forms of cancer such as carcinoma. Some common processes seen through each miRNA value include gene silencing and regulation processes that involved apoptosis. miRNA 6882 was the only miRNA value that was not able to find sufficient information to draw any conclusions relating to the miRNA or to the other 11 values. Even though a lot of the miRNAs may not be directly related to AD, we believe an indirect influence on gene expression could still exist. For example, miRNA 142, one of the 11 values we further investigated, had functions that have been linked to severe brain injuries prediction in patients[19]. It could be possible to utilize this miRNA to detect changes within AD patient brains. Or, miRNA 182 is positively related to apoptosis. It could be that there could be an overexpression of this miRNA in AD patients[20]. 

Our first overlapped miRNA value is miRNA 21 (hsa-mir-21, MIR21). It plays a crucial role in many biological functions and diseases such as cancer and cardiovascular disease. MIR21 also regulates various immunological and developmental processes[21].

miRNA 451B or MIR451B is located on the chromosome 17q11.2. Similar to MIR21, MIR451B is commonly associated with human cancers but is also responsible as a gene silencer which refers to the downregulation of gene expression by miRNAs[22]. 

miRNA 142 or MIR142, has a gene ontology that associates this particular miRNAs roles to gene silencing, negative regulation of inflammatory responses, positive regulation of neuroinflammatory responses, and even responses to tumor necrosis factors[23]. Variations of MIR142 have also been linked to predicting severe brain injury (SBI) in patients. 

miRNA 26B or MIR26B, attributed to processes that include gene silencing by an miRNA, negative regulation of defense response to viruses, positive regulation of apoptotic signaling pathways (apoptotic refers to cell death), as well as positive regulation of tau-protein kinase activity[18]. Tau-protein kinase activity is a feature of AD progression for those affected by the disease

miRNA 182 or MIR182, is similar to MIR26B in that it also has a positive regulation response to apoptotic processes. Additional roles include gene silencing, negative regulation of epithelial cell apoptotic processes and positive regulation of gene expression[20].  It has a chromosome location at 7q32.2 that is most commonly associated with the most common type of cancer, carcinoma.

miRNA let-7a-3 (MIR let-7a-3), miRNA let-7b (MIR let-7B), and miRNA let-7f-1 (MIR let-7f-1) are part of the MIRLet7 family[24]. MIR let-7a-3 and MIR let-7b both share the chromosome location 22q13.31 while MIR let-7f-1 is located at 9q22.32. MIR let-7b has processes such as negative regulation of hydrogen peroxide-mediated programmed cell death, and positive regulation of angiogenesis[25]. MIR let-7f-1 is associated with negative regulation of apoptotic processes and the negative regulation of protein kinase protein B[26]. All three are associated with gene silencing properties.

miRNA 766 (MIR766) has pathways such as gene silencing and cellular response to tumor necrosis factor[28]. Research indicates MIR766 is closely related to other cancer related miRNAs.

miRNA 1248 (MIR1248) has pathways such as viral mRNA translation and the transportation of the SLBP independent mature mRNA[29]. It is believed that RNA processing is also a standard processes completed by MIR1248.

miRNA 6882 (MIR6882) 

Furthermore, we realized that the paper utilized a different differential expression method compared to what we wanted to use. We wanted to use DESeq2 as we have previously used it before, and also factors in the entire dataset that is given. The original paper used a Wilcoxon-Mann-Whitney test, a non parametric model that only looked at a specific miRNA. We felt that using DESeq2 is advantageous as it considers all the different miRNAs and does not just look at an individual miRNA. This takes into consideration all of the data, which provides a more accurate result.

Part of the limitations concerning this project include the availability of sufficient data. While the research paper that influenced our project provided us publicly with the 70 patient sample data, it was mentioned that additional entry points were utilized. This prevented us from being able to properly compare our results during various stages of the project due this difference. For example, if we had used the additional data, we may have been able to reproduce the significant results by solely running DESeq2. How this affected our overall outcome can be seen when we were only able to collect 11 miRNA values that overlapped out of a sample of over 1000 miRNA values. There was also a mention of several cognition tests, including Alzheimer Disease Assessment Scale-cognitive subscale (ADAS-Cog), Clinical Dementia Rating (CDR), Wechsler Memory Scale, and Mini-Mental State Exam (MMSE). None of the results of any of these tests were publicly available for us, which could have inhibited our results and findings. We could not have utilized these mental tests to further our results or used them as additional factors within our analysis. 

Overall, we realize how complex AD is and the need for more research to be done in order to find a cure or definitive detection of this disease. miRNAs and other biomarkers can be a place to start, but there are also so many other factors that can contribute to and need to be examined more. However, we hope that the research and findings that we have done could be a starting point for future research, especially if it involves utilizing blood based samples similar to our study. Considering the promising outlook for using blood based data in the fight against AD, we hope that there could be more studies done on miRNAs and its functions, leading to more possible relationships/correlations between that and AD. If we were to do further investigation, we would like to have more information on the cognitive tests previously mentioned and how they could supplement the data further. Obtaining a much larger data sample size would also be something we would want to do. But, we hope that our current findings could help contribute to existing research on AD pathways or may lead to the beginning of novel research on this disease.


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




