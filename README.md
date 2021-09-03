# WPV
A SAS macro for weighted pseudo-values

## Overview
WPV is a SAS macro to calculate and analyse weighted pseudo-values in case of a latent binary covariate that emerges over time as proposed by Mittlböck, Pötschger and Heinzl (2021).

## Details
Calculation and analysis of weighted pseudo-values (WPV) is motivated by investigating the impact of allogeneic stem cell transplantation on childhood leukaemia. The approach compares long-term survival of two cohorts defined by the availability or non-availability of suitable donors for stem cell transplantation. A patient’s cohort membership becomes known only after completed donor search with or without an identified donor. If a patient suffers an event during donor search, stem cell transplantation will no longer be indicated. In such a case, donor search will be ceased and cohort membership will remain unknown. 
By considering the probability that a donor would have been identified after ceasing of donor search, weights for common pseudo-values are defined. 
A weighted generalized linear model is used to estimate survival probabilities at a predefined time point of interest for both groups and their cumulative hazard ratio (cHR) together with their confidence intervals. 

The Macro call for the simulated example data set named *simbsp_a_1000_05* would be 
> libname simdat '*Data_Path*'; 
> <br> %include "*Macro_Path*\WPV_SAS_Macro.sas"; 
> <br> %WPV(data=simdat.simbsp_a_1000_50, td_time=binary_time, surv_time=time, surv_event=event, tsearch=3, tstar=5, result_out=result_out); 

for an analysis time point at 5 years (t*) for the pseudo-values and for a maximum time to identify the group membership of 3 years.
<br> *Data_Path* should be replaced by the path where the data set is stored and *Macro_Path* has to be replaced by the path where the SAS macro is stored.


## References
* Mittlböck M, Pötschger U. and Heinzl H.: Weighted pseudo-values for partly unobserved group membership in paediatric stem cell transplantation studies. Stat Methods Med Res 2021; to appear.
* Andersen PK and Pohar Perme M. Pseudo-observations in survival analysis. Stat Methods Med Res 2010; 19: 71–99.
