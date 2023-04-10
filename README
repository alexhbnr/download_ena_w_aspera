## Download sequencing data from ENA via ASPERA

This [Snakemake](https://snakemake.readthedocs.io/en/stable/) workflow allows to download sequencing
data from the European Nucleotide Archive using the ASPERA protocol. Next to downloading the
sequencing data, the pipeline will automatically calculate the md5sum hash of the downloaded files
and compare it against the expected hashes stored in the ENA database.

The pipeline requires four parameters as input that need to be provided via the `--config` parameter
of Snakemake:

  1. `samplelist`: a text file with the run accessions that need to be download, one per line
  2. `outdir`: the output directory for the downloaded files
  3. `slot`: the type of data to be downloaded [`fastq`, 'submitted', `sra`]
  4. `protocol`: the protocol to be used for downloading [`aspera`, `ftp`]
  5. `aspera_path`: the path to ASPERA installation folder that contains the sub-folders `bin` and
     `etc`

To start the pipeline, run `snakemake` with the following command.

snakemake --config samplelist="samplelist_test.txt" \
                   outdir="bams" \
                   slot="submitted" \
                   protocol="aspera" \
                   aspera_path="/usr/local64/opt/aspera/connect"
    -j 1 --resources downloads=1

To allow more than one task to be executed, increase the value of the parameter `-j`, accordingly.
In case more than one file should be downloaded at the same time, increase the number of parallel
download jobs by increasing the value for the parameter `downloads`.
