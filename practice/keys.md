1. What directory are you in?
```
pwd #answer should be /home/<your ned-id>/unix_basic/practice
```
2. How many files are there in this directory?
```
ls | wc -l #answer should be 3
```
3. Make a directory in this directory and name it `answers`.
```
mkdir /home/<your ned-id>/unix_basic/practice/answers
```
or
```
mkdir answers #if you are in the directory /home/<your ned-id>/unix_basic/practice already
```
4. Get all the regions on chr1, put the redults in a file named chr1.bed and put the file in the directory `answers`.
Note: I am in the directory `/home/<my ned-id>/unix_basic/practice` to perform the following command. If you are in different directories, change the command accordingly. Or to be on the safe side, use absolute path.
```
grep -w "chr1"  E003-H3K27ac.narrowPeak > answers/chr1.txt
```
or
```
grep -w "chr1" ~/unix_basic/practice/E003-H3K27ac.narrowPeak > ~/unix_basic/practice/answers/chr1.txt
```
5. How many regions of interest are there on chr1?
```
wc -l ~/unix_basic/practice/answers/chr1.txt #answer should be 14940
```
6. How will you count the number of regions on chr1 without saving those regions to a file?
```
grep -w "chr1" E003-H3K27ac.narrowPeak | wc -l
```
7. How many unique chromosomes are there in the E003-H3K27ac.narrowPeak file?
```
cut -f 1 E003-H3K27ac.narrowPeak | sort -u | wc -l #answer should be 24
```
8. How many regions each chromosome has in the file?
There are many ways to do this. For example, if you know some programming, you can use `for` or `while` loops. Those loops will make the task much less tedious. However, for now, you can find each of the chromosomes individually.
```
grep -w "chr1" E003-H3K27ac.narrowPeak | wc -l #answer: 14940
grep -w "chr10" E003-H3K27ac.narrowPeak | wc -l #answer: 7466
grep -w "chr11" E003-H3K27ac.narrowPeak | wc -l #answer: 8007
grep -w "chr12" E003-H3K27ac.narrowPeak | wc -l #answer: 8498
grep -w "chr13" E003-H3K27ac.narrowPeak | wc -l #answer: 4698
grep -w "chr14" E003-H3K27ac.narrowPeak | wc -l #answer: 4968
grep -w "chr15" E003-H3K27ac.narrowPeak | wc -l #answer: 4864
grep -w "chr16" E003-H3K27ac.narrowPeak | wc -l #answer: 5269
grep -w "chr17" E003-H3K27ac.narrowPeak | wc -l #answer: 6790
grep -w "chr18" E003-H3K27ac.narrowPeak | wc -l #answer: 4033
grep -w "chr19" E003-H3K27ac.narrowPeak | wc -l #answer: 5890
grep -w "chr2" E003-H3K27ac.narrowPeak | wc -l #answer: 12990
grep -w "chr20" E003-H3K27ac.narrowPeak | wc -l #answer: 4081
grep -w "chr21" E003-H3K27ac.narrowPeak | wc -l #answer: 1811
grep -w "chr22" E003-H3K27ac.narrowPeak | wc -l #answer: 3036
grep -w "chr3" E003-H3K27ac.narrowPeak | wc -l #answer: 11257
grep -w "chr4" E003-H3K27ac.narrowPeak | wc -l #answer: 8893
grep -w "chr5" E003-H3K27ac.narrowPeak | wc -l #answer: 9315
grep -w "chr6" E003-H3K27ac.narrowPeak | wc -l #answer: 10353
grep -w "chr7" E003-H3K27ac.narrowPeak | wc -l #answer: 9431
grep -w "chr8" E003-H3K27ac.narrowPeak | wc -l #answer: 7428
grep -w "chr9" E003-H3K27ac.narrowPeak | wc -l #answer: 7077
grep -w "chrX" E003-H3K27ac.narrowPeak | wc -l #answer: 5466
grep -w "chrY" E003-H3K27ac.narrowPeak | wc -l #answer: 306
```
9. How would you sort the file answers/chr1.bed based on the second column in ascending order (from small to large)?
```
sort -k 2 -n answers/chr1.txt
```
To see the head of the results, you can do
```
sort -k 2 -n answers/chr1.txt | head
```
10. Which region on `chr1` has the highest `-log10(q-value)`?
```
sort -k 9 -n answers/chr1.txt | tail
```
or
```
sort -k 9 -n -r answers/chr1.txt | head #sort in numerical (-n) and in reverse order (a.k.a. decending order) (-r)
```
The answer is
```
chr1    62902073        62903462        Rank_1  1859    .       49.55787        185.91341       176.42285       497
```
