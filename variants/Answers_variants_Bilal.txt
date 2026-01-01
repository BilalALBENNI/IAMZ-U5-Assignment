This report is done by Bilal AL BENNI and Sasha KASSIS

# Session 5: Mapping and Variant Calling Report
---

## 5.1 How we solved the exercises

### Exercise 1: Read Quality Control and Alignment
We started by assessing the quality of raw paired-end FASTQ reads for sample SAMEA2569438 using FastQC. We identified that the dataset consisted of two files because they represent forward and reverse reads from a paired-end sequencing experiment. We then used BWA-MEM to align these reads to the Oryza sativa (rice) reference genome (chromosome 10).

### Exercise 2: Alignment File Formats
The initial alignment was generated in SAM format. We used Samtools to convert this to the more efficient binary BAM format and also explored the CRAM format. We observed that CRAM provides the highest compression (saving 40-50% space over BAM) by using reference-based compression, though the reference file is required for decompression.

### Exercise 3: Post-processing and Depth Analysis
To prepare the alignment for variant calling, we used 'samtools sort' to organize reads by genomic coordinate and 'samtools index' to allow for rapid data retrieval. We utilized 'samtools flagstat' to confirm a high mapping rate (99.49%). Finally, we used 'samtools mpileup' to analyze base coverage across the chromosome.

### Exercise 4: Duplicate Marking and Metadata
We used Picard-tools 'AddOrReplaceReadGroups' to add essential metadata (Sample ID, Library ID, Platform) to the BAM header. To prevent false-positive variant calls, we used 'MarkDuplicates' to identify and flag PCR artifacts. We verified the results by loading the BAM and index files into the Integrative Genomics Viewer (IGV) to visualize reads at specific coordinates.

### Exercise 5: Variant Calling and Filtering
We used FreeBayes to call SNPs and small indels, setting the ploidy to 2. The resulting VCF file contained 31,521 raw records. To remove artifactual variants, we applied a quality filter (QUAL < 1) using 'bcftools filter'. This resulted in 30,490 high-confidence variants, including 25,441 SNPs and 2,395 indels, which were then visualized and validated using IGV.

## 5.2 Problems Faced
The primary challenge in this session involved the transition from SAM to BAM/CRAM formats, as random retrieval of genomic regions only works on sorted and indexed files. Additionally, distinguishing true biological variants from sequencing noise required careful filtering based on quality scores, as raw variant callers like FreeBayes are designed to be highly sensitive and often report false positives that must be removed manually using BCFTools.

## 5.3 References:

### 3000 Rice Genomes Project (2014). The 3000 rice genomes project. GigaScience, 3(1).

### Danecek, P., et al. (2021). Twelve years of SAMtools and BCFtools. GigaScience, 10(2).

### Li, H. (2013). Aligning sequence reads, clone sequences and assembly contigs with BWA-MEM. arXiv:1303.3997.

### Garrison, E., & Marth, G. (2012). Haplotype-based variant detection from short-read sequencing. arXiv:1207.3907.

