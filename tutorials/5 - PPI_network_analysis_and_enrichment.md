# Tutorial on protein network interaction analysis and functional enrichment analysis

### Target audience
Cytoscape novices / beginners

### Contents

1.	Introduction
2.	Learning outcomes
3.	Requirements 
4.	Cytoscape 
5.	Tutorial 

### Introduction
In this tutorial, we will use a practical example to show how to use the popular open source tool Cytoscape to both upload and to build (through the PSICQUIC client to access several protein interaction repositories at the same time) a PPI network and explore it in order to detect topological properties, find topological clusters, and use the BINGO app to **perform GO enrichment analysis of the network**. 

### Learning outcomes
By the end of this tutorial the learner should be able to:
-	Upload a PPI network in Cytoscape
-	Build the same PPI network from Cytoscape using PSICQUIC
-	Save Cytoscape sessions
-	Filter out interactions with low score
-	Select nodes and edges
-	Download and use the BINGO app 

### Requirements
In order to carry out this tutorial, you need:
1.	Cytoscape version 3.10.1 or more (downloadable from [www.cytoscape.org](www.cytoscape.org))
2.	A list of proteins you want to build a network from (e.g. parkinson_uniprot_list.txt)
3.	The corresponding network table (file Parkinson_MITAB2.7.txt)
4.	BINGO app installed in Cytoscape

### Cytoscape 
[https://cytoscape.org](https://cytoscape.org)
Cytoscape is an open source software platform for visualising molecular interaction networks and biological pathways and integrating these networks with annotations, gene expression profiles and other state data. Although Cytoscape was originally designed for biological research, now it is a general platform for complex network analysis and visualisation. Cytoscape core distribution provides a basic set of features for data integration, analysis, and visualisation. Additional features are available as **Apps** (formerly called Plugins). **Apps** are available for network and molecular profiling analyses, new layouts, additional file format support, scripting, and connection with databases. They may be developed by anyone using the Cytoscape open API based on Java™ technology and App community development is encouraged. Most of the Apps are freely available from [Cytoscape App Store](http://apps.cytoscape.org/).

## Tutorial

### Dataset(s)
The dataset used for the guided analysis example presented in this tutorial consists of a set of 15 proteins involved in Parkinson disease. 
More specifically, our goal will be to find if there is experimental evidence for interactions within the proteins linked to the Parkinson diseases. To this end, we selected the genes derived from the Parkinson pathway curated in [SIGNOR database](https://signor.uniroma2.it/pathway_browser.php?organism=&pathway_list=SIGNOR-PD&x=15&y=12). From the visualisation page, it is possible to download the pathway relations and to select the genes involved in this pathway and to create a dataset that we will use to generate the interaction pathway.
With this selected dataset of 15 proteins involved in Parkinson disease, we can generated an interaction network in the form of a tab-separated table (Parkinson_MITAB2.7.txt).
This tab-separated table can be generated either directly from the PSICQUIC web page (http://www.ebi.ac.uk/Tools/webservices/psicquic/view/) and then this network can be loaded in Cytoscape or we can generate the interaction network between the Parkinson-linked proteins using directly the PSICQUIC client of Cytoscape.






