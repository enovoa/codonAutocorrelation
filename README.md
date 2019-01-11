# codonAutocorrelation
Compute codon autocorrelation (aka codon covariation, codon reuse, codon pair usage) from fasta sequences

## What is included
- Scripts to compute and analyze codon autocorrelation from fasta sequences 
- Output: 3 types of measurements: 
(i) number of standard deviations from expected
(ii) effect vector
(iii) relative synonymous codon pair usage (RSCPU) 
For more information on what these metrics are, please see: Novoa EM, Jungreis I, Jaillon O, Kellis M. Elucidation of codon usage signatures across the domains of life. bioRxiv 2018. https://doi.org/10.1101/421487

## Quick start
If you want to go directly from a fasta to relative codon pair usage, you can directly run:
```
fromFasta2CodonAutocorrelation.sh <FILE.fasta>
```

## How to run the software: step by step

### STEP 1: Download genome CDS fasta sequences
You can download them, for example, from the EMBL CDS database: ftp://ftp.ebi.ac.uk/

### STEP 2: Get frequencies of codon pairs 

```
codon_autocorrelation_multiple_sequences.py <FILE.fasta> <mode>
where: <mode> can be DNA or RNA
```
This will generate two files: FILE.total_codons an FILE.paired_codons

### STEP 3: Merge two files from step 2
```
parse_codon_autocorrelation_output.sh <FILE.paired_codons> <FILE.total_codons>

```
This will generate a merged file: <INPUT>.merged

### STEP 4: Fix missing values for codon pairs that did not exist
```
fix_merged_file_codon_autocorrelation_counts_ALLaminoacids.sh <FILE.merged>
```
This will generate a merged file: <INPUT>.FIXED

### STEP 5: Compute codon pair usage statistics, relative to individual codon usage
```
  parse_codon_autocorrelation_merged.R --save <FILE.FIXED>
```

## Future work
Code can be modified to allow for the calculation of codon autocorrelation among non-synonymous codons (ongoing work)

## Citing this work

If you find this code useful, please cite: Novoa EM, Jungreis I, Jaillon O, Kellis M. Elucidation of codon usage signatures across the domains of life. bioRxiv 2018. https://doi.org/10.1101/421487

## Contact

If you have any doubts/questions/concerns, please contact: eva.novoa@crg.eu. Thanks!

