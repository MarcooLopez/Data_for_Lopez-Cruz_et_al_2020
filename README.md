
# Wheat dataset

### Description

The dataset consists of 1,092 inbred wheat lines grouped into 39 trials and grown during the 2013-2014 season at the Norman Borlaug experimental research station in Ciudad Obregon, Sonora, Mexico. Each trial consisted of 28 breeding lines that were arranged in an alpha-lattice design with three replicates and six sub-blocks. The trials were grown in four different environments:

 - E1: Flat-Drought (sowing in flat with irrigation of 180 mm through drip system)
 - E2: Bed-2IR (sowing in bed with 2 irrigations approximately 250 mm)
 - E3: Bed-5IR (bed sowing with 5 normal irrigations)
 - E4: Bed-EHeat (bed sowing 30 days before optimal planting date with 5 normal irrigations approximately 500 mm)

#### 1. Phenotypic data

Measurements of grain yield (YLD) were reported as the total plot yield after maturity. Records for YLD are reported as adjusted means from which trial, replicate and sub-block effects were removed. Measurements for days to heading (DTH), days to maturity (DTM), and plant height (PH) were recorded only in the first replicate at each trial and thus no phenotype adjustment was made.

#### 2. Reflectance data

Reflectance data was collected from the fields using both infrared and hyper-spectral cameras mounted on an aircraft on 9 different dates (time-points) between January 10 and March 27th, 2014. During each flight, data from 250 wavelengths ranging from 392 to 850 nm were collected for each pixel in the pictures. The average reflectance of all the pixels for each wavelength was calculated from each of the geo-referenced trial plots and reported as each line reflectance. Data for reflectance and Green NDVI and Red NDVI are reported as adjusted phenotypes from which trial, replicate and sub-block effects were removed. Each data-point matches to each data-point in phenotypic data.

#### 3. Marker data

Lines were sequenced for GBS at 192-plexing on Illumina HiSeq2000 or HiSeq2500 with 1 x 100 bp reads. SNPs were called across all lines anchored to the genome assembly of Chinese Spring (International Wheat Genome Sequencing Consortium 2014). Next, SNP were extracted and filtered so that lines >50% missing data were removed. Markers were recoded as –1, 0, and 1, corresponding to homozygous for the minor allele, heterozygous, and homozygous for the major allele, respectively. Next, markers with a minor allele frequency <0.05 and >15% of missing data were removed. Remaining SNPs with missing values were imputed using the mean of the observed marker genotypes at a given locus.

### Format

Replicated (adjusted) phenotypic and reflectance data for all four environments (E1, ..., E4) are storaged in R-datasets `wheatHTP.E1`, ..., and `wheatHTP.E4`, respectively. Each file contains the following objects

 - `Y`: (matrix) phenotypic data for YLD, DTH, DTM, and PH; and the trial in which each genotype was tested.
 - `X`: (9-dimensional list) reflectance data for time-points 1,2,...,9.
 - `VI`: (9-dimensional list) green and red NDVI for time-points 1,2,...,9.

### Usage in R

```r
site <- "https://github.com/MarcooLopez/Data_for_Lopez-Cruz_et_al_2020/raw/main"
filename <- "wheatHTP.E1.RData"

download.file(paste0(site,"/",filename), filename, mode="wb")
load(filename)

```
