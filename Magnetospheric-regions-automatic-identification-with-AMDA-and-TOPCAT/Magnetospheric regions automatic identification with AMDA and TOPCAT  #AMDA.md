###Magnetospheric regions automatic identification with AMDA and TOPCAT	
#AMDA-TOPCAT use case
[Change Log](#Log)  
[Science Use Case](#Science Use Case)  
[Goals](#Goals)  
[Steps](#Steps)  
[References](#References)



<h2 id="Authors">Authors</h2>

V. Génot – October 2012 – V2  
His email:  

<h2 id="Log">Change Log</h2>

|Version|Name|Note|
|---|---|---|
|1|[Keyuan Yin](https://github.com/megadiesel705)|First converted from [this site](http://typhon.obspm.fr/VESPA-tutorials/docs/AMDA-TOPCAT_Magnetospheric_regions_automatic_identification.pdf)|

<h2 id="Science Use Case">Science Use Case</h2>

•  Based on Jelinek et al., JGR 2012 (paper1)  

<h2 id="Goals">Goals</h2>

Goal :  


–  Identify bow shock and magnetopause  


–  AMDA conditional parameters  


<h2 id="Steps">Steps</h2>

**Magnetospheric region identification in Paper1**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/1_.png" width="500" alt="1">  

**THEMIS A magnetospheric sampling over ~3 years**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/2_.png" width="500" alt="2">  

Magnetospheric regions  
*Jelinek et al., JGR 2012*  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/3_.png" width="500" alt="3">  

**Magnetospheric Regions**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/4_.png" width="500" alt="4">  

**Bow shock and magnetopause identification**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/5_.png" width="500" alt="5">

In both case, each bin represents the probability (<1) for this location to be in the magnetosheath  
*Jelinek et al., JGR 2012*  

**Step by step AMDA–TOPCAT analysis  

•  define rB and rn in AMDA (create new parameters, see slide for exact definition)  
&nbsp;&nbsp;•  time delay between ACE and THEMIS A is taken constant  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• forinstancesee http://cdpp-amda.cesr.fr/DDHTML/HELP/delay.html  
•  in AMDA : in the « Download Results » window choose « Send to TOPCAT »  

**Step by step AMDA–TOPCAT analysis
Use of AMDA conditional parameters  

•  define the solar wind ram pressure pSW shifted to THEMIS A  
&nbsp;&nbsp;•  time delay may be taken as 4000s as before   
&nbsp;&nbsp;• pSW=1.67e-6nACEVACE^2  
•  define a new (conditional) parameter : flag_msh

￼**Transfer via SAMP (same procedure as before)**  

•  the table is loaded into TOPCAT  
•  adjust binning as necessary  

**Parameter definition in AMDA**  
```
r_n = n_i_tha/shiftT_(sw(0),4000)  
```

```
r_b = bs_tha(3)/shiftT_(imf(3),4000)  
```

```
p_sw = shiftT_(sw(0)*sw(1)*sw(1),4000)*1.67e-6
```

```
flag_msh = (n_i_tha/shiftT_(sw(0),4000)+bs_tha(3)/shiftT_(imf(3),4000) > 4.) & (bs_tha(3)/shiftT_(imf(3),4000) - 10.*n_i_tha/shiftT_(sw(0),4000) <0.)
```

flag_msh value is either 1 (THEMIS A is in the magnetosheath) or 0  

**Time delay between ACE and THEMIS A**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/6_.png" width="500" alt="6">  

```
It is computed along the XGSE direction : T=|XACE-XTHEMIS_A|/VSW
```

**Time Dalay**  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/7_.png" width="500" alt="7">  

Here the delay T varies much more, a « banded » delay could be adopted (not implemented here) with conditional parameters :  

```
```

```
```


```
```

*In AMDA a conditional parameter P is such that P=1 if P is true

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/8_.png" width="500" alt="8">  

**Perspectives**  
• Use this procedure to deduce bow shock and magnetopause models  


Using the binning TOPCAT functionality for density map  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/9_.png" width="500" alt="9">  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/10_.png" width="500" alt="10">  

<img src="https://raw.githubusercontent.com/megadiesel705/tutorials/master/Magnetospheric-regions-automatic-identification-with-AMDA-and-TOPCAT/img/11_.png" width="500" alt="11">  

<h2 id="References">References</h2>

Please refer this tutorial to the [original version](http://typhon.obspm.fr/VESPA-tutorials/docs/AMDA-TOPCAT_Magnetospheric_regions_automatic_identification.pdf)





