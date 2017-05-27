# Fig-SV
FSig-SV (Functionally significant structural variants) method identifies coding and non-coding elements significantly affected by deletion, insertion, duplication, inversion and translocation events. Output of the method is a list of coding and non-coding elements that are rearranged in more samples than expected randomly. 

Find genes with significantly rearranged coding and non-coding regions (FSig-SV):
Steps involved to get the p-value for genomic elements affected by SV:

	1- Untar the FSig-SV.tar.gz using the command
		tar -zxvf FSig-SV.tar.gz

	FSig-SV directory contains following sub-directories and files

	a) FSig-SV.R is the main R script to find genes with significantly rearranged CDS(coding sequence), promoter and enhancers. 
	  
	b) convert_format.sh script converts the format of ICGC data to FSig-SV.R compatible input format (see example.bed)

	c) input folder that contains all the required files for FSig-SV.R 
		-  example.bed is an example SV dataset in bed format (chr  BreakPoint1  BreakPoint2  SVtype  sampleID) 
		-  chr_arm_lengths.rds contains genomic information of chromosome arm lengths. 
		-  chr_regions_arm_width.rds contains genomic information of allowed regions avoinding gaps.
		-  encode.v16.drm.bed : encode defined enhancer region (DRM) in bed format. This file should be downloaded from the url 
		http://khuranalab.med.cornell.edu/tissue_specific_network/FSig-SV.tar.gz
		-  gencode.v16.cds.bed contains coding sequence for each gene defined using gencode V16.
		-  gencode.v16.promoter.bed contains promoters for different gene isoforms.

	d) Output of the program will be automatically saved in this folder

	Commands to run: 
	Rscript FSig-SV.R <input_SV_file> <iterations>
	example: Rscript FSig-SV.R input/example.bed 1000
	iterations refers to number of permutations of random shuffle.
NOTE: The program is compute intensive. High number of iterations will take more execution time. Default is 1000 iterations.

For any further queries or comments please contact: prd2007@med.cornell.edu or ekk2003@med.cornell.edu

