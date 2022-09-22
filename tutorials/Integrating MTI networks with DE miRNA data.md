## Tutorial: Integrating miRNA-target gene networks with transcriptomics data

This tutorial describes a network analysis workflow in Cytoscape for integrating miRNA expression data in a network of miRNA-target interactions (MTI).
Overall, the workflow will fo through the following points:

    - Loading a network of validated miRNA-target interactions (MTI) derived from public databases
    - Finding a set of differentially expressed miRNAs in a dataset of interest
    - Integration and visualization of experimental data in the MTI network
    - Network filtering based on significance level from test of differential expression
    - Network functional enrichment analysis on selected target nodes
    - Basic Network analysis

---

### Loading a network of validated miRNA-target interactions (MTI) derived from public databases

Experimentally validated miRNA-target interactions were downloaded from [miRTarBase](https://mirtarbase.cuhk.edu.cn/) (release 8.0), and then filtered from bash command line to remove *weak* interactions (**--> how would you do that?**).  

![Sample lines from file of human miRNA-target data obtained from miRTarbase, release 8.0](https://github.com/allegravia/tutorial-cytoscape/blob/main/data/images/f.png)


- launch Cytoscape
- download network file: [**hsa_MTI__strong.csv**] (https://github.com/allegravia/tutorial-cytoscape/blob/main/data/hsa_MTI__strong.csv)
- import the file to create a network using **File → Import → Network from File** (This will bring up the Import Network From Table dialog).
        Click on Select None to disable all columns.
        Click on the *miRNA* column and set this column as the *Source Node* column (green circle).
        Click on the *Target gene* column and set this column as the *Target Node* column (red target).
        Click on the *Experiments* column and set this column as the *Interaction type* column (purple arrow).
        Click OK.This will create a network of 3589 nodes and 11170 edges, where each node represents either a miRNA or a target gene.
        

---

### Finding a set of differentially expressed miRNAs in a dataset of interest

In this tutorial, we will use miRNA expression data obtained by high-throughput sequencing technology in breast cancer samples and normal tissues from The Cancer Genome Atlas (TCGA) project.

Pre-processed data (Reads per million mapped reads, or RPM-normalized read counts across samples) was obtained by using the R/Bioconductor package [*curatedTCGAData*](https://bioconductor.org/packages/release/data/experiment/vignettes/curatedTCGAData/inst/doc/curatedTCGAData.html). **Important: expression data are summarized here at the hairpin level!**, thus one will need mapping of hairpins to mature miRNAs to integrate expression data with the above MTI network (**--> how would you do that?**).  

After running in R a differential expression analysis, over 400 miRNA precursors are found to be deregulated in breast cancer compared to normal tissues.

![Let's start with a set of miRNAs deregulated in breast cancer](https://github.com/allegravia/tutorial-cytoscape/blob/main/data/images/volcano_plot.svg)
---

### Integration and visualization of experimental data in the MTI network

- download results from the analysis of miRNA differential expression in breast cancer, that is stored in file: [**TCGA_BRCA_mirs__DEoutput__wMiRBaseAnnotations.txt**] (https://github.com/allegravia/tutorial-cytoscape/blob/main/data/TCGA_BRCA_mirs__DEoutput__wMiRBaseAnnotations.txt)
- import the file as node table columns by using **File → Import → Table from File** (This will bring up the Import Columns From Table dialog).
            Click on the *miRNA.name* column and set this column as the *key* column (this column will be used to map annotations to network nodes).
            It turns out that all of the defaults are correct for just importing the data, so click on OK.
            This will import all of the data in the spreadsheet and associate each row with the corresponding node.
            You should be able to see this in the Table Panel (bottom right panel, below network view).



We’ll use the Select tab in the Control Panel to find the significant overall expression changes.

    Open the Select tab and click on the + button to add a new condition. In this case we’re going to add a Column Filter. Select the "Mean log2FC" column and set the values to be between -5 and -1. This will select all genes that are significantly underexpressed on average, across all samples (only one gene should be selected).
    Repeat the same process as above, but set the values to be between 1 and 5. You’ll also need to change the type of match (at the top of the panel) to Match any (OR). No additional genes will be selected in this case (but this approach will be reused later).

Only one gene shows significant average expression changes across all samples, RPS4Y1, a ribosomal protein that has been shown to be linked to glioblastoma, but it’s still a relatively unsatisfying result that only a single protein changes expression in glioblastoma patients. A closer examination might be in order...

---

### Network filtering based on significance level from differential expression testing

---

### Network functional enrichment analysis on selected target nodes

---

### Basic Network analysis



