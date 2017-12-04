# CO1Classifier
Training sets that can be used with the Ribosomal Database Project classifier (Wang et al., 2007) to taxonomically assign Eukaryote CO1 mtDNA sequences.

-------------------------------------------------------------

If you use these training sets in a publication, please cite:

Training set - 
Porter, T.M., & Hajibabaei, M. (2017) Automated high throughput animal DNA metabarcode classification.  bioRxiv, doi: https://doi.org/10.1101/219675

Classifier - 
Wang et al. (2007) Naïve Bayesian classifier for rapid assignment of rRNA sequences into the new bacterial taxonomy.  Applied and Environmental Microbiology, 73: 5261.

-------------------------------------------------------------

December 1, 2017 - The CO1 v1 training set can be used to make taxonomic assignments to the GENUS rank and the CO1 v2 training set can be used to make taxonomic assignments to the SPECIES rank.  These were developed and tested with the RDP classifier 2.12 (separate download and installation).  

CO1v1_trained.tar.gz and CO1v2_trained.tar.gz contains the files produced after training the RDP Classifier and these compressed files should be downloaded individually.  

At the command-line run tar -xvzf FileName.tar.gz to decompress the folder.

Use with the RDP classifier as follows:

java -Xmx8g -jar /path/to/rdp_classifier_2.12/dist/classifier.jar classify -t /path/to/CO1version_trained/rRNAClassifier.properties -o ClassifiedQueryFilename QueryFilename

The folder 'ReferenceFiles' contains CO1v1_training.tar.gz and CO1v2_training.tar.gz with the original taxon and fasta files used to train the RDP classifier and are included here for reference only.  

For additional information on choosing appropriate bootstrap support cutoff values, see Porter & Hajibabaei (2017).

For additional information on how to run the RDP classifier, see the RDPclassifier 2.12 README.
