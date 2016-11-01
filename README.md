# Maelstrom example 

#### Simon van Heeringen <s.vanheeringen@science.ru.nl>

The notebook in this repository will reproduce the results from my poster at the Ninth Annual RECOMB/ISCB Conference on Regulatory & Systems Genomics meeting ([RSG with DREAM 2016](https://www.iscb.org/recomb-regsysgen2016)).

See the notebook here: [maelstrom_poster.ipynb](maelstrom_poster.ipynb).


Maelstrom is an ensemble algorithm that was developed with the goal to make differential regulatory motif analysis easy.
It takes as input a set of regions (for instance from ChIP-seq, ATAC-seq or DNaseI experiments) and measurements of two or more experiments (for instance log2-transformed, normalized read counts). 
Alternatively, you can provide labels, for instance from clustering.

This means your input data should look something like this:

```
loc	NK	Monocytes	T-cells	B-cells
chr12:93507547-93507747	3.11846121722	2.52277241968	1.93320358405	0.197177179733
chr7:38236460-38236660	1.0980120443	0.502311376556	0.200701906431	0.190757068752
chr10:21357147-21357347	0.528935300354	-0.0669540487727	-1.04367733597	-0.34370315226
chr6:115521512-115521712	0.406247786632	-0.37661318381	-0.480209252108	-0.667499767004
chr2:97359808-97360008	1.50162092566	0.905358101064	0.719059595262	0.0313480230265
chr16:16684549-16684749	0.233838577502	-0.362675820232	-0.837804056065	-0.746483496024
chrX:138964544-138964744	0.330000689312	-0.29126319574	-0.686082532015	-0.777470189034
chr2:186923973-186924173	0.430448401897	-0.258029531121	-1.16410548462	-0.723913541425
chrX:113834470-113834670	0.560122313347	-0.0366707259833	-0.686082532015	-0.692926848415
```

Or like this:

```
loc	cluster
chr15:49258903-49259103	NK 
chr10:72370313-72370513	NK 
chr4:40579259-40579459	Monocytes
chr10:82225678-82225878	T-cells 
chr5:134237941-134238141	B-cells 
chr5:58858731-58858931	B-cells 
chr20:24941608-24941808	NK 
chr5:124203116-124203316	NK 
chr17:40094476-40094676	Erythroblast
chr17:28659327-28659527	T-cells
```

Both these formats are tab-separated.

Maelstrom will run a variety of algorithms to predict discriminative motifs, and integrate these results using rank aggregation. 


## Prerequisites

GimmeMotifs (including Maelstrom) will only work on Linux and Mac OS X.
Before running this tutorial, make sure that [GimmeMotifs](http://github.com/simonvh/gimmemotifs) is installed and that the genomes are indexed. 
In addition you need [Jupyter Notebook](http://jupyter.org/).
The most straightforward way is to use [Anaconda](https://www.continuum.io/downloads).
    
### Install the latest version of GimmeMotifs using Anaconda:
    
```
$ conda install gimmemotifs=0.10.0b4 -c bioconda -c r
```

### Get the hg19 and mm10 genomes:

```
$ mkdir $HOME/genomes/
$ gimme genome $HOME/genomes/ hg19
$ gimme genome $HOME/genomes/ mm10
```

### Install jupyter

```
$ conda install jupyter
```

## Run the notebook

```
$ cd dir/where/you/cloned/this/repo/
$ jupyter nnotebo

