---
layout: post
title: Download NCBI Protein Sequences 
tags: [research]
---

For a project I have been working on lately I wanted to download all archaeal *gyrA* sequences from NCBI and make a blast database out of them. I searched up and down the internet for a `curl` (or `wget`) solution, but didn't find anything that did exactly what I wanted. It took quite a bit of time for me to piecemeal one together, but my solution is below. Under the solution, I have listed my myriad google searches in hopes that someone will land on this page faster than it took me to craft this solution at some point in the future!

I found the sequences I was interested in by navigating to NCBI, selecting "protein" from the drop down menu selection, and searching for "gyra[All Fields] AND archaea[filter]". I selected "Send to:" from the drop down menu in the top right hand corner, selected file, and changed the format to Accession List. This produced a file with all accessions I wanted to download on their own line. I then fed that file into the following `while` loop:
 
```
while read inline 
do
	i=$inline
	curl -s  "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=protein&id=${i}&rettype=fasta&retmode=txt">>archaea-gyra.faa
done < archaea-gyra.seq
```

## Google queries:

+ download ncbi protein sequences wget 
+ download all ncbi protein seqs for a protein name unix 
+ programmatically download all ncbi protein seqs for a protein name unix 
+ download all protein sequences from protein db ncbi 
+ how to download all protein sequences ncbi
+ how to download all genbank protein sequences matching a query 