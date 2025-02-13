# Title of Dataset: Data from: Bacterial predation of a fungal wheat pathogen: Prelude to experimental evolution of enhanced biocontrol agents
---

##  General Information

Author information:

Corresponding author (first author):
Name: Sabrina A. Eisner
Institution: ETH Zurich, Switzerland
Email: sabrina.eisner@env.ethz.ch

Co-author:
Name: Francesca Fiegna
Institution: ETH Zurich, Switzerland

Co-author:
Name: Prof. Bruce McDonald
Institution: ETH Zurich, Switzerland

Co-author:
Name: Prof. Gregory J. Velicer
Institution: ETH Zurich, Switzerland

Geographic location of data collection: Zurich, Switzerland

Funding sources that supported the collection of the data: ETH Grant ETH-25 21-2

## Data and File Overview
For best understanding of the dataset, it is recommended to read it accompanied to the paper ‘Bacterial predation of a fungal wheat pathogen: Prelude to experimental evolution of enhanced biocontrol agents’ in Plant Pathology (doi: 10.1111/ppa.13716). The purpose of the data was to assess *Myxococcus xanthus* growth on *Zymoseptoria tritici* and to assess *Z. tritici* population reduction caused by the presence of *M. xanthus*. The experimental setup lets *Z. tritici* grow on blended and autoclaved wheat straw for a specified amount of time before different concentrations of *M. xanthus* are added on top. This setup was repeated for four additional cycles by transferring different dilutions of the *M. xanthus* population onto a fresh set of flasks with straw and *Z. tritici*. In the second experiment, *Z. tritici* population size was tracked at day 0 and after seven days of growth together and in the absence of two different *M. xanthus* densities in two different environments (straw and TPM hard agar). We were able to show that presence of any of the two *M. xanthus* densities tested significantly reduces *Z. tritici* population size over the duration of one week of growth in both environments, with the higher density of *M. xanthus* reducing it ~80% on straw and >99% on TPM hard agar.
In the following part, files will be grouped based on the figure they belong to in the paper mentioned above.



## Description of the Data and file structure

### Figure 1
**Files:** Data_Fig_1_and_S1.xslx, 1A5_5d.xslx, 1A5_12d.xslx, 1A5_19d.xslx, H2O_5d.xslx, H2O_12d.xslx, H2O_19d.xslx, H2O_and_1A5.R

**Organisms used:** *Myxococcus xanthus* strain GJV1 (lab wildtype), *Zymoseptoria tritici* strain ST99CH_1A5 (1A5).

**Number of variables:**
Data_Fig_1_and_S1.xslx: 5
1A5_5d.xslx: 3
1A5_12d.xslx: 3
1A5_19d.xslx: 3
H2O_5d.xslx: 3
H2O_12d.xslx: 3
H2O_19d.xslx: 3

**Variable list:**
Data_Fig_1_and_S1.xslx:
Myxo_con: 100µl of 5x this concentration of *M. xanthus* was added to the flasks with straw
Time: Duration of growth of *M. xanthus* on *Z. tritici*/H2O on straw
Cells: Log10 of calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.
Strain: Genotype. *Z. tritici* strain used (1A5, 1E4, 3D7, 3D1) or water control
Pre-moistening duration: Incubation time of straw with H2O or *Z. tritici* only, time before addition of *M. xanthus*.
For all other .xslx files mentioned above:
	Myxo_con: 100µl of 5x this concentration of *M. xanthus* was added to the flasks with straw
	Time: Duration of growth of *M. xanthus* on *Z. tritici*/H2O on straw
Cells: Log10 of calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.

**Explanation of dataset:**
‘Data_Fig_1_and_S1.xslx’ contains all the data for figure 1 and S1 in the way said data was collected. Each tab represents one growth duration of *M. xanthus* and contains all three biological replicates. It also contains calculations of confidence intervals form said data. Relevant for figure 1 are values of the variable Strain “1A5” and “H2O”. The data sheet contains all calculation steps for the estimation of population size, which was calculated by having an internal standard curve for each replicate (done by spotting 5 different GJV1 densities for each replicate and fitting a curve through the points). For easier handling with R, the file was split into smaller Excel files (‘1A5_5d.xslx’, ‘1A5_12d.xslx’, ‘1A5_19d.xslx’, ‘H2O_5d.xslx’, ‘H2O_12d.xslx’, ‘H2O_19d.xslx’) based on *Z. tritici* genotype and pre-moistening duration, where only the average population size was taken for each timepoint (+ confidence interval already calculated before). The different panels of figure 1 show growth of *M. xanthus* on straw imbued with either H2O (a-c) or Z. tritici 1A5 (d-f), where the straw was pre-moistened for different durations of time. a+d show 19 days of pre-moistening, b+e show 12 days of pre-moistening, and c+f show 5 days of pre-moistening. To plot the different panels, the R script in ‘H2O_and_1A5.R’ was used.




