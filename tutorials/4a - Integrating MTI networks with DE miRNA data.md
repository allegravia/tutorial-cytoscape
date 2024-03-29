## Tutorial: Integrating miRNA-target gene networks with transcriptomics data

This tutorial describes a network analysis workflow in Cytoscape for integrating miRNA expression data in a network of miRNA-target interactions (MTI).
Overall, the workflow will go through the following points:

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

In this tutorial, we will use miRNA expression data obtained by high-throughput sequencing technology in breast cancer samples and normal tissues from ![The Cancer Genome Atlas (TCGA) program](https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga).

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

     - map (miRNA) log fold change in breast cancer to the **Node Fill Color**, so that nodes with lower expression in breast cancer compared to normal samples will be colored blue, while nodes with higher cancer expression will be colored red.
     - map significance for expression values to **Node Border Width**, so that nodes with significant changes will appear with a thicker border.
---

### Integration of node annotation from public databases

- download annotations on gene biotype obtained from Ensembl [BioMart](https://www.ensembl.org/biomart/martview/), and stored in file: [**nodes2type.txt**] (https://github.com/allegravia/tutorial-cytoscape/blob/main/data/nodes2type.txt)
- import the file as node table columns by using **File → Import → Table from File**.
            All of the defaults should be correct for importing the data, so just click on OK.
            This will import all of the data in the spreadsheet and associate each row with the corresponding node.
            Again, you should be able to see the new annotation column added in the spreadsheet shown in the Table Panel.
            
- map gene type to the Node Shape, so that miRNA nodes (that is, *miRNA_name* gene type!) will appear with a diamond shape, protein-coding nodes with a rectangular shape, and lncRNAs as parallelograms. Finally, set hexagon as the default node shape.

---

### Network filtering based on differential expression significance level and log-fold change

Now we will use information gained from expression data analysis, such as significance observed in the differential expression test and log fold-change of expression level in breast cancer samples compared to normal samples, to select a subnetwork of miRNA-target interactions likely relevant to investigate disregulated pathways in breast cancer disease.

To this end, use the **Filter** tab from the Control Panel (left menu) to find the most significant overall expression changes, as follows:

    - Open the Filter tab and click on the + button to add a new condition. In this case we’re going to add a Column Filter. Select the "BH.adjusted_pvalues" column and set the values to be between 0.0 and 0.049 (in other words, select BH adjusted p-values < 0.05). This will select all miRNAs (only miRNAs in this network have associated expression data!) that are significantly deregulated in breast cancer, based on the choosen significance threshold. By applying this filter, you will read (bottom of FIlter panel) that 406 nodes have been selected, and you will see selected nodes highlighted in yellow in the network view.
    
    - Select the first neighbors of selected miRNA nodes by using **Select → Nodes → First neighbors of selected nodes → Directed outgoing**. This will select all target genes of the subsets of differentially expressed miRNAs that we just selected based on test p-value.
    
    - Create a separate subnetwork from these selected nodes (ie. DE miRNAs and their experimentally validated target genes) by using **File → New Network  → from selected nodes, all edges**. This will create a new network in the left panel of 2783 nodes and 8002 edges. Rename this sub-network "sig_miRNAs".
    
Now, your turn: 
    - create a sub-sub-network from the *topDEmiRNAs* network by modifying the above filtering procedure to now select only miRNAs whose values of log-fold-change are at least 1 (or -1), or more extreme. Create a new network also including direct target genes of the selected miRNAs. (Hint: design your filter based on appropriate values of the "log2FC"). Name this sub-sub-network *sig_and_topDEmiRNAs*.
    
---

### Network functional enrichment analysis on selected target nodes

Let's explore which biological processes are mostly affected in breast cancer deregulation based on functional enrichment analysis of genes targeted by  top deregulated miRNAs. There are many tools available in Cytoscape to perform functional enrichment. Here we will use for simplicity the built-in functional enrichment available from the *BINGO* App:
- Select protein-coding nodes by using again the Filter menu and setting a filter on the *gene_type* column to be "protein_coding"
- Launch functional enrichment analysis by using: **Apps → BINGO** (→ set cluster name - this will be used to save results on your pc, directory to save the results of functional enrichment analysis, and change organism to Homo sapiens. THen click on *Start BINGO*).

**which biological processes would you say are mostly affected in breast cancer pathogenesis based on functional enrichment analysis?**


---

### Basic Network analysis

Finally, let's analyse the last sub-network (*sig_and_topDEmiRNAs*) to identify hub nodes, both miRNA and target gene nodes, in this network. We can do that as follows:

- Deselect all nodes by using **Select → Nodes → Deselect All Nodes**. This is to ensure that we run the network analysis on all nodes and components.
- RUn the network analysis by using **Tools → Analyze network** (→ check the option: *Analyze as directed graph* from the pop-up window).


**which miRNAs are the top 5 hubs in this networks?**

**which column would you look at to find out top co-regulated target genes in this networks?**

**Is this a scale-free network? How can you tell?**

---

