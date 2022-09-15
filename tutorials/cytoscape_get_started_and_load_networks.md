# Getting started, exploring network data and loading networks

This tutorial is based on the Cytoscape [Loading Network Tutorial](https://cytoscape.org/cytoscape-tutorials/protocols/loading-networks/#/)

## Table of content
1. Install and launch Cytoscape
2. High-level tour of the features of Cytoscape
3. Cytoscape core concepts
4. What types of analyses can we do with Cytoscape?
5. Network data types, file formats, file content
6. Loading networks to Cytoscape

## Getting started
1. Before we start, install and launch the latest version of [Cytoscape](https://cytoscape.org/).
2. Let's start with a high-level tour of the features of Cytoscape: [Tour of Cytoscape](https://cytoscape.org/cytoscape-tutorials/protocols/tour-of-cytoscape/#/)
3. Then have a look at the cytoscape core concepts: [Introduction to Cytoscape](https://cytoscape.org/cytoscape-tutorials/presentations/modules/intro-cytoscape/index.html#/)
4. What type of analyses can we do with Cytoscape? <br> 
Here you will find a list of possible analyses you can do in biology using Cytoscape: [network analysis](https://github.com/cytoscape/cytoscape-tutorials/wiki#network-analysis)
5. 

## Network data types
#### Cytoscape can import network data from:
- Files (or URLs)
- Excel, TSV, CSV
- XGMML: eXtensible Graph Markup and Modelling Language
- SBML: Systems Biology Markup Language
- BioPAX
- PSI-MI
- SIF: Simple Interaction Format
- GML: Graph Markup Language
- ... and others depending on loaded Apps

- Public repositories:
  - PSICQUIC
  - STRING (via the stringApp)
  - IntAct (via the IntActApp)
  - Reactome (via the ReactomeFI app)
  - WikiPathways (via the WikiPathways app)
  - Pathway Commons (via the CyPath2 app)
  - NDEx
- Automation:
  - Command line scripts
  - CyREST via R, Python, etc
#### Cytoscape can load tables from:
- Files (or URLs)
  - Excel, TSV, CSV
- Public repositories
  - BioMart
Automation:
- Command line scripts
- CyREST via R, Python, etc

## Loading networks and Tables
- [Loading Networks](https://cytoscape.org/cytoscape-tutorials/protocols/loading-networks/#/) <br>
This tutorial describes the details of importing an existing network and applying a layout.
- [Importing Data From Tables](https://cytoscape.org/cytoscape-tutorials/protocols/importing-data-from-tables/#/)<br>
This tutorial describes how to import expression data from a spreadsheet, and how to link it to already loaded networks.
- [Importing Network From Table](https://cytoscape.org/cytoscape-tutorials/protocols/importing-network-from-table/#/)<br>
This tutorial describes how to import a network from tabular data.
