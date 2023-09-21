# Getting started, exploring network data and loading networks

This tutorial is based on [Cytoscape Tutorials](https://cytoscape.org/cytoscape-tutorials/)

## Table of content
1. Install and launch Cytoscape
2. Cytoscape core concepts
3. High-level tour of the features of Cytoscape
4. What types of analyses can we do with Cytoscape?
5. Network data types, file formats, file content
6. Loading networks to Cytoscape

## Getting started
1. Before we start, install and launch the latest version of [Cytoscape](https://cytoscape.org/).
2. Let's have a look at the cytoscape core concepts: [Introduction to Cytoscape](https://cytoscape.org/cytoscape-tutorials/presentations/modules/intro-cytoscape/index.html#/)
3. Then make a high-level tour of the features of Cytoscape: [Tour of Cytoscape](https://cytoscape.org/cytoscape-tutorials/protocols/tour-of-cytoscape/#/)
4. What types of analyses can we do with Cytoscape? <br> 
Here you will find a list of possible analyses you can do in biology using Cytoscape: [network analysis](https://github.com/cytoscape/cytoscape-tutorials/wiki#network-analysis)

## Supported Network File Formats
Cytoscape can read network files written in several formats.
To learn more about supported formats, see the [Cytoscape Manual](https://manual.cytoscape.org/en/stable/Supported_Network_File_Formats.html)
<br>
In particular, Cytoscape can import network data from:
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
Moreover, Cytoscape can load tables from:
- Files (or URLs)
  - Excel, TSV, CSV
- Public repositories
  - BioMart
- Automation:
  - Command line scripts
  - CyREST via R, Python, etc


#### SIF format
SIF is a simple interaction format consisting of three columns of data: source, interaction and target. 
To learn more about the SIF format, see the Cytoscape manual.

Download galFiltered.sif. This sample file is also included with your Cytoscape installation, in the sampleData folder.
Load the network via ``` File → Import → Network from File....```
To see the whole network, select ``` View → Fit Content```.

## Loading networks and Tables
- [Loading Network Tutorial](https://cytoscape.org/cytoscape-tutorials/protocols/loading-networks/#/)
- [Loading Networks](https://cytoscape.org/cytoscape-tutorials/protocols/loading-networks/#/) <br>
This tutorial describes the details of importing an existing network and applying a layout.
- [Importing Data From Tables](https://cytoscape.org/cytoscape-tutorials/protocols/importing-data-from-tables/#/)<br>
This tutorial describes how to import expression data from a spreadsheet, and how to link it to already loaded networks.
- [Importing Network From Table](https://cytoscape.org/cytoscape-tutorials/protocols/importing-network-from-table/#/)<br>
This tutorial describes how to import a network from tabular data.

#### Loading SIF files:
Download galFiltered.sif. This sample file is also included with your Cytoscape installation, in the sampleData folder.
Load the network via ``` File → Import → Network from File....```
To see the whole network, select ``` View → Fit Content```.

#### Loading XGMML files:
XGMML is an XML format and can includes node and edge attributes as well as visual style properties. To learn more about the XGMML format, see the Cytoscape manual.

```Go to File → Import → Network from URL.... ``` and enter the following ```URL: https://raw.githubusercontent.com/cytoscape/cytoscape-tutorials/gh-pages/protocols/data/BasicDataVizDemo.xgmml```
This is the same network as in the previous step, but with node fill color corresponding to expression values.
