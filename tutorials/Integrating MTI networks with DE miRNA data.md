## Tutorial: Integrating miRNA-target gene networks with transcriptomics data

This tutorial describes a network analysis workflow in Cytoscape for integrating miRNA expression data in a network of miRNA-target interactions (MTI).
Overall, the workflow will fo through the following points:

    - Loading a network of validated miRNA-target interactions (MTI) derived from public databases
    - Finding a set of differentially expressed miRNAs in a dataset of interest
    - Integration and visualization of experimental data in the MTI network
    - Integration of node annotations from public databases
    - Network filtering based on differential expression significance level and log-fold change
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
            Click on OK. This will import all of the data in the spreadsheet and associate each row with the corresponding node.
            You should be able to see this in the Table Panel (bottom right panel, below network view).

- recalling methods learned in this cytoscape tutorial on [**[Basic Data Visualization](https://cytoscape.org/cytoscape-tutorials/protocols/basic-data-visualization/#/) from [Cytoscape GitHub website](https://github.com/cytoscape/cytoscape-tutorials).**], modify your network view as follows:
            + map (miRNA) expression values to the Node Fill Color, so that nodes with low expression will be colored blue, while nodes with high expression will be colored red.
            + map significance for expression values to Node Border Width, so that nodes with significant changes will appear with a thicker border.
---

### Integration of node annotation from public databases

- download annotations on gene biotype obtained from Ensembl [BioMart](https://www.ensembl.org/biomart/martview/), and stored in file: [**nodes2type.txt**] (https://github.com/allegravia/tutorial-cytoscape/blob/main/data/nodes2type.txt)
- import the file as node table columns by using **File → Import → Table from File**.
            All of the defaults should be correct for importing the data, so just click on OK.
            This will import all of the data in the spreadsheet and associate each row with the corresponding node.
            Again, you should be able to see the new annotation column added in the spreadsheet shown in the Table Panel.
            
- map gene type to the Node Shape, so that miRNA nodes will appear with a diamond shape, protein-coding nodes with a rectangular shape, and lncRNAs as parallelograms. Finally, set hexagon as the default node shape.

---


### Network filtering based on differential expression significance level and log-fold change

---

### Network functional enrichment analysis on selected target nodes

---

### Basic Network analysis



