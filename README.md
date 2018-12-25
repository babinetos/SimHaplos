# SimHaplos
Software that simulates haplotypes for case/control studies. The software allows for GxE interactions in the risk of the binary trait and also allows for differences int he haplotype frequencies between the two groups formed by the levels of a binary covariate.


This is a beta version of the simulate_dep software for simulating hyplotype
data fo haplotype studies under a given GxE interaction model. This
software is copyright Swati Biswas and licensed under the GNU GPLv3. 
I may be contacted by email at Swati.Biswas@utdallas.edu. Following are
some instructions on compiling and running the software.

COMPILING:

All code is written in C and should compile on any platform
with a compliant compiler. The Makefile assumes gcc is installed. To 
compile descend int to src subfolder and type "make" from the command line. 
This will create a binary executable file called "simulate_dep".

RUNNING:

The simulate_dep program requires an input file with the information of the simulation model 
(for an example see the provided infile.txt)  and the name of an output file where the 
simulated data will be stored. Both files MUST be specified using command line arguments. 
The program can be run by typing the following on the command prompt:

simulate_dep infile.txt out.txt


FILE FORMATS:

infile.txt: 

The program assumes that the study includes a binary covariate which may or may 
not be related with the frequency of the haplotypes. 

The following is an example of the infile along with explanations of what info
is provided in each line. NOTE: do not include the comments after the # as the 
program will not work appropriately.

6	     	      # Number of Haplotypes inthe population	
5		      # Number of SNPs in the haplotype block 
1000		      # Number of cases generated
1000		      # number of Non-cases generated
0.1		      # Baseline risk
0		      
1 0 0 1 1 	      # 1st haplotype; columns correspond to SNPs; 1-Major Allele 
0 1 0 1 1  	      # 2nd haplotype; columns correspond to SNPs; 1-Major Allele 

0 0 1 0 0 	      # 3rd haplotype; columns correspond to SNPs; 1-Major Allele  

0 0 0 1 1 	      # 4th haplotype; columns correspond to SNPs; 1-Major Allele  

0 0 0 0 0 	      # 5th haplotype; columns correspond to SNPs; 1-Major Allele  

0 1 1 0 0 	      # 6th haplotype; columns correspond to SNPs; 1-Major Allele 

                  # By default the last haplotype is considered the base 
                  
0.35 0.25  1	    # Frequencies of the 1st haplotype in each subgroup defined by covariate

     	   	        # the third value provides the ODDS RATIO increase of the haplotype 
                  
		              # with repect to the BASELINE risk
                  
0.01 0.005  3	      # Info on the 2st haplotype

0.01 0.02  1	      # Info on the 3rd haplotype

0.03 0.28  1	      # Info on the 4th haplotype

0.05 0.17  1	      # Info on the 5th haplotype

0.55 0.275  1	      # Info on the 6th haplotype

0.5 1	    	        # Covariate frequency and ODDS RATIO increase of the 1-value over the 

    		            # BASELINE risk 
                    
1		      # GxE ODDS RATIO increase of Haplottype 1 with Covariate level 1

1		      # GxE ODDS RATIO increase of Haplottype 2 with Covariate level 1

3		      # GxE ODDS RATIO increase of Haplottype 3 with Covariate level 1

1		      # GxE ODDS RATIO increase of Haplottype 4 with Covariate level 1

1		      # GxE ODDS RATIO increase of Haplottype 5 with Covariate level 1



Outfile:

NOTE: The program will give you a segmentation error if you do not provide a 
outfile name.

1st Row contains the headings of the columns:

Subsequent rows contain the affection status, covariate value, and genotypes for the
simulated sample. Each row corresponds to a person. 

Columns contain the following iformation:

1st: 		    Affection Status
2nd:		    Covariate value
3rd and 4th:	    Alleles at SNP 1
5th and 6th:	    Alleles at SNP 2
...