### Figure 2
**Files:** Data_Fig_2_and_S2.xlsx, Data_calculations_slopes.xslx, 1A5_100x.xlsx, 1A5_1000x.xlsx, 1A5_10000x.xlsx, 1A5_100000x.xlsx, 1A5_transfers_R_file.R, One_sample_t_test_slopes.xlsx, Slope_averaged.xlsx, slope_all_strains_averaged.R

**Organisms used:** 
Figure 2A: *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5
Figure 2B: *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5, ST99CH_1E4 (1E4), ST99CH_3D7 (3D7), and ST99CH_3D1 (3D1).

**Number of variables:**
Data_Fig_2_and_S2.xlsx: 3
Data_calculations_slopes.xslx: 4
1A5_100x.xlsx: 3
1A5_1000x.xlsx: 3
1A5_10000x.xlsx: 3
1A5_100000x.xlsx: 3
Slope_averaged.xlsx: 2

**Variable list:**
Data_Fig_2_and_S2.xlsx:
Strain: Genotype. *Z. tritici* strain used (1A5, 1E4, 3D7, 3D1) or water control
Dilution: Dilution factor (100x, 1000x, 10’000x, and 100’000x). In the paper, these are referred to as population transfer proportions 1%, 0.1%, 0.01%, and 0.001%.
mm/day: mm/day averaged over the four measurements taken of the swarm size.

Data_calculations_slopes.xslx:
Strain: Z. tritici strain used (1A5, 1E4, 3D7, 3D1)
Replicate: Replicate 1, 2, or 3
Cells: Calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.
Dilution: Dilution factor (100x, 1000x, 10’000x, and 100’000x). In the paper, these are referred to as population transfer proportions 1%, 0.1%, 0.01%, and 0.001%.

Slope_averaged.xlsx:
Dilution: Dilution factor (100x, 1000x, 10’000x, and 100’000x). In the paper, these are referred to as population transfer proportions 1%, 0.1%, 0.01%, and 0.001%.
Slope: Slope of trendline through population size between cycles. Indicates growth (value >0) or decline (value <0) of population over cycles.

All other .xlsx files:
Replicate: Replicate 1, 2, or 3
Cells: Calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.
Step: Original (cycle 1), transfer 1/2/3/4 (cycle 2/3/4/5) of experiment

**Explanation of dataset:**
Figure 2a shows the population size of *M. xanthus* GJV1 over the duration of 5 growth cycles (original + transfer 1/2/3/4) on straw with *Z. tritici* 1A5. The data for the transfers is collected in 'Data_Fig_2_and_S2.xlsx', where each tab signifies one transfer cycle. Cell numbers were calculated in the same was as figure 1. Figure 2a uses *Z. tritici* 1A5 as a representative for all strains used, as there was no significant difference between strains. For easier handling in R, data was split into four files (‘1A5_100x.xlsx’, ‘1A5_1000x.xlsx’, ‘1A5_10000x.xlsx’, ‘1A5_100000x.xlsx’) based on dilution factor and *Z. tritici* strain used. The data was then plotted using ‘1A5_transfers_R_file.R’. For Figure 2a, slopes of population growth were calculated in ‘Data_calculations_slopes.xslx’ based on the data collected in ‘Data_Fig_2_and_S2.xlsx’. The data was re-organized in ‘Slope_averaged.xlsx’ for easier handling in R and was plotted using ‘slope_all_strains_averaged.R‘. A one sample t-test against 0 was performed to test significant difference to 0 in ‘One_sample_t_test_slopes.xlsx’.



### Figure 3
**Files:** Zymo_population_size_experiment.xslx, R_file_TPM_fig_3.xlsx, R_file_Straw_fig_3.xlsx, R_file_fig3.R

**Organisms used:** *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strain 1A5

