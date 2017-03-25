# Blacklists

I downloaded these blacklists from Anshul Kundaje's page: 

http://mitra.stanford.edu/kundaje/akundaje/release/blacklists/

```
wget http://mitra.stanford.edu/kundaje/akundaje/release/blacklists/hg38-human/hg38.blacklist.bed.gz
wget http://mitra.stanford.edu/kundaje/akundaje/release/blacklists/mm9-mouse/mm9-blacklist.bed.gz
wget http://mitra.stanford.edu/kundaje/akundaje/release/blacklists/mm10-mouse/mm10.blacklist.bed.gz
wget http://mitra.stanford.edu/kundaje/akundaje/release/blacklists/hg19-human/Anshul_Hg19UltraHighSignalArtifactRegions.bed.gz
gunzip *
```

I unzipped them, and then I standardized the names.
