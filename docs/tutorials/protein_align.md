---
title: Protein alignment
parent: Tutorials
nav_order: 1
permalink: /tutorials/protein_alignment/
---

# Protein sequence alignment
{: .no_toc }

{: .note }
What is the easiest way to visualise a protein alignment?

I have been looking for the best way to visualise protein (amino acid) alignments. The 
alignment part was not the key issue - more of how to do the downstream visualisation.

I then stumbled upon this tool, Snipit (https://github.com/aineniamh/snipit), through a 
colleague of mine, and turns out Snipit makes cool linear plots to visualise protein SNPs!

Here is how you can make a quick alignment + visualisation of your protein SNPs:

{: .note }
You will need to run this in a Terminal, and install mafft and snipit. I did the installation
through conda.


| | |
|:--|:--|
| **Input** | Protein sequences in FASTA format (`proteins.fasta`) |
| **Output** | SNPs plot and table |
| **Tools** | [MAFFT](https://mafft.cbrc.jp/alignment/software/), [snipit](https://github.com/aineniamh/snipit) |


Sample protein FASTA file:

```text
>reference
MKTAYIAKQRQISFVKSHFSRQ
>sample_1
MKTAYIAKQRQISFVKSHFSRE
```

{: .tip }
Put the sequence you want as reference (for alignment) as the first FASTA. 


Run mafft for alignment:
```bash
mafft --auto proteins.fasta > aln.fasta
```

Run snipit to make plot and SNP table:
```bash
snipit aln.fasta \
  --sequence-type aa \
  --colour-palette ugene \ # ugene for protein alignment
  --write-snps \ # write snp table
  --output-file substitutions \
  --format pdf # save plot in pdf, png, svg, ...
```


![Substitution plot]({{ site.baseurl }}/assets/images/aa_alignment.pdf){: width="600" }
*Figure 1. Protein SNPs using the OptrA protein as example.*


## References

- Katoh K, Standley DM (2013). MAFFT multiple sequence alignment software version 7. *Molecular Biology and Evolution* 30:772–780.
- snipit: <https://github.com/aineniamh/snipit>
