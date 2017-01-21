This repository contains decoy fasta files for alignments.

* alphasat - Manually curated sequences from GenBank annotated for centromeric or alpha-satellite DNA repeats.
* chrMx - Doubled chrM (chrM sequence pasted 2 times, one right after another) to simulate circular DNA for aligners that do not have a circular setting
* rDNA - Complete human ribosomal repeat unit

Build genome references for these decoy sequences using [refgenie](http://github.com/databio/refgenie) like this:

```
refgenie.py -i hg19_alphasat.fa
```

A complete setup:

```
GENOMES=$RESOURCES/genomes

pip install --user --upgrade https://github.com/epigen/pypiper/zipball/master
git clone https://github.com/databio/ref_decoy.git
git clone https://github.com/databio/refgenie.git

for fa_file in `ls ref_decoy/*.fa`; do python refgenie/src/refgenie.py -i $fa_file; done
```
