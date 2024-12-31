# A Graph-Based Analysis of Gene Activity in Lung Cancer based on Protein-Interaction Networks

## System requirements
- min. 16GB RAM
- tested with Windows 11 and Ubuntu 22

## Pre requirements
- docker
- docker-compose version 2.22.0 or higher
- python3
- jupyter
- pip3

## Setup
- increased Docker VM memory to 16GB 

## Project structure
- **/code**: contains the jupyter notebooks to prepare the data and create the Neo4j database
- **/tex**: contains the LaTeX files for the thesis
- **/import_date**: (not included in the repository) contains the data from the GTEx and CMP databases and will be downloaded automatically by the jupyter notebooks
- **/processed_data**: (not included in the repository) contains the processed data from the GTEx and CMP databases and will be created automatically by the jupyter notebooks

## Local start
To start the project locally and reproduce the results, follow the steps below.

### 0. install python packages
Install the required python packages in the root directory of the project
```bash
pip3 install -r requirements.txt
```

### 1. start neo4j
Start neo4j in the root directory of the project
```bash
docker-compose up
```
The neo4j database is now available at http://localhost:7474/browser/

Initial login credentials:

**Username:** neo4j

**Passwort:** theBestNeo4JPassword4ever

### 2. start jupyter notebook
Start jupyter notebook in the root directory of the project

### 3. execute jupyter files
Execute the jupyter files in the following order:

* code/01_prepare_GTEx.ipynb
  * File to prepare the data from the GTEx database.


* code/02_prepare_CMP.ipynb 
  *  File to prepare the data from the CMP database.
 

* code/03_gene_nodes.ipynb
    * File to create the table that serves as the base for gene nodes.


* code/04_nodes_and_edges.ipynb
  * File to create the tables that serve as the base for protein nodes, protein-protein interactions, and gene-protein connections.


* code/05_neo4j_db_creation.ipynb
  * File to create the Neo4j database with the gene and protein nodes, protein-protein interactions, and gene-protein connections.


* code/06_neo4j_graph_algo.ipynb
    * File to run the PageRank graph algorithm on the Neo4j database and analyze the results.