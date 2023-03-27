# Eukaryote CO1 Reference Set For The Identification of DNA Metabarcodes

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4741447.svg)](https://doi.org/10.5281/zenodo.4741447)  

This repository contains training sets that can be used with the Ribosomal Database Project classifier (Wang et al., 2007) to taxonomically assign Eukaryote CO1 mtDNA sequences.  The latest release can be downloaded from https://github.com/terrimporter/CO1Classifier/releases .  The trained files ready to be used with the RDP Classifier are available as well as the original files used for training (a taxonomy file and a FASTA file) are available as 'version-ref'.  Since version 5, I'm also releasing reference sets formatted to work with BLAST+ and SINTAX.  

## Quick start

```linux
############ Install the RDP classifier if you need it
# The easiest way to install the RDP classifier v2.13 is using conda
conda install -c bioconda rdp_classifier
# Alternatively, you can install from SourceForge and run with java if you don't use conda
wget https://sourceforge.net/projects/rdp-classifier/files/rdp-classifier/rdp_classifier_2.13.zip
# decompress it
unzip rdp_classifier_2.13
# record path to classifier.jar ex. /path/to/rdp_classifier_2.13/dist/classifier.jar

############ Get the latest COI training set
wget https://github.com/terrimporter/CO1Classifier/releases/download/v4/CO1v4_trained.tar.gz

# decompress it
tar -xzf CO1v4_trained.tar.gz

# record the path to the rRNAClassifier.properties file ex. /path/to/mydata_trained/rRNAClassifier.properties

############ Run the RDP Classifier 
# If it was installed using conda, run it like this:
rdp_classifier -Xmx8g classify -t /path/to/mydata_trained/rRNAClassifier.properties -o rdp.output query.fasta
# Otherwise run it using java like this:
java -Xmx8g -jar /path/to/rdp_classifier_2.13/classifier.jar -t /path/to/mydata_trained/rRNAClassifier.properties -o rdp.output query.fasta
```

## How to cite

If you use these training sets in a publication, please cite:

### CO1 Classifier publication
Porter, T.M., & Hajibabaei, M. (2018) Automated high throughput animal CO1 metabarcode classification.  Scientific Reports, 8, 4226.

### CO1 Classifier code repository
Teresita M. Porter. (2017, December 4). Eukaryote CO1 Reference Set For The RDP Classifier (Version v4.0.1). Zenodo. http://doi.org/10.5281/zenodo.4741447   

### The RDP classifier 
Wang et al. (2007) Naïve Bayesian classifier for rapid assignment of rRNA sequences into the new bacterial taxonomy.  Applied and Environmental Microbiology, 73: 5261.

## Releases

### v5

This version was updated to include COI sequences mined from GenBank [February 2023].  These records reflect those deposited between
1982 - 2022 (inclusive).  GenBank sequences were filtered to only include those 500bp+, containing no nucleotide ambiguities, and preferrably with a Linnean binomial species name and/or a BOLD BIN.  Sequences were screened to remove human and bacterial conaminants.  Bacterial outgroup sequences were added.

Accuracy was assessed using 5-fold cross validation.  The metazoan sequences in the classifier were divided into 5 groups. ach fold of the data, the remaining four folds were combined to create a training set (i.e., 20% test, 80% train).  The average number of correct sequences from each fold was used to calculate the cutoffs below.

Assuming that your query sequences are present in the reference set, using these cutoffs should result in ~99% correct assignments:

Rank | 500bp+ | 400 bp | 300 bp | 200 bp | 100 bp
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 |  |  | 0 |   
Kingdom | 0 |  |  | 0 |   
Phylum | 0 |  |  | 0 |    
Class | 0 |  |  | 0 |   
Order | 0 |  |  | 0 |   
Family | 0 |  |  | 0 |   
Genus | 0.3 |  |  | 0 |   
Species | NA |  |  | NA |   

NA = No cutoff available will result in 99% correct assignments

If you really want to work with species level data, then assuming that your query sequences are present in the reference set, using these cutoffs should result in ~95% correct assignments:

Rank | 500bp+ | 400 bp | 300 bp | 200 bp | 100 bp  
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 |  |  | 0 |   
Kingdom | 0 |  |  | 0 |   
Phylum | 0 |  |  | 0 |    
Class | 0 |  |  | 0 |   
Order | 0 |  |  | 0 |   
Family | 0 |  |  | 0 |   
Genus | 0 |  |  | 0 |   
Species | 0.95 |  |  | 0.95 |   

NA = No cutoff available will result in 95% correct assignments

If you are okay with more lenient cutoffs, since this method has been shown to have a high false negative rate in practice, then using these cutoffs should result in ~90% correct assignments:

Rank | 500bp+ | 400 bp | 300 bp | 400 bp | 100 bp  
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 |  |  | 0 |   
Kingdom | 0 |  |  | 0 |   
Phylum | 0 |  |  | 0 |    
Class | 0 |  |  | 0 |   
Order | 0 |  |  | 0 |   
Family | 0 |  |  | 0 |   
Genus | 0 |  |  | 0 |  
Species | 0.1 |  |  | 0.20 |   

### v4

This version was updated to include COI sequences mined from GenBank [April 2019] and the BOLD data releases [iBOL_phase2.0_COI.tsv to iBOL_phase_6.50_COI.tsv] from http://v3.boldsystems.org/index.php/datarelease .  GenBank sequences were filtered to only include those 500bp+, containing no nucleotide ambiguities, and with a Linnean binomial species name.  BOLD sequences were filtered to only retain sequences 500bp+, with less than 3 ambiguous bases, and containing a Linnean binomial species name.  Sequences were screened for human and bacterial contaminants.  Bacterial outgroup sequences were added.

This page will be updated with updated cutoffs when available.  For now use the recommended cutoffs for v3 (below).

### v3.2

This version was updated to include some invasives species of interest even though their sequences are less than 500bp in length.

The latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.2
The CO1v3_2_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the latest release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.2-ref
The CO1v3_2_training.tar.gz file should be cecompressed.  The folder contains the original taxonomy and fasta files that are included here for reference only.  They are the same as the v3 files except that a few bacterial outgroup sequences that were misannotated as bacteriophage viruses were removed.

The v3 MINIMUM bootstrap cutoff values should be used with this version of the CO1 classifier.

### v3.1

The v3.1 release can be downloaded from here:
https://github.com/terrimporter/CO1Classifier/releases/tag/v3.1
The CO1v3_1_trained.tar.gz file should be decompressed and used directly with the RDP Classifier to make taxonomic assignments to the species rank.

The reference files for the v3.1 release can be downloaded from here:
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

If you really want to work with species level data, then assuming that your query sequences are present in the reference set, using these cutoffs should result in ~95% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp  
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 | 0 | 0 | 0 | 0  
Kingdom | 0 | 0 | 0 | 0 | 0  
Phylum | 0 | 0 | 0 | 0 | 0   
Class | 0 | 0 | 0 | 0 | 0  
Order | 0 | 0 | 0 | 0 | 10  
Family | 0 | 0 | 0 | 0 | 30  
Genus | 0 | 0 | 0 | 0 | 30  
Species | 60 | 70 | 70 | 80 | NA  

NA = No cutoff available will result in 95% correct assignments

If you are okay with more lenient cutoffs, since this method has been shown to have a high false negative rate in practice, then using these cutoffs should result in ~90% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp  
--- |:---:|:---:|:---:|:---:|:---:  
Superkingdom | 0 | 0 | 0 | 0 | 0  
Kingdom | 0 | 0 | 0 | 0 | 0  
Phylum | 0 | 0 | 0 | 0 | 0   
Class | 0 | 0 | 0 | 0 | 0  
Order | 0 | 0 | 0 | 0 | 0  
Family | 0 | 0 | 0 | 0 | 10  
Genus | 0 | 0 | 0 | 0 | 10  
Species | 0 | 0 | 0 | 0 | 40  

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

Assuming that your query sequences are present in the reference set, using these cutoffs should result in ~95% correct assignments:

Rank | 500bp+ | 400 bp | 200 bp | 100 bp | 50 bp
--- |:---:|:---:|:---:|:---:|:---:
Superkingdom | 0 | 0 | 0 | 0 | 0
Kingdom | 0 | 0 | 0 | 0 | 0
Phylum | 0 | 0 | 0 | 0 | 0 
Class | 0 | 0 | 0 | 0 | 0
Order | 0 | 0 | 0 | 0 | 10
Family | 0 | 0 | 0 | 0 | 30
Genus | 0 | 0 | 0 | 0 | 30
Species | 50 | 40 | 50 | 60 | 90

NA = No cutoff available will result in 95% correct assignments

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

# References

Porter, T.M., & Gibson, J.F., Shokralla, S., Baird, D.J., Golding, G.B., Hajibabaei, M. (2014) Rapid and accurate taxonomic classification of insect (class Insecta) cytochrome c oxidase subunit 1 (COI) DNA barcode sequences using a naive Bayesian classifier.  Molecular Ecology Resources, 14: 929-942.

Porter, T.M., & Hajibabaei, M. (2018) Automated high throughput animal CO1 metabarcode classification.  Scientific Reports, 8, 4226.

Wang, Q., Garrity, G. M., Tiedje, J. M., & Cole, J. R. (2007). Naive Bayesian Classifier for Rapid Assignment of rRNA Sequences into the New Bacterial Taxonomy. Applied and Environmental Microbiology, 73(16), 5261–5267. Available from https://sourceforge.net/projects/rdp-classifier/

# Acknowledgements

We acknowledge support from the Canadian federal Genomics Research & Development Initiative (GRDI), Metagenomics-Based Ecosystem Biomonitoring (Ecobiomics) project.

Last updated: March 27, 2023
