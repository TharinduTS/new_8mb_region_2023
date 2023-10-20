# new_8mb_region_2023

# First I extracted the region of interest from the vcf file using samtools
```bash
module load samtools
module load bcftools
mkdir region_1


find ../*.bam -printf "%f\n">files
while read i; do samtools consensus --show-del YES -r Chr7:8364998-8371997 -o region_1/"$i".consensus ../"$i";done<files

```
