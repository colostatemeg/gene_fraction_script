# gene_fraction_script

##Summary

This is a script to determine what proportion of a reference sequence (e.g., a gene) is aligned by at least 1 sequence read in a fastq file (i.e., the "gene fraction").

The script to do this is available as a jar file [on GitHub](https://github.com/colostatemeg/gene_fraction_script/releases)

The script was written by Adam Dettenwanger.

##Usage

The script takes as input a SAM file and a database of reference sequences.  It outputs 1 required file, which includes the gene fraction for each identified reference sequences.  It will also output a mismatch file, if specified.

Command-line usage:
```
java -jar gene_fraction_calculator.jar [-t <int>][-V][-m <missMatchesOutFile>] -d <database.fa> -i <samFile.sam> -o <outputFile>

Required parameters:

-d   Path to the reference database. This must be a fasta file. It must also be the same reference database that was used to create the input SAM file.
  
-i   Path to the input SAM file.
  
-o   Path to the ratio output file. This is a tab delimited file that contains the read counts and coverage ratios for the reference genes.  Note that any reference genes that were not seen in the SAM file will not show up in this file.

Optional parameters:

-t   Threshold. This is the minimum number of matches that are required for a read to be included in the coverage ratio for a gene. There are two modes of operation, threshold and exact-match mode. If -t <int> is specified with an integer larger than 0, then the program will operate in threshold mode. If -t is not specified then the program will use exact-match mode. In exact-match mode, only reads where the entire read matches the reference (with no miss-matches) will be included in the coverage ratio. THIS OPTION HAS A PROFOUND EFFECT ON THE RESULTS.
  
-m   Path to the miss-matches output file. If specified, the program will create a tab delimited file that contains all of the miss-matches within the match/miss-match regions in accordance with the Extended CIGAR string.
  
-V   Verbose mode.  The Program will print LOTS of information to STDOUT. Its best to redirect this to a file so it can be viewed in a sensible manner. The verbose information serves well as a log file.
  
-v   Print the program version, then exit.
  
-h   Print this awesome help message, then exit.
  
-c   Coffee Break.  Brew some extra strength coffee, then exit.
```
