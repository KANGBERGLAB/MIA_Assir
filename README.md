RNA-seq Analysis Pipeline for "IL-17A alters human cortical development in a 3D ex vivo model of maternal immune activation"
This repository contains the R code used to perform RNA-seq analysis as described in the paper "IL-17A alters human cortical development in a 3D ex vivo model of maternal immune activation" (Assir et al., 2014). The code was used to analyze RNA-seq data and generate the figures presented in the publication.

Table of Contents
Overview
Requirements
Installation
Usage
Input Data
Output Files
Reproducibility
Contact Information
Overview
This project performs the following tasks:

Imports RNA-seq quantification data from Salmon output files.
Loads metadata for the samples.
Processes and summarizes transcript-level data to gene-level data using tximeta.
Performs differential gene expression analysis using DESeq2.
Outputs results for different cell types (NSC and bulk).
Generates CSV files for downstream analyses and plots for the paper figures.
Requirements
The analysis requires R version x.x.x or higher, and the following R packages must be installed:

tximeta (version x.x.x)
DESeq2 (version x.x.x)
org.Hs.eg.db (version x.x.x)
These packages will be installed automatically if missing.

Installation
To run the analysis, first clone this repository and make sure that you have R and RStudio installed.

Step 1: Clone the repository
Open a terminal and run the following command to clone the repository:

bash
Copy code
git clone https://github.com/yourusername/rnaseq-analysis-pipeline.git
Step 2: Install required R packages
You can install the required R packages by running the following script in R:

r
Copy code
source("R/rnaseq_analysis.R")
This script automatically checks for and installs any missing packages.

Usage
Once the repository is cloned and the packages are installed, you can run the RNA-seq analysis by following these steps:

Ensure your RNA-seq quantification files from Salmon are placed in the specified directory (see Input Data section below).
Modify the paths in the example usage to match your directory structure.
Run the analysis function run_rnaseq_analysis().
Example Usage
r
Copy code
# Set the base directory for quant files and metadata
base_dir <- "/path/to/MIA_salmon_quant"
metadata_path <- "/path/to/metadata.csv"
output_dir <- "/path/to/output"

# Run the analysis
run_rnaseq_analysis(base_dir, metadata_path, output_dir)
This will output CSV files containing differential gene expression results for both NSC and bulk cell types.

Input Data
1. Salmon Quantification Files
Ensure that the Salmon quantification files (e.g., quant.sf) are available in the specified directory. The directory structure should look like this:

python
Copy code
MIA_salmon_quant/
├── S1_transcripts_quant/
│   └── quant.sf
├── S2_transcripts_quant/
│   └── quant.sf
├── S3_transcripts_quant/
│   └── quant.sf
...
2. Metadata File
You should provide a metadata file (metadata.csv) with information about the samples. This file should contain the following columns:

folder_name: Corresponds to the sample folder names (e.g., S1_transcripts_quant).
condition: The experimental condition (e.g., IL17A, Veh).
cell: Cell type (e.g., NSC, Bulk).
donor: Donor or biological replicate ID.
An example of the metadata file format:

folder_name	condition	cell	donor
S1_transcripts_quant	IL17A	NSC	D1
S2_transcripts_quant	Veh	Bulk	D2
S3_transcripts_quant	IL17A	Bulk	D3
...	...	...	...
Output Files
The output directory will contain the results of the differential expression analysis for NSC and bulk cells:

DEG_MIA_nsc_results.csv: Differential expression results for NSC.
DEG_MIA_bulk_results.csv: Differential expression results for bulk cells.
These CSV files will include gene-level statistics such as log2 fold change, p-value, adjusted p-value (FDR), etc.

Reproducibility
The code in this repository was used to generate the results and figures in the publication "[Full Title of Your Paper]" (Author et al., Year). You can reproduce the analysis by following these steps:

Clone this repository.
Download and organize the input data as described in the Input Data section.
Run the analysis using the provided run_rnaseq_analysis() function.
The exact versions of R and the packages used are listed in the sessionInfo() output below:

bash
Copy code
# Example session info (replace with your actual session info)
sessionInfo()
# R version 4.0.2 (2020-06-22)
# Platform: x86_64-pc-linux-gnu (64-bit)
# ...
For detailed analysis scripts related to figures in the paper, refer to the scripts/ directory, which contains individual scripts for generating plots and other results.

Contact Information
For questions or further information, please contact:

Muhammad Assir
Email: dr.zamankhan@gmail.com
Affiliation: University of Aberdeen
