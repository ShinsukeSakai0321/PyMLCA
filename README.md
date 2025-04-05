# PyMLCA
## Software for Generalized Matrix-based LCA and Reliability Based LCA
#### Shinsuke Sakai   
 Emeritus Professor, The University of Tokyo   
 Visiting Professor, Yokohama National University

 ### Overview
On this site, we provide python software code required for general-purpose matrix-based LCA analysis and LCA based on reliability design. Algorithm for sensitivity analysis using perturbation method is based on the theory shown by Sakai and Yokoyama[1]. 
Should any required packages be missing during execution, please install them accordingly. When publishing results obtained using the software provided on this site, please be sure to include a citation to this site.

[1][Shinsuke Sakai and Koji Yokoyama. Formulation of sensitivity analysis in life cycle assessment using a
perturbation method. Clean technologies and environmental policy, Vol. 4, No. 2, pp. 72–78, 2002.](https://link.springer.com/article/10.1007/s10098-002-0150-2) 

### Procedure
1. Download all the files from this site.
1. Create a folder to store inventory data. As an example, the folder named 'SandwichPackage' is already created.
1. Save the inventory data to be analyzed in that folder.
1. Import PyMLCA module using 'import PyMLCA as pm' command.
1. Create an instance to manage the analysis using 'dp=pm.DesignProcess()' command.
1. From here on, use the created instance to perform the intended analysis.

### Operation check
The following describes the method for checking when using the inventory data in the SandwichPackage folder.

First, create an instance and define the inventory data folder.
```python
import PyMLCA as pm
dp=pm.DesignProcess()
path='./SandwichPackage'
dp.SetDfFromPath(path)
```
Next, perform a matrix-based LCA.
```python
solution,surplusFlow,loadValue=dp.SimpleAnalysis()
```
Confirm the created coefficient matrix.
```python
print(dp.rbld.mlca.coefficientMat)
```
Display the solution of the process values.
```python
print(solution)
```
Display the names of the environmental impacts and their solutions.
```python
flowName,b,loadName=dp.GetName()
print('Names of the environmental impacts=',loadName)
print('Their solutions=',loadValue)
```
Calculation of sensitivity matrix.
```python
i=0
print('Calculation of sensitivity matrix for environmental load:',loadName[i])
print(dp.rbld.mlca.Smat(i))
```
Example for reliability based design for LCA in sandwich packages is written in 'Example.md'. Please trExample for reliability based design for LCA in sandwich packagesy and check it.

### File details
|file |description |
|-----------|-----------|
| PyMLCA.py   | Package for matrix-based LCA and sensitivity analysis  |
| LimitState.py | Package for reliability analysis|
| Kriging.py| Package for Kriging analysis|
|./SandwichPackage | folder which have inventory data for Sandwich Packages|
| Example.md| Example for reliability based design for LCA in sandwich packages|