**Number of variables:**
Zymo_population_size_experiment.xslx: 4
R_file_TPM_fig_3.xlsx: 3
R_file_Straw_fig_3.xlsx: 3

**Variable list:**
Zymo_population_size_experiment.xslx:
Environment: Environment on which *Z. tritici* was growing on. Either TPM hard agar or straw
Treatment: Concentration of added *M. xanthus* (TPM = 0/Buffer only, Mlow = 5 x 106, Mhigh = 5 x 108 cells)
Time: Time of harvest after inoculation (0 days or 7 days)
Cfu: Log10 of colony forming units measured

R_file_TPM_fig_3.xlsx and R_file_Straw_fig_3.xlsx:
Treatment: Concentration of added *M. xanthus* (TPM = 0/Buffer only, Mlow = 5 x 106, Mhigh = 5 x 108 cells)
Time: Time of harvest after inoculation (0 days or 7 days)
Cfu: Log10 of colony forming units measured

**Explanation of dataset:**
In order to measure *Z. tritici* population size, the harvested sample was diluted and 150 µl of the dilutions were spread on a Yeast-Sucrose hard agar plate with kanamycin (to kill *M. xanthus*) using a Drigalski spreader. The cfu was measured after one week of growth at room temperature. The two panels show relative (panel a) and absolute (panel b) numbers of *Z. tritici* population size in presence and absence of different concentrations of *M. xanthus*. Figure 3a was constructed in the Excel file ‘Zymo_population_size_experiment.xslx’, whereas Figure 3b was created using the R script ‘R_file_fig3.R’, using Excel files ‘R_file_TPM_fig_3.xlsx’ and ‘R_file_Straw_fig_3.xlsx’ as basis.

**Explanation of terms used:**
TPM: Buffer containing Tris-HCl, MgSO4, and KH2PO4. Used as neutral buffer for M. xanthus.
Drigalski spreader: Metal triangle used to spread bacterial samples.



### Supplementary Figure 1
**Files:** Data_Fig_1_and_S1.xslx, 1A5_5d.xslx, 1A5_12d.xslx, 1A5_19d.xslx, 1E4_5d.xslx, 1E4_12d.xslx, 1E4_19d.xslx, 3D7_5d.xslx, 3D7_12d.xslx, 3D7_19d.xslx, 3D1_5d.xslx, 3D1_12d.xslx, 3D1_19d.xslx, H2O_5d.xslx, H2O_12d.xslx, H2O_19d.xslx, line_plot_all_strains.R

**Organisms used:** *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5, 1E4, 3D7, and 3D1.

**Number of variables:** 
Data_Fig_1_and_S1.xslx: same as Figure 1.
All other .xslx files: 3

**Variable list:**
 Data_Fig_1_and_S1.xslx: same as Figure 1.

All other .xslx files: 
Myxo_con: 100µl of 5x this concentration of *M. xanthus* was added to the flasks with straw
	Time: Duration of growth of *M. xanthus* on *Z. tritici*/H2O on straw
Cells: Calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.

**Explanation of dataset:**
Supplementary Figure 1 shows the same data as figure 1, but shows the data for all four *Z. tritici* strains tested instead of only the representative strain 1A5. Additionally, it plots two different versions of the water control for easier understanding (one with complete error bars and one zoomed in one with the same y-axis as the other graphs).




### Supplementary Figure 2
**Files:** 1A5_100x.xlsx, 1A5_1000x.xlsx, 1A5_10000x.xlsx, 1A5_100000x.xlsx, 1E4_100x.xlsx, 1E4_1000x.xlsx, 1E4_10000x.xlsx, 1E4_100000x.xlsx, 3D7_100x.xlsx, 3D7_1000x.xlsx, 3D7_10000x.xlsx, 3D7_100000x.xlsx, 3D1_100x.xlsx, 3D1_1000x.xlsx, 3D1_10000x.xlsx, 3D1_100000x.xlsx, all_transfers_lineplot.R, slopes_all_strains.xlsx, slope_all_strains.R

**Organisms used:** *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5, 1E4, 3D7, and 3D1.

**Number of variables:**
	slopes_all_strains.xlsx: 3
	All other .xlsx files: 3

**Variable list:**
	slopes_all_strains.xlsx:
