# new_8mb_region_2023

# First I extracted the region of interest from the vcf file using samtools
```bash
module load samtools
module load bcftools
mkdir region_1


find ../*.bam -printf "%f\n">files
while read i; do samtools consensus --show-del YES -r Chr7:8364998-8371997 -o region_1/"$i".consensus ../"$i";done<files

```
# approach 4
```extract region
bcftools view ../../PCA/vcfs/combined_data_2023_Aug.vcf.gz --regions Chr7:8363998-8371998>region1.vcf
```
git clone from this page/ follow instructions

MAKE the script executable to make it easier to work with
```wget
https://github.com/edgardomortiz/vcf2phylip
```
then convert the refion to fsata
```
#!/bin/sh
#SBATCH --job-name=fst
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --time=12:00:00
#SBATCH --mem=64gb
#SBATCH --output=abba.%J.out
#SBATCH --error=abba.%J.err
#SBATCH --account=def-ben

#SBATCH --mail-user=premacht@mcmaster.ca
#SBATCH --mail-type=BEGIN
#SBATCH --mail-type=END
#SBATCH --mail-type=FAIL
#SBATCH --mail-type=REQUEUE
#SBATCH --mail-type=ALL

python vcf2phylip.py --input ../../../PCA/vcfs/no_mello_no_cal_whole_genome.vcf.gz.recode.vcf.gz --nexus --fasta
```
