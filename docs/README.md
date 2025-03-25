# ONT sequencing data processing for prokaryote isolates

These docs were originally generated for the purposes of a study that was investigating bacterial comparative genomics and virus-host pairings in a bacterial culture collection isolated from estuarine water samples. 

The processing steps outlined in these docs include: 

1. raw data prep, basecalling, and demultiplexing  
1. sequence read qc and quality trimming
1. assembly and assembly polishing
1. prokaryote genome stats, taxonomy, and gene annotation
1. associated phage identification, gene annotation, and similarity to reference viral genomes.

NOTE:

- The steps and tools covered represent *one* approach to processing Oxford Nanopore long-read sequencing data for **prokaryote** isolates. At each of the steps, several alternative tools are available and worth considering. The method outlined simply represents the approach we took with this study, and offers an overview of the processing steps required overall.
- Also note that, once assemblies are generated, the steps involved in 4_Isolate_genomes and 5_Phage_genomes are directly analogous to those presented in the metagenomics and viromics data processing docs also hosted on the [Genomics Aotearoa github](https://github.com/GenomicsAotearoa/environmental_metagenomics). Please see those documents for more detailed description of each of the relevant steps (including information on alternative methods). 
- Sequencing and assembling genomes of **eukaryote** organisms is a considerably more complex task. This is not discussed here, and the process outlined in these docs is likely not sufficient (at best) or may be wholly inappropriate (at worst) for that task.
- Note that if your input samples are not pure isolates (e.g. mixed-community cultures or environmental samples), it may be necessary to add additional steps after assembly to separate out genomes of individual organisms (and/or very closely related populations) (i.e. binning assembled contigs into MAGs/SAGs etc). This is not covered in these docs.

All examples that follow are based on sequencing of **96 isolates** multiplexed during ONT library prep (each tagged with a unique barcode (in this case, barcode1-96)).
