# Processing Strand-seq data

## Installation

```
git clone --recursive https://github.com/friendsofstrandseq/mosaicatcher.git
cd mosaicatcher
make
./src/main
```

If external dependencies ([boost](http://www.boost.org/) >= 1.63 and [HTSlib](https://github.com/samtools/htslib) >= 1.2.1)
are already installed, you can checkout without `--recursive`. Here is an example using easybuild:

```
git clone https://github.com/friendsofstrandseq/mosaicatcher.git
cd mosaicatcher
module load Boost
module load HTSlib
make
./src/main
```


## Strand-seq read counting and generation of QC plots

Mosaicatcher counts Strand-seq reads and classifies strand states of each chromosome in each cell
using a hidden Markov model.

Choose between bins of fixed width (`-w`) or predefined bins (`-b`).

```
./src/main -o counts.txt.gz -i counts.info -x data/exclude/GRCh38_full_analysis_set_plus_decoy_hla.exclude -w 200.000 cell1.bam cell2.bam [...]
```

To generate QC plots from these tables run

```
Rscript R/qc.R counts.txt.gz counts.info counts.pdf
```

