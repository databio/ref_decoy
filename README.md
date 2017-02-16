# Genome assembly decoy sequences

This repository contains decoy fasta files for alignments.

## Contents:

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

## Assembly info

These decoy sequences aren't actually relative to an assembly (e.g. hg19) but to an organism (e.g. human). At the moment I'm naming them relative to the assembly, though, (e.g. `hg19_alphasat`), so that programmatic software can easily find them (it is given the string `hg19` and can derive the decoy folders as needed). Thus the `hg38` versions are just symlinks to the `hg19` versions. It's a bit of a hack --  they have to be duplicated so the tool can find them if you're using hg19 or hg38.
