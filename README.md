# stipw

## Inverse probability weighted parametric survival models with variance obtained via M-estimation

_stipw_ is a user-written Stata command, which performs an inverse probability weighted (IPW) analysis on survival data. The main advantage of stipw is that M-estimation is used to calculate the variance, which takes into account the uncertainty associated with the weight estimation. 

### Installation

stipw will soon be added to the SSC archive and can then be downloaded using:
```
ssc install stipw
```

Alternatively, _stipw_ can be pulled from GitHub. You will need to type the following at the beginning of your code before you can use _stipw_:
```
adopath ++ "<file_location>"       // Folder location of the saved stipw ado and help files
do "<file-location>/stipw.ado"
```

### Dependencies

_stipw_ requires the dependencies: _dm79_, _stpm2_ and _rcsgen_. These can be installed as follows:
```
net install dm79, from(http://www.stata.com/stb/stb56)
ssc install stpm2
ssc install rcsgen
```
Note that _stipw_ relies on _stpm2_ version 1.7.5 May2021 or later. You may need to update your version of _stpm2_ if you already have it installed.

### Method outline

_stipw_ begins by using logistic regression to model the treatment/exposure variable adjusting for the specified confounders. The propensity score is estimated and stabilised (default) or unstabilised weights are calculated. Stabilised weights require a second logistic regression model, where treatment is modelled with no covariates, in order to estimate the treatment prevalence. The data is then _restset_ with the weights (using _pw_ weights). A range of parametric models (modelled with _streg_ or _stpm2_) can be fitted to the weighted data. The default is to calculate the M-estimation variance estimator (as this appropriately takes into account the uncertainty associated with the weight estimation), although the standard robust variance estimator can also be provided. See the help file for more details.  

### Example code

* The help file provides example code.
* Code for an example IPW analysis can be found [here](https://github.com/Micki-Hill/stipw_sim_app/blob/main/Application/actg175_application.do).

### Presentations and publications

* Slides presented at the 2021 UK Stata conference can be found [here](https://www.statauk.timberlake-conferences.com/presentations).
* Manuscript of the methods is in draft.

Please report any errors you may find to Micki Hill, mh594@le.ac.uk.

