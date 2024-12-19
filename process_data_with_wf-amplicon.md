Plan to use nextflow epi2me to process fastq_pass files output from MinION. For example using _Ceratobasidium theobromae_ _HD_ amplicon barcode24.

``
mkdir HD-amplicons
mkdir HD-amplicons/fastq
cd HD-amplicons/fastq
ln -s /var/lib/minknow/data/NLRs_Cocoa_291024/NLRs_Cocoa/20241029_1210_MN42941_FAX75472_800d4df6/fastq_pass/barcode24 barcode24
``

Move the reference sequence into the directory. Instead of full Sulawesi derived genome (GCA_009078325.fa), use the 5kb plus/minus sequence regions flanking the HD allele.

``
mv HD_5kb_flanking.fa HD-amplicons/
``

Linked directory looks like this.

``
lab-MS-7D78:~/temp/NLR_HD_amplicons$ ls -lhrt /var/lib/minknow/data/NLRs_Cocoa_291024/NLRs_Cocoa/20241029_1210_MN42941_FAX75472_800d4df6/fastq_pass/barcode24/
total 6.4M
-rw-rw-r-- 1 minknow minknow 142K Oct 29 12:23 FAX75472_pass_barcode24_800d4df6_088665c8_0.fastq.gz
-rw-rw-r-- 1 minknow minknow 146K Oct 29 12:34 FAX75472_pass_barcode24_800d4df6_088665c8_1.fastq.gz
-rw-rw-r-- 1 minknow minknow  93K Oct 29 12:44 FAX75472_pass_barcode24_800d4df6_088665c8_2.fastq.gz
-rw-rw-r-- 1 minknow minknow 115K Oct 29 12:53 FAX75472_pass_barcode24_800d4df6_088665c8_3.fastq.gz
-rw-rw-r-- 1 minknow minknow  68K Oct 29 13:05 FAX75472_pass_barcode24_800d4df6_088665c8_4.fastq.gz
-rw-rw-r-- 1 minknow minknow 136K Oct 29 13:13 FAX75472_pass_barcode24_800d4df6_088665c8_5.fastq.gz
``
etc.

Now run wf-amplicon v1.1.3-g8f9a298.

``
nextflow run epi2me-labs/wf-amplicon \
--fastq 'HD-amplicons/fastq/barcode24/' \
--reference 'HD-amplicons/HD_5kb_flanking.fa
``

The workflow output looks like this:
https://htmlpreview.github.io/h?ttps://github.com/peritob/HD-amplicon-processing/blob/main/wf-amplicon-report.html
