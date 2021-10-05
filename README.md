# NSweepPlus
An SPSS macro to identify collinear and low variance variables and use the rest in a PCA

About NSweepPlus

NSweepPlus is an SPSS macro that reads in a set of variables from an SPSS system file and identifies variables that have very low variance (<CRIT), and variables that are collinear with one or more variables, or a combination of them, on the set of variables (with residual variance <CRIT after other variables have been accounted for). The collinearity is analyzed in the order in which the variables are specified in the parameter VARS. For example, when analyzing variables Var1, Var2 and Var3, where Var1 and Var3 are collinear, it will identify Var3 as collinear with the previous variables. If the variables are entered as Var3, Var2 and Var1, it will identify Var1 a collinear.

With the set of variables that are not colinear and do not have low variance, it conducts a principal components analysis, creates principal component scores and saves them to a file. 

NSweepPlus produces as output a list of all the variables specified for the analysis, with a column indicating if the variable had low variance (LoVariance = 1) or if the variable was collinear with the previous variables in the analysis (IsCollinear = 1). It also produces a file with the principal component scores, and a summary file for the principal components with information about the amount of variance accounted for by each of them.

Due to the nature of the analysis performed by NSweepPlus, all the variables specified in the analysis must be numeric, and these must not be any missing values, either system missing values or user defined system missing values.  

Sampling weights, when available, can be used for the analysis, and you can also select and work with a subset of the data.

NSweepPlus identifies low variance and collinear variables following these steps: 

1.	Creates a variance-covariance matrix with the data

2.	Identifies variables with low variance

3.	Uses the SWEEP operator on the variance-covariance matrix, column by column, skipping a column when the pivot for the matrix is very small (<CRIT), and identifying the variable for this column as collinear. The variables are swept in the order in which they were specified in the VARS parameter.
