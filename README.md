# AquaGWAS-GUI
## [Download AquaGWAS](https://github.com/gdengchao/AquaGWAS/releases/download/V1.0/AquaGWAS_V1.0.zip)
## [Download test data](https://github.com/gdengchao/AquaGWAS/releases/download/V1.0/test_data.zip)

## Usage for GUI
**There are five modules in AquaGWAS:** 
1. PROJECT, 2. ASSOC, 3. MAN/QQ, 4. PCA/LD, 5. ANNOTATION

+ **PROJECT (Project setting)**   
    Select an appropriate output directory and set an easily distinguishable project name to which all AquaGWAS final output will be based.   

    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/project.png"/>
    </p>


+ **ASSOC (Association analysis)**   
1. Open input file    
    Click on the left side of the interface to open the required input file.  

2. Set tool and model    
    Select the appropriate analysis tool and model (plink: liear, logistic; gemma: LMM BSLMM; emmax: EMMA), gemma and emmax can click "**>>**" to set more tool-specific parameters.  

3. Set quality control parameters   
    Three basic parameters respectively are MAF (minor allele frequency)， MIND(SNPs with low genotype calls are removed) and GENO(individual with low genotype calls are removed). "**>>**" can be clicked to set parameters of LD fitering(window size, step length and r2 threshold).

