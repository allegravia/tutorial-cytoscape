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

![Let's start with a set of miRNAs deregulated in breast cancer](https://github.com/allegravia/tutorial-cytoscape/blob/main/data/images/volcano_plot.svg)
---

### Integration and visualization of experimental data in the MTI network

---

### Network filtering based on significance level from differential expression testing

---

### Network functional enrichment analysis on selected target nodes

---

### Basic Network analysis



