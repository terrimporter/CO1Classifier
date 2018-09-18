# Introduction

This repository contains training sets that can be used with the Ribosomal Database Project classifier (Wang et al., 2007) to taxonomically assign Eukaryote CO1 mtDNA sequences.  The latest release can be downloaded from https://github.com/terrimporter/CO1Classifier/releases .  The trained files ready to be used with the RDP Classifier are available as well as the original files used for training (a taxonomy file and a FASTA file) are available as 'version-ref'.

# How to cite

If you use these training sets in a publication, please cite:

## Training set 
Porter, T.M., & Hajibabaei, M. (2018) Automated high throughput animal CO1 metabarcode classification.  Scientific Reports, 8, 4226.

## Classifier 
Wang et al. (2007) Naïve Bayesian classifier for rapid assignment of rRNA sequences into the new bacterial taxonomy.  Applied and Environmental Microbiology, 73: 5261.

# Releases

### v3.1

The latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.1
The CO1v3_1_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.1-ref
The CO1v3_1_training.tar.gz file should be cecompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They are the same as the v3 files except that a few bacterial outgroup sequences that were misannotated as bacteriophage viruses were removed.

The v3 MINIMUM bootstrap cutoff values should be used with this version of the CO1 classifier.

### v3

The v3 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.0
The CO1v3_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the v3 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.0-ref
The CO1v3_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They were originally mined from GenBank in April 2018.  These sequences were originally identified to the species rank in the NCBI nucleotide database.  All sequences here are at least 500bp long and have been screened to remove human and bacterial contaminant sequences.  Sequences containing any nucleotide ambiguities were excluded.  Taxonomic composition is largely Arthropoda and Chordata.  Outgroup taxa representing other major eukaryote and prokaryote lineages have been included.

Assuming that your query sequences are present in the reference set, using these cutoffs should result in ~99% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp  
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 | 0 | 0 | 0 | 0  
Kingdom | 0 | 0 | 0 | 0 | 0  
Phylum | 0 | 0 | 0 | 0 | 0   
Class | 0 | 0 | 0 | 0 | 30  
Order | 0 | 0 | 0 | 20 | 70  
Family | 0 | 10 | 20 | 20 | 70  
Genus | 40 | 30 | 30 | 40 | 90  
Species | NA | NA | NA | NA | NA  

NA = No cutoff available will result in 99% correct assignments

### v2 

The v2.0 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v2.0
The CO1v2_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the v2.0 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v2.0-ref
The CO1v2_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  This dataset is based on v1.0 except that the species rank was retained.

Assuming that your query sequences are present in the reference set, using these cutoffs should result in ~99% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp
--- |:---:|:---:|:---:|:---:|:---:
Superkingdom | 0 | 0 | 0 | 0 | 0
Kingdom | 0 | 0 | 0 | 0 | 0
Phylum | 0 | 0 | 0 | 0 | 0 
Class | 0 | 0 | 0 | 0 | 30
Order | 0 | 0 | 0 | 10 | 70
Family | 0 | 0 | 20 | 20 | 70
Genus | 30 | 30 | 30 | 30 | 80
Species | NA | NA | NA | NA | NA

NA = No cutoff available will result in 99% correct assignments

### v1

The original release described in Porter & Hajibabaei (2017) can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v1.0
The CO1v1_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the genus rank.

The reference files for the original release described in Porter & Hajibabaei (2017) can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v1.0-ref
The CO1v1_training.tar.gz file should be decompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They were originally mined from GenBank in August 2016.  These sequences were originally identified to the species rank in the NCBI nucleotide database but have been summarized to the genus rank here.  All sequences here are at least 500bp long and have been screened to remove human contaminant sequences.  Taxonomic composition is largely Arthropoda and Chordata.  Outgroup taxa representing other major Eukaryote groups were included if they contained the BARCODE keyword in GenBank.

Assuming that your query sequences are present in the reference set, using these cutoffs should result in ~99% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp
--- |:---:|:---:|:---:|:---:|:---:
Superkingdom | 0 | 0 | 0 | 0 | 0
Kingdom | 0 | 0 | 0 | 0 | 0
Phylum | 0 | 0 | 0 | 0 | 0 
Class | 0 | 0 | 0 | 0 | 60
Order | 0 | 0 | 10 | 40 | 80
Family | 20 | 20 | 30 | 40 | 80
Genus | 70 | 60 | 60 | 60 | NA

NA = No cutoff available will result in 99% correct assignments

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