Dilution: Dilution factor (100x, 1000x, 10’000x, and 100’000x). In the paper, these are referred to as population transfer proportions 1%, 0.1%, 0.01%, and 0.001%.
Slope: Slope of trendline through population size between cycles. Indicates growth (value >0) or decline (value <0) of population over cycles.
Strain: Z. tritici strain used (1A5, 1E4, 3D7, or 3D1)

All other .xlsx files:
Replicate: Replicate 1, 2, or 3
Cells: Calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.
Step: Original (cycle 1), transfer 1/2/3/4 (cycle 2/3/4/5) of experiment

**Explanation of dataset:**
Supplementary Figure 2 shows the same data as figure 2, but shows data for all four *Z. tritici** strains tested instead of only the representative strain 1A5. For easier handling in R, the file ‘Data_calculations_slopes.xslx’ was split into smaller Excel files based on *Z. tritici** strain and dilution factor (above named as Strain_Dilution.xlsx). Additionally, Suppl. Fig. 2 shows the slopes for all *Z. tritici* strains individually instead of averaged as in figure 2. For this, the file ‘Data_calculations_slopes.xslx’ was simplified to ‘slopes_all_strains.xlsx’ for easier handling in R using ‘slope_all_strains.R’.




### Supplementary Table 1
**Files:** All_data_ANOVA_compatible.xlsx, No_water_all_data.xlsx, Water_data_ANOVA_compatible.xlsx, ANOVA_R_file_Suppl_Table_1.R

**Organisms used:** *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5, 1E4, 3D7, and 3D1.

**Number of variables:**
	All_data_ANOVA_compatible.xlsx: 5
No_water_all_data.xlsx: 5
Water_data_ANOVA_compatible.xlsx: 5

**Variable list:**
All_data_ANOVA_compatible.xlsx: 
Density: 100µl of 5x this concentration of *M. xanthus* was added to the flasks with straw
PG: ‘Pre-growth’, also pre-moistening duration. Incubation time of straw with H2O or *Z. tritici* only, time before addition of *M. xanthus*.
GT: ‘Growth time’. Duration of growth of *M. xanthus* on *Z. tritici*/H2O on straw
Zymo: Genotype of *Z. tritici* used or H2O.
Cells: Log10 of calculated cell number of *M. xanthus* based on swarming rate per day. Calculation is based on standard curve performed in parallel to every replicate and timepoint.

No_water_all_data.xlsx: same as ‘All_data_ANOVA_compatible.xlsx’, but Zymo only contains only *Z. tritici* strains and no H2O control.

Water_data_ANOVA_compatible.xlsx: same as ‘All_data_ANOVA_compatible.xlsx’, but Zymo only contains H2O control and no *Z. tritici* strains.

**Explanation of dataset:**
Statistical analysis of the dataset of Figure 1/Suppl. Figure 1 using a multiple factor ANOVA. Three different ANOVAs were performed on three different parts of the dataset. First, the whole data set was analyzed for all contributing factors (Density, PG, GT, Zymo, Cells). After that, the data set was split into two: *Z. tritici* treatments and H2O control treatments. These two data sets were analyzed for the same factors, except the H2O control was not analyzed for ‘Zymo’ (technically ‘genotype’). A Tuckey post hoc test was used subsequently. The results of these ANOVAs are depicted in Suppl. Table 1.



### Supplementary Table 2
**Files:** Data_slopes.xlsx, ANOVA_R_file_Suppl_Table_2.R

**Organisms used:** *Myxococcus xanthus* strain GJV1, *Zymoseptoria tritici* strains 1A5, 1E4, 3D7, and 3D1.

**Number of variables:**
	Data_slopes.xlsx: 3
    
**Variable list:**
	Strain: Z. tritici strain used (1A5, 1E4, 3D7, or 3D1)
Dilution: Dilution factor (100x, 1000x, 10’000x, and 100’000x). In the paper, these are referred to as population transfer proportions 1%, 0.1%, 0.01%, and 0.001%.
Slope: Slope of trendline through population size between cycles. Indicates growth (value >0) or decline (value <0) of population over cycles.

**Explanation of dataset:**
Statistical analysis of Figure 2/Suppl. Figure 2 using a Two-Way ANOVA with the factors Slope and Dilution of the data set ‘Data_slopes.xlsx’. A Tuckey post hoc test was used subsequently. The results of this ANOVA are depicted in Suppl. Table 2.