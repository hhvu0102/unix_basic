## Bioinformatics and Computational Biology Programming Workshop 2021
# Basic UNIX Totorial - Practice Exercise

In this section, we will be practicing using UNIX commands to explore some real data (well, the data in the lecture section was real too).

The data supplied here, E003-H3K27ac.narrowPeak.gz, is a narrow peak file downloaded from [The Roadmap Epigenomes Project](https://egg2.wustl.edu/roadmap/web_portal/index.html). Briefly, it contains the regions of interest in H1 embryonic stem cells. The file is in a format called `narrowPeak`. The first column of the file is the chromosome (in the form `chr*`), the second column is the start position of the region, and the third column is the stop position of the region. The other columns can be read about [here](http://genome.ucsc.edu/FAQ/FAQformat.html#format12). Also, the general file format is called `bed`, you can read about it on the same website.

You can see that the data here has a filename extension of `.gz`. It means the data had been compressed. To decompress the file, do the following command:
```
gzip -d E003-H3K27ac.narrowPeak.gz
```

Wonder what `-d` means? You can read about it (and other options of `gzip`) with the command `man gzip`.

After running `gzip -d`, the file is decompressed, and you can take a look at it using `head`, `tail`, or `less`. For example:
```
head E003-H3K27ac.narrowPeak 

chr1	62902073	62903462	Rank_1	1859	.	49.55787	185.91341	176.42285	497
chr1	167188355	167189834	Rank_2	1720	.	40.23876	172.03049	163.95490	1285
chr3	52321759	52322314	Rank_3	1632	.	38.65456	163.21417	155.62671	178
chr12	2112635	2113682	Rank_4	1606	.	43.39093	160.68999	153.20804	857
chr17	37843581	37845970	Rank_5	1597	.	46.80020	159.78378	152.31027	636
chr22	41487757	41489245	Rank_6	1563	.	50.80712	156.38486	149.09296	149
chr7	150096960	150103429	Rank_7	1522	.	39.38457	152.20432	145.02338	2985
chr3	143689453	143692088	Rank_8	1521	.	43.07797	152.10539	144.92659	1297
chr7	131288334	131290206	Rank_9	1519	.	41.70934	151.93806	144.76556	1569
chr7	99006271	99006540	Rank_10	1510	.	36.43667	151.02107	143.87294	121
```

1. What directory are you in?
2. How many files are there in this directory?
3. Make a directory in this directory and name it `answers`.
4. Get all the regions on `chr1`, put the redults in a file named `chr1.bed` and put the file in the directory `answers`.
- Make sure you get only `chr1`, not `chr11`, `chr12`, etc.
- Hint: look at the manual page `man grep`. What option should you use?
5. How many regions of interest are there on `chr1`?
6. How would you sort the file `answers/chr1.bed` based on the second column in ascending order (from small to large)?
- Hint: If the first few lines of the results after `sort` look like this:
```
chr1	10002662	10003327	Rank_15426	221	.	9.18838	22.17389	19.14895	378
chr1	10003568	10003897	Rank_21511	168	.	8.83023	16.86713	14.04075	117
chr1	10003947	10004066	Rank_166325	20	.	2.06458	2.02596	0.35051	2
chr1	100066302	100066419	Rank_136863	36	.	3.20236	3.63083	1.59659	58
chr1	10010655	10010961	Rank_58658	71	.	4.43577	7.13862	4.78478	121
```
It means you are sorting the second column alphabetically. We do not want to sort alphabetically.
