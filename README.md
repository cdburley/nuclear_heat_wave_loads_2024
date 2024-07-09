# ntp_heat_wave_loads
This repository houses the raw data and processing scripts to create the hourly load time series by 
Balancing Authority for the NTP project. Data are scaled to match the 2035 annual total loads data by BA. 
The future loads for different weather years are based on the Total ELectricity Loads (TELL) model.

## Input Files
The input data needed to recreate this process is stored in the [data](data/) directory.

## Output Files
The output of this processing is stored in the [data](data/) directory. Original datasets for the WECC only use the 
filename format: "TELL_Loads_2035_Based_on_YYYY_Weather_With_Climate_Change.csv". Data for the WECC and EIC combined 
uses the filename format: "TELL_EIC_WECC_Loads_2035_Based_on_YYYY_Weather_With_Climate_Change.csv"

## Summary Plots
Quick-look plots analyzing the data are stored in the [plots](plots/) directory.

## Notes
1) In the WECC loads in CISO, IPCO, NEVP, and PACE are modeled as a whole in TELL but are separated in GridView. To 
create the data for these BAs I used the whole load simulated by TELL and distributed it to the subregions within the 
BA using the annual total load in each subregion to portion out the TELL loads. Those subregions will have different the
same hour-to-hour variability but different magnitudes depending on their total load fractions.
2) In the EIC loads in FMPP, FPL, MISO, PJM, SOCO, SWPP, and TVA are modeled as a whole in TELL but are separated in 
GridView. I used the same technique to subdivide the loads as I did in the original WECC data workflow.
3) TELL does not model BAs in Canada or Mexico. For BAs in those countries (CFE, IESO, TE, NB, NS, CORNWALL, NF, BCHA, 
and AESO) I used the raw time series from the WECC+EIC Gridview file that Kostas passed to me.
4) There are some regions that have no mapping to BAs modeled by TELL. For those regions I used the raw time series from 
the WECC+EIC Gridview file that Kostas passed to me. Those BAs are SETH, SERU, SEHA, IPP-REL, MH, TH_Mead, TH_Malin, 
SPC, TH_PV, OSC, PS, MPW, GLH, CPLW, YAD, WECC, and WBDC-WECC. Many of these regions have 0 loads in the GridView file.

## Mapping Files
Two files describing the BA mapping between TELL and Gridview are provided in the [data](data/) directory. The file 
'BA_Mapping.xlsx' shows how the names match up and which BAs have subregions. The file 
'Final_EIC_WECC_BA_Crosscheck.xlsx' goes through the WECC+EIC Gridview file that Kostas passed to me column-by-column 
to make sure that each region expected in the file is accounted for in my technique using the TELL model.

## Citations
Any use of this data in a publication, presentation, or report should use the following citations. Please contact 
Casey Burleyson (casey.burleyson@pnnl.gov) prior to any reuse of the data.
>
**Citation for the TELL model**
>
McGrath et al., (2022). tell: a Python package to model future total electricity loads in the United States. Journal of Open Source Software, 7(79), 4472, https://doi.org/10.21105/joss.04472
> 
**Citation for the underlying weather data**
>
Burleyson, C., Thurber, T., & Vernon, C. (2023). Projections of Hourly Meteorology by Balancing Authority Based on the IM3/HyperFACETS Thermodynamic Global Warming (TGW) Simulations (v1.0.0) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/1960530
>
Jones, A. D., Rastogi, D., Vahmani, P., Stansfield, A., Reed, K., Thurber, T., Ullrich, P., & Rice, J. S. (2022). IM3/HyperFACETS Thermodynamic Global Warming (TGW) Simulation Datasets (v1.0.0) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/1885756
