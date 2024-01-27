
# **SPREG**

# **SPREG : Regression Analysis of Secondary Phenotype Data in Case-Control Association Studies**

SPREG is a computer program for performing regression analysis of
secondary phenotype data in case-control association studies. Secondary
phenotypes are quantitative or qualitative traits other than the
case-control status. Because the case-control sample is not a random
sample of the general population, standard statistical analysis of
secondary phenotype data can yield very misleading results. SPREG
implements valid and efficient statistical methods, as described in Lin
DY, Zeng D. 2009, [Proper analysis of secondary phenotype data in
case-control association
studies](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2684820/pdf/nihms94335.pdf/?tool=pmcentrez),
[Genetic
Epidemiology](https://onlinelibrary.wiley.com/journal/10982272),
33:256-265.

## **GENERAL INFORMATION**

The software is written in C and built under 64-bit x86-based Linux. The
current release performs linear regression analysis of quantitative
traits and logistic regression of binary traits under the additive mode
of inheritance with or without environmental factors.

## **SYNOPSIS**

> **spreg**   infile   outfile   rate   nenv

All four program parameters are required and must be entered in the same
order as specified above.

## **PROGRAM PARAMETERS**

 

| Parameter | Description                                                |
|:----------|:-----------------------------------------------------------|
| infile    | Name of the input file                                     |
| outfile   | Name of the output file                                    |
| rate      | Disease rate                                               |
| nenv      | Number of environmental variables; 0 or a positive integer |

 

## **INPUT**

The program requires one input file. The input file contains text data
in a matrix format. Suppose there are *n* study subjects, *k* genes, and
*d* environmental variables. The input file is a (*k* + *d* + 2) by *n*
matrix, with columns representing study subjects, and rows conforming to
this format:

1.  Row 1 contains the primary phenotype of the study subjects. This
    should be the case-control status (1=case; 0=control). Missing
    values are represented by NA.

2.  Row 2 contains the secondary phenotype values of the study subjects.
    Their values must be numerical, and can be either binary or
    continuous. Binary values must be coded as 0 and 1; otherwise they
    will be treated as continuous. Missing values are represented by NA.

3.  If one or more environmental variables are to be included in the
    analysis, they must be row 3 through row (*d* + 2), with each row
    representing one environmental variable, where *d* is the total
    number of environmental variables. Values of environmental variables
    must be numerical. Missing values are represented by NA.

4.  All subsequent rows are genotypes of genes. Suppose there are *k*
    genes while the number of environmental variables is *d*, noting
    that *d* can be 0. Row (*d* + 3) corresponds to gene 1; row
    (*d* + 4) corresponds gene 2; … ; and row (*d* + *k* + 2)
    corresponds to gene *k*. Values of genotypes must be numerical.
    Genotype values other than 0, 1, and 2 are accepted. Missing values
    are represented by NA.

If the disease is rare, enter any number less than 0.01 for the disease
rate.

## **OUTPUT**

Computational results are written to the output file specified by the
user. For each gene, the output shows the maximum likelihood estimate of
the genetic effect (i.e., slope parameter in the linear model or log
odds ratio in the logistic model), its standard error, the
standard-normal test statistic and the (two-sided) p-value.

## **EXAMPLE**

The example files (can be downloaded in the DOWNLOAD section below)
includes an input file `demo.dat` and an output file `demo.out`. The
input file `demo.dat` contains the case-control status of 3000
individuals, a continuous secondary phenotype, two environmental
variables, and genotypes of 10 genes. The disease rate is 0.08.

Enter the command

> spreg demo.dat demo.out 0.08 2

to obtain the output file as given in `demo.out`. Its contents are

>  
>
> Gene_number    Estimate   Std_Error      Z_stat     p_value  
> 1   5.203e-03   8.509e-03   6.114e-01   5.409e-01  
> 2  -1.275e-03   5.514e-03  -2.312e-01   8.172e-01  
> 3  -3.067e-03   5.713e-03  -5.368e-01   5.914e-01  
> 4   8.081e-04   5.651e-03   1.430e-01   8.863e-01  
> 5  -1.198e-04   8.013e-03  -1.495e-02   9.881e-01  
> 6   2.148e-03   6.575e-03   3.267e-01   7.439e-01  
> 7   2.517e-03   7.245e-03   3.474e-01   7.283e-01  
> 8  -2.308e-03   5.975e-03  -3.864e-01   6.992e-01  
> 9  -2.384e-02   6.004e-03  -3.970e+00   7.178e-05  
> 10  -1.665e-02   6.257e-03  -2.661e+00   7.781e-03
>
>  

## **DOWNLOAD**

#### **SPREG 2.0 for 64-bit x86 based Linux \[updated May 18, 2011\]**

executable (zip archive) **»**
[spreg-2.0-linux.zip](http://dlin.web.unc.edu/wp-content/uploads/sites/1568/2013/01/spreg-2.0-linux.zip)

#### **Example files \[updated May 18, 2011\]**

zip archive **»**
[spreg-2.0-example.zip](http://dlin.web.unc.edu/wp-content/uploads/sites/1568/2013/01/spreg-2.0-example.zip)

## **REFERENCE**

Lin DY, Zeng D. 2009. [Proper analysis of secondary phenotype data in
case-control association
studies](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2684820/pdf/nihms94335.pdf/?tool=pmcentrez).
[Genetic
Epidemiology](https://onlinelibrary.wiley.com/journal/10982272),
33:256-265.

## **VERSION HISTORY**

 

<table style="width:99%;">
<colgroup>
<col style="width: 11%" />
<col style="width: 18%" />
<col style="width: 68%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Version</th>
<th style="text-align: left;">Date</th>
<th style="text-align: left;">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">1.0</td>
<td style="text-align: left;">April 22, 2008</td>
<td style="text-align: left;">First version released</td>
</tr>
<tr class="even">
<td style="text-align: left;">2.0</td>
<td style="text-align: left;">May 18, 2011</td>
<td style="text-align: left;"><ul>
<li><p><strong>New Features:</strong></p>
<ul>
<li><p>1) Allowing environmental factors in the model</p></li>
<li><p>2) Allowing genotype values to be other than 0, 1,<br />
and 2</p></li>
<li><p>3) New input file format</p></li>
<li><p>4) New command-line parameters</p></li>
<li><p>5) New example data</p></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>
