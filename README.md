# Genome assembly decoy sequences

This repository contains fasta files for pre-alignments. These are useful for studies of repeats, mtDNA, or using as decoy sequences.

## Contents:

### Repeats

* human_alu.fa - Manually curated sequences from GenBank for alu elements.
* human_alphasat.fa - Manually curated sequences from GenBank annotated for centromeric or alpha-satellite DNA repeats.
* human_rDNA.fa - Complete human ribosomal repeat unit
* human_repeats.fa: a combination of the 3 of above (alu, alphasat, and rDNA) , produced with `cat human_alu.fa human_alphasat.fa human_rDNA.fa > human_repeats.fa`.

### mtDNA

* rCRSd.fa is the Revised Cambridge Reference Sequence (rCRS) of the Human Mitochondrial DNA obtained from [NC_012920](http://www.ncbi.nlm.nih.gov/nuccore/251831106). It is duplicated (pasted 2 times, one right after another) to simulate circular DNA for aligners that do not have a circular setting (hence the appended `d` to the name). This is the assembly used in hg38.
* RSRS.fa is from [this paper](http://dx.doi.org/10.1016/j.ajhg.2012.03.002).
* eve1.fa is from [this paper](http://dx.doi.org/10.1093/nar/gkm207).
* chrMx - Doubled chrM derived from [AF347015](http://www.ncbi.nlm.nih.gov/nuccore/13273284), the African Yoruban sequence used in the hg19 assembly.

## Pre-built indexes

You can download pre-built [refgenie](http://www.github.com/databio/refgenie) reference genomes indexes for use in pipelines here:

* [list of pre-built indexes](http://big.databio.org/refgenomes/)

To use these with [pypiper](http://www.databio.org/pypiper) pipelines, just unzip the folder and place in your genomes folder (e.g. `$GENOMES`).

## Built it yourself

Build genome references for these decoy sequences using [refgenie](http://github.com/databio/refgenie) like this:

```
refgenie.py -i hg19_alphasat.fa
```

A complete setup:

```
GENOMES=decoy_genomes

pip install --user --upgrade https://github.com/epigen/pypiper/zipball/master
git clone https://github.com/databio/ref_decoy.git
git clone https://github.com/databio/refgenie.git

for fa_file in `ls ref_decoy/*.fa`; do python refgenie/src/refgenie.py -i $fa_file; done
```

Or, using the refgenie docker image (adds `-d`):

```
for fa_file in `ls ref_decoy/*.fa`; do python refgenie/src/refgenie.py -d -i $fa_file; done
```

