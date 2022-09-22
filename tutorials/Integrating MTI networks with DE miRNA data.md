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

- launch Cytoscape
- download network file: 
- import the file to create a network using File → Import → Network from File
    This will bring up the Import Network From Table dialog.
        Click on Select None to disable all columns.
        Click only on the GeneName column and set this column as the Source Node column (green circle).
        Click OK. You’ll see a warning about no edges, but that’s OK. This will create a grid of 1500 unconnected nodes, where each node represents a gene.



---

### Finding a set of differentially expressed miRNAs in a dataset of interest

![Let's start with a set of miRNAs deregulated in breast cancer](https://github.com/allegravia/tutorial-cytoscape/blob/main/data/volcano_plot.svg)
---

### Integration and visualization of experimental data in the MTI network

---

### Network filtering based on significance level from differential expression testing

---

### Network functional enrichment analysis on selected target nodes

---

### Basic Network analysis



