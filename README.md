# Introduction

This repository contains training sets that can be used with the Ribosomal Database Project classifier (Wang et al., 2007) to taxonomically assign Eukaryote CO1 mtDNA sequences.

# How to cite

If you use these training sets in a publication, please cite:

## Training set 
Porter, T.M., & Hajibabaei, M. (2018) Automated high throughput animal CO1 metabarcode classification.  Scientific Reports, 8, 4226.

## Classifier 
Wang et al. (2007) Naïve Bayesian classifier for rapid assignment of rRNA sequences into the new bacterial taxonomy.  Applied and Environmental Microbiology, 73: 5261.

# Releases

### May 28, 2018

The latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.0
The CO1v3_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.0-ref
The CO1v3_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They were originally mined from GenBank in April 2018.  These sequences were originally identified to the species rank in the NCBI nucleotide database.  All sequences here are at least 500bp long and have been screened to remove human and bacterial contaminant sequences.  Sequences containing any nucleotide ambiguities were excluded.  Taxonomic composition is largely Arthropoda and Chordata.  Outgroup taxa representing other major eukaryote and prokaryote lineages have been included.

### December 4, 2017 

The v2.0 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v2.0
The CO1v2_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the v2.0 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v2.0-ref
The CO1v2_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  This dataset is based on v1.0 except that the species rank was retained.

The original release described in Porter & Hajibabaei (2017) can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v1.0
The CO1v1_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the genus rank.

The reference files for the original release described in Porter & Hajibabaei (2017) can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v1.0-ref
The CO1v1_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They were originally mined from GenBank in August 2016.  These sequences were originally identified to the species rank in the NCBI nucleotide database but have been summarized to the genus rank here.  All sequences here are at least 500bp long and have been screened to remove human contaminant sequences.  Taxonomic composition is largely Arthropoda and Chordata.  Outgroup taxa representing other major Eukaryote groups were included if they contained the BARCODE keyword in GenBank.

# How to use

Decompress the tar.gz file:

$ tar -xvzf FileName.tar.gz

Use with the RDP classifier:

java -Xmx8g -jar /path/to/rdp_classifier_2.12/dist/classifier.jar classify -t /path/to/CO1version_trained/rRNAClassifier.properties -o ClassifiedQueryFilename QueryFilename

# Additional information

For additional information on choosing appropriate bootstrap support cutoff values, see Porter & Hajibabaei (2017):
https://doi.org/10.1101/219675

For additional information on how to run the RDP classifier, see the RDPclassifier 2.12 README.

The RDP classifier v2.12 can be downloaded from:
https://sourceforge.net/projects/rdp-classifier/

# Acknowledgements

We acknowledge support from the Canadian federal Genomics Research & Development Initiative (GRDI) interdepartmental EcoBiomics project.
