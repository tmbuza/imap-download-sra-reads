# Resizing Fastq Files

## Purpose

Sometimes, you may want to extract a small subset of Fastq files to test a bioinformatics pipeline.

To resize Fastq files, follow these steps:

## Using `seqkit sample`

You can resize Fastq files using the `seqkit sample` function. This tool allows you to randomly sample reads from Fastq files.

## Example

Here's an example of extracting only 1% of the paired-end metagenomics sequencing data. 

> This bash script extracts 1% of the reads from only two samples (SRR10245277 to SRR10245280).

```bash
mkdir -p data
for i in {77..80}
  do
    cat SRR102452$i\_1.fastq \
    | seqkit sample -p 0.01 \
    | seqkit shuffle -o data/SRR102452$i\_1_sub.fastq \
    | cat SRR102452$i\_2.fastq \
    | seqkit sample -p 0.01 \
    | seqkit shuffle -o data/SRR102452$i\_2_sub.fastq
  done
  
```
