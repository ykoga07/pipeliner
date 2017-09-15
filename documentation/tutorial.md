## Nextflow Tutorial
#### Pre-requisites
Pipeliner requires Java, Nextflow, and Anaconda for implementation. All other tools for implementation are wrapped in the conda environment described below. 

*1. Download Nextflow*

Make sure you have Java 7/8 installed and then install Nextflow to a working directory. Test the Nextflow executable before continuuing.
```bash
java -version
cd path/to/wd
curl -s https://get.nextflow.io | bash
./nextflow run hello
```

*2. Download Conda*

`Conda` is available through [Anaconda](https://www.continuum.io/downloads) and [Miniconda](https://conda.io/miniconda.html). 

*Note that Anaconda comes pre-packaged with a Python distribution. Make sure you download the Python 2.7 version to ensure compatability with all packages used throughout the RNA-seq workflow. You will install Python 2.7 explicitly if you choose miniconda.*

*3. Create Conda Environment*

If this is your first time working with conda, you may need to edit your configuration paths to ensure anaconda/miniconda is invoked when calling 'conda'.
```bash
gedit ~/.bashrc # linux
gedit ~/.bash_profile # osx
```
Create a conda environment and install the necessary bioconda packages. 
```bash
conda create -n pipeliner python=2.7
source activate pipeliner
conda install -c bioconda perl-threaded fastqc trim-galore star multiqc samtools rseqc stringtie
 ```
 
#### Running the pipeline
*4. Run Test Data*
Download test data from this repository and test it on Nextlfow. Currently need to modify explicit paths to fastq read files, this will be changed soon.

After cloning the repository, change paths in the following locations:  
pipeliner/Gallus_gallus/nextflow.config  
pipeliner/Gallus_gallus/ggal_date/ggal_alpha.csv  

```bash
git clone https://github.com/anfederico/pipeliner
cd pipeliner/Gallus_gallus
curl -s https://get.nextflow.io | bash
./nextflow main.nf -c nextflow.config
```

Pipeliner consists of a main nextflow script parametrized using a configuration file. The configuration file includes all parameters necessary to run the pipeline including  parameters to direct the path of files and results, as well as selecting specific tools and processes to run. All files necessary to run this example is in the folder *Gallus_gallus*.