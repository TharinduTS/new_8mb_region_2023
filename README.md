# new_8mb_region_2023

# First I extracted the region of interest from the vcf file using samtools
```bash
module load samtools
module load bcftools
mkdir region_1

bcftools query -l ../PCA/vcfs/combined_data_2023_Aug.vcf.gz >files
while read i; do samtools faidx ../reference_genome/XENTR_10.0_genome_scafconcat_goodnamez.fasta Chr7:8320031-8391760 | bcftools consensus ../PCA/vcfs/combined_data_2023_Aug.vcf.gz --sample "$i" > ./region_1/"$i"out.fa;done<files
```
