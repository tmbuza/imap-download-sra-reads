# Downloading Multiple Fastq Files

To download multiple fastq files, follow these steps:

## Confirm `fasterq-dump` Installation
Ensure that `fasterq-dump` is in the path. You can type `which fasterq-dump` or `fasterq-dump --help` in the terminal to confirm its presence.

## Specify Output and Temporary Files
When using `fasterq-dump`, you must specify the output directory (`--outdir`) and temporary directory (`--temp`).

## Download in a Loop
You can use a `for loop` to specify a range of SRA accessions and download them sequentially. Here's an example code for downloading reads from the NCBI-SRA for accessions ranging from SRR7450706 to SRR7450761:

```bash
for (( i = 706; i <= 761; i++ ))
    do
        time fasterq-dump SRR7450$i \
        --split-3 \
        --force \
        --skip-technical \
        --outdir data/reads \
        --temp data/temp \
        --threads 4		
    done

```
