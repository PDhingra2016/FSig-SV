# Fig-SV
FSig-SV (Functionally significant structural variants) method identifies coding and non-coding elements significantly affected by deletion, insertion, duplication, inversion and translocation events. Output of the method is a list of coding and non-coding elements that are rearranged in more samples than expected randomly. 

Find genes with significantly rearranged coding and non-coding regions (FSig-SV):
Steps involved to get the p-value for genomic elemnets affected by SV:

	1- uncompressing the FSig-SV.tar.gz
		tar -zxvf FSig-SV.tar.gz

	FSig-SV directory contains following sub-directories and files

	a) FSig-SV.R : the main R script that compute to find genes with significantly rearranged CDS(coding sequence), promoter and enhancers. 
	  
	b) convert_format.sh :  scripts to convert the format of ICGC data to the FSig-SV.R compatible input format (see example.bed)

	c) input : folder that contains all the required files for FSig-SV.R 
		-  example.bed : SV dataset file in bed format (chr  BreakPoint1  BreakPoint2  SVtype  sampleID) 
		-  chr_arm_lengths.rds : genomic information of chromosome arm lengths in R object format. 
		-  chr_regions_arm_width.rds : genomic information of allowed regions avoinding gaps in R object format.
		-  encode.v16.drm.bed : encode defined enhancer region (DRM) in bed format
		-  gencode.v16.cds.bed : gene coding regions in bed format
		-  gencode.v16.promoter.bed : promoter regions in bed format

	d) output : folder that will contains the results 

	Command to run: Rscript FSig-SV.R <input_SV_file> <iterations>
	example: Rscript FSig-SV.R input/example.bed 1000
	iterations refers to number of permutations of random shuffle.
NOTE: the high number of iterations will lead to more execution time. Default is 1000 iterations.

