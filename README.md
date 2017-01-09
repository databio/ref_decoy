This repository contains decoy fasta files for alignments.

* alphasat - Manually curated sequences from GenBank annotated for centromeric or alpha-satellite DNA repeats.
* chrMx - Doubled chrM (chrM sequence pasted 2 times, one right after another) to simulate circular DNA for aligners that do not have a circular setting
* rDNA - Complete human ribosomal repeat unit

Build genome references for these decoy sequences using [refgenie](http://github.com/databio/refggenie) like this:

```
refgenie.py -i hg19_alphasat.fa
```