4. Select phenotype      
    When the input phenotype data file contains multiple phenotype data, you can select the phenotype to be analyzed in the lower right corner of the interface. AquaGWAS will analyze each phenotype separately.   
    ![ASSOC](https://github.com/gdengchao/AquaGWAS/blob/main/resource/assoc.gif)

+ **MAN/QQ (Manhattan plot and QQ plot)**  
After association analysis, the p-value file will automatically open, click the "plot" respectively, obtain Manhattan and Quantile-Quantile plot.   
**Notice:** Make sure R is installed before plotting. If it is not installed, R can be installed using the following commands in Ubuntu:  
    >```   
    >   sudo apt install r-base   
    >```  
    and commands in CentOS:
    >```  
    >    yum install epel-release   
    >    yum install R    
    >```  
    ![MAN/QQ](https://github.com/gdengchao/AquaGWAS/blob/main/resource/man_qq.gif)

+ **PCA/LD (Principal component analysis and linkage disequilibrium)**   
        Both PCA and LD need to the genotype file, you can open genotype in the left side of interface.  
     **For PCA**, you can set the number of PCs and how many threads will run byGCTA.(Need R to get a plot,  installation method refer to #4)  
    ![PCA](https://github.com/gdengchao/AquaGWAS/blob/main/resource/pca.gif)   

    **For LD**, you can choose whether to select "By family" or not. When you select "By family", LD will be analyzed per family according to FID, and each family will get a result respectively.                
    ![LD](https://github.com/gdengchao/AquaGWAS/blob/main/resource/ld.gif)
 
    
+ **ANNOTATION (Structural annotation and functional annotation)**
1. annotaion  
    The module annotation contains structural annotation and fucntional annotation. The input files for  structual anntation are avinput, reference gene and reference sequence. The avinupt is a input file for annovar.
    The reference gene could be a gtf file or gff file, and reference sequence should be a .fasta file. In addition, you can offer a refGene.txt as reference gene and a refMrna.fa as reference sequence.   
    The input files for functional anntation are snp position and functional annotation reference database.     
    (We offered "*_refGene.txt", "*refGeneMrna.fa" and funcation annotation databse file of some species)  
    ![ANNOTATION](https://github.com/gdengchao/AquaGWAS/blob/main/resource/anno.gif)  
2. step  
    The "avinput" and "snp_pos" file can be generated from a ".vcf"(open in Genotype) and a p-value file of association analysis(open automatically after association analysis). The threshold is used for filtering SNP and getting significant SNP.  
    ![STEP](https://github.com/gdengchao/AquaGWAS/blob/main/resource/anno_step.gif)   
3. auqatic database  
    We have integrated 27 commonly used aquatic animal databases that can be used for gene annotation. The following links are available：    
    Link1:  链接：https://pan.baidu.com/s/1s9swL0XTKsn9k9R2z_w7JQ 提取码：lsqe    
    Link2:  [Google driver](https://drive.google.com/drive/folders/1w7uDlOZMj1O63FeFQ_KGc3vLBXJ_Sixk?usp=sharing)   
    Link3:  [TeraCLOUD](https://futtsu.teracloud.jp/share/1121fd0207dc8717)  


## Usage for CMD
For the use of the command line form, we recommend that you directly perform the basic setting operations in the GUI, copy the command generated by the graphical interface, and paste the command to the terminal to run. At this time, you need to pay attention to the path where AquaGWAS-CMD is located and the path of each input file need to be adjusted to the corresponding path at any time according to the running computer.  

**1. ASSOC， manhattan plot and QQ plot**   
    Manhattan plot and QQ plot will be generated directly after the ASSOC is over. The   parameters of the Manhattan graph need to be entered while entering the correlation analysis command.  
    ![CMD-ASSOC](https://github.com/gdengchao/AquaGWAS/blob/main/resource/cmd-assoc.gif)

**2. PCA**   
    ![CMD-PCA](https://github.com/gdengchao/AquaGWAS/blob/main/resource/cmd-pca.gif)

**3. LD**   
    ![CMD-ASSOC](https://github.com/gdengchao/AquaGWAS/blob/main/resource/cmd-ld.gif)

**4. Annotation**  
    ![CMD-ASSOC](https://github.com/gdengchao/AquaGWAS/blob/main/resource/cmd-anno.gif)

+ All the parameter of AquaGWAS-CMD and be list by command(Terminate opens in the directory AquaGWAS-CMD)
    > ```
    > ./AquaGWAS-CMD -h
    > ```
+ The detailed parameters are shown in the figure below:  
    ![CMD-option](https://github.com/gdengchao/AquaGWAS/blob/main/resource/cmd-options.png)

## Description of input file 

**1. Phenotype**  
Two options:  
    a. Single phenotype data file, file suffix：'.phe', file content：“FID IID PHE”, without header.  
    ![Single-pheno](https://github.com/gdengchao/AquaGWAS/blob/main/resource/single-pheno.png)  
    b. Multiple phenotype data file, file suffix: no '.phe', file content: "FID IID PHE1 ... PHEn", with header.  
    ![Multi-pheno](https://github.com/gdengchao/AquaGWAS/blob/main/resource/multi-pheno.png)  

**2. Genotype**   
    VCF, PED, TPED, BED  

**3. Map**  
    Corresponds to the Genotype file：MAP(PED), TFAM(TPED). It don't have to be input, the software automatically goes to the Genotype uniform file directory to read map file when not being entered.

**4. Covariate**  
    File content:"FID IID 1 Covar1 ... Covar n".   
    Note that the intercept has to be included, meaning that the third column is recommended to be 1 always, and the covariates needs to be included from the fourth column. The order of the individual IDs should conform to the phenotype files.     
    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/covar.png"/>
    </p>  

**5. Kinship**  
    It will automaticaly generate when use gemma and emmax, you can choose to open an old Kinship file generated by corresponding tools, in order to save time.  

**6. Assoc p-val file**  
    Result file generated by plink, gemma or emmax after association analysis.  

**7. AVINPUT**  
    Input file of annovar. File content: "CHR Start End Ref Ob"  
    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/avinput.png"/>
    </p>

**8. Ref gene**  
    gff, gtf or "*refGene.txt"  

**9. Ref seq**  
    fasta or "*refGeneMrna.fa"  

**10. SNP postion**  
    "snp_ID p-val CHR BP", without header    
    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/snp_pos.png"/>
    </p>

**11. Func anno ref**        
    a. Suffix: "**.funanno**"; 
    The first column is gene ID, the other columns is description of gene, without header.
    "Gene_ID Descrition_1 ... Descripton_n", each column separated by Tab.    
    b. Suffix: "**.ncbi.csv**";   
    With header, each column separated by comma, index by "Locus" and get information from clumn "Protein Name".   
    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/ncbi.png"/>
    </p>
    c. Suffix: "**.ensem.csv**";     
    With header, each column separated by comma, every data item in double quotes, index by the column "Gene stable ID" and get infomation from the column "Gene description".
    <p align="center">
        <img src="https://github.com/gdengchao/AquaGWAS/blob/main/resource/ensem.png"/>
    </p>

