# Read Alignment

Read Alignment is the process of comparing short reads with a reference genome to find the best-matching position.
**BWA** is a fast and accurate tool for short alignment, and **JBrowse** can view the result of the alignment in Galaxy.

## Step 1: BWA-MEM
- In the Tools panel search bar, type **BWA** and under the **Mapping** section, select **Map with BWA**
- Under **Will you select a reference genome from your history or use a built-in index?** select **Use a genome from history and build index**.
- Under **Use the following dataset as the reference sequence** select **1:genome (as fasta)**
- Under **Select input type** select **Paired fastq collection** 
- Under **Select a paired collection** select **3: Pair-end data (fasterq-dump)**
- Your choices will look like this:

<img src="../img/align/bwa.png" width="800">

- Click **Execute**


## SAM format
BWA produces a file in Sequence Alignment Map (SAM) format or the compressed version BAM.

<img src="../img/sam_format.jpeg" width="800">

[Image Source](www.samformat.info)


## View bam file using JBrowse

- In the **Tools** panel search bar, type **JBrowse** and select **JBrowse genome browser**
- Under **Reference genome to display** select **Use a genome from history**
- Under **Select the reference genome** select **1: genome (as fasta)**

- Next we'll add two Track groups, each with an annotation track
  - Under **Track Group** click **Insert Track Group**
  - Under **Track Category** type “bam files”
  - Click **Insert Annotation Track**
  - Select track type **BAM Pileups** and under **BAM Track Data** click the folder icon and select the list **RNA STAR on collection: mapped.bam**
  - Again, click **Insert Track Group**
  - Under **Track Category** type “genes”
  - Click **Insert Annotation Track**
  - Select track type **GFF/GFF3/BED Features** and under **GFF/GFF3/BED Track Data** select **hg38_genes.bed**.

- Finally, run the job:
  - Scroll down and click **Execute**.
  - Once the job is complete (green) click the eye icon to view the data.
  - In the **Available Tracks** panel select the HIV and Mock samples from 12 hr, as well as the bed file.

<img src="../img/jbrowse_available_tracks.png" width="200">

- We'll zoom in on one gene **MYC**. To do this, click on the search bar to the left of the **Go** button and type `chr8:127735434-127742951` 
- The bam tracks will show the reads that align to the region for each sample. 
- The color will show whether the read aligns to the + or –strand and grey lines show splice regions where a read spans an intron. 
The gene track at the bottom called **hg38_genes.bed** will show 6 features of EGR1, by clicking on them you will be able to see the different feature types (exon, CDS, start_codon, stop_codon).

<img src="../img/jbrowse_myc.png" width="900">

[Previous: Process Raw Reads](02_Process_raw_reads.md)
