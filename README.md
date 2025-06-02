# Pinto-2025-LMon-Milk-Model

## Overview
  The share table model in the present study is an adapted version of the share table model originally published by our group (Reyes et al., 2022). The original work presented a quantitative microbial risk assessment of norovirus transmission in school cafeteria systems with a share table. 

  We later revised the model to study milk spoilage, specifically for a common, fast-growing psychrotrophic bacteria, Pseudomonas poae (Pinto et al., 2024). We utilized the same sharing dynamics as the original model, and additionally tracked the initial level of spoilage bacteria in milks and microbial growth over simulated cafeteria service(s), using the Buchanan 3-phase linear model (Buchanan et al., 1997) and parameters from Lau et al. (2022). Microbial growth was measured for each milk until it was consumed, discarded, or donated. We utilized the empirical temperature data collected during our experimental study of P. poae growth as an input to the milk spoilage growth model, and evaluated at what point (if any) contaminated milks in the system exceed our defined spoilage threshold of 6.0 Log10 CFU/ml. We modeled a single scenario, representing our experimental share table: two 50-minute lunch services with a 25-minute break between the services each day (5 days/week, repeated over 1,000 weeks) with no temperature management implemented from the start to the end of the lunch services and overnight refrigeration between days of service. A further adaption of the milk spoilage model was made to evaluate 25 realistic school cafeteria scenarios  (Corea et al., 2024). Most scenarios included manipulation of single variables at a time, including length of meal services and breaks, initial spoilage contamination, ambient temperature of the cafeteria, overnight refrigeration temperature, share table storage conditions, and toggling the share table off. We also evaluated scenarios manipulating share table conditions (adding a tray with ice or ice packs) for long and very long meal service lengths. A full description of the scenarios and values input to the model can be found in Table 1 and the supplemental materials of Corea et al. (2024). 

  This study presents an adaptation of the model from Corea et al. (2024) to assess the safety of milk on share tables by studying: (i) time to 1-Log10 Listeria monocytogenes growth, (ii)  L. monocytogenes concentration at consumption, and (iii) listeriosis risk from milk consumption under 22 scenarios. The initial spoilage contamination scenarios were omitted from this model as the initial contamination of L. monocytogenes in pasteurized milk is extremely low. Here, we simulate milk in a cafeteria system with a share table over a 5-day school week (37 weeks/school year, repeated over 50 school years). 

## Usage
### User Guide 
You can find the full user guide document in the [Share Table Model User Guide](/Share_Table_Model_User_Guide.docx) file. The document contains information on input and output datasets, brief descriptions of files needed for a user to run this model, and detailed information and how-to-use for main analysis. 

### Setup
#### Input datasets 
- **Time and temperature profiles** - In the “Predicted Time and Temp Profiles” folder, there are 21 Df_RT_MT_xxx.csv files created for 22 different time and temperature abuse scenarios (Note: the “no share table” scenario uses the same file as baseline share table scenario).  

- **Datasets generated for this manuscript** - In the “Input Data” folder, there are 22 RDS files that contains the saved data files generated for this manuscript from running this model. These files contain the information used to calculate the (i) time to 1-Log10 L. monocytogenes growth, (ii) L. monocytogenes growth, and (iii) listeriosis risk from milk consumption under school share table scenarios. You can reproduce the same results if you input these RDS files. If you rerun the model and generate new main datasets for analysis, you would obtain similar results, but these would vary slightly from what is presented in the manuscript. Thus, these RDS files are saved to this GitHub.

### Running
The following are the files needed to run this model. Most of the files do not need to be modified to run the model. For those that need to be changed, the how-to-use and detailed information are described in the [Share Table Model User Guide](/Share_Table_Model_User_Guide.docx) file.

- **Analysis Pinto et al 2025.Rmd** - The main analysis file. This file runs the model and generates the results: (i) time to 1-Log10 *L. monocytogenes* growth, (ii) *L. monocytogenes* growth, and (iii) listeriosis risk from milk consumption under school share table scenarios.
- **Calc_FeedingItems.R** - Restock the service line if items ran out for a given day.
- **Calc_StudentContamination.R** - Calculate initial contamination of pathogen or allergen in students. 
- **Functions_Full_Analysis.R** - Create the main data frame for running the share table model.
- **Input_Functions.R** - Create functions for adding time to main data frame. 
- **Input_Random.R** - Create functions for generating probabilities of touching food items and other student behaviors (sharing food, picking an additional item from share table, and eating share table items).
- **Input_RandomWeeks.R** - Track the weekly random input of wash hand or hand sanitizer method. 
- **Input_Static.R (Input_Static_xxxx.R)** - Static inputs in the model, including student data, number and length of services, days and weeks, service line information (number of items and size of selection table), inputs for calculation if student is contaminated, inputs for allergen contamination, inputs behavioral probabilities. Multiple files created for different number and length of services. 
- **Main_Loop.R** - Create the Main_Loop function that runs the model simulation for one food item (whether be touched, whether be contaminated, is there enough in selection table, whether get consumed). 
- **Main_Loops2.R** - Create the loops to iterate for students, services, days per week, and weeks per school year. 
- **Output_Days.R** - For items left over from one day of service, add the overnight time, growth during overnight time, and return to reservice in next day of service. 
- **Output_Services.R** - For items left over from selection table or share table during one day of service, add the growth of L. monocytogenes between every service and the turnaround growth.  
- **Util_CCFunctions2.R** - Create functions for touching items, picking items (from selection table and share table), eating items, sharing items, and cross contamination. 
- **Util_Counter&Lists.R** - Create the empty lists and counters.
- **Util_DataFrames.R** - Add contamination and time to the main data frame.
- **Util_DFFunctions.R** - Create functions for creating data frames for items in one service in the first day, data frames for items in the reservice, and data frame for items that are restocked to service line when run out. 
- **Util_DFWeekCreation.R** - Create data frames for sensitivity analysis. 
- **Util_Functions.R** - Create functions for searching data frames, log reduction, adding time, unit conversion, etc.  
- **Util_Library.R** - Load/library the packages for running the model. 
- **Util_Output_Functions.R** - Create functions for assigning not consumed items (discarded/donated), adding number of services to total, and getting leftover items. 

## Authors
You can view the list of authors in the [AUTHORS](/AUTHORS) file.

## Contact
Corresponding author: Matthew J. Stasiewicz<br>
103 Agricultural Bioprocess Lab<br>
1302 W. Pennsylvania<br>
Urbana, IL, 1361801<br>
USA<br>
+1-217-265-0963<br>
[mstasie@illinois.edu](mailto:mstasie@illinois.edu)

## Citation


## License
This project's code is licensed under the GNU General Public License v3.0 and dataset is licensed the Creative Commons Attribution Share Alike 4.0 International license. Please see the [LICENSE.code](/LICENSE.code) and [LICENSE.dataset](/LICENSE.dataset) files for details.

## Acknowledgements
Any opinions, findings, or recommendations in this paper are those of the authors and do not necessarily reflect the view of the USDA. The authors declare that they have no known conflicts of interest that could influence the work reported in this paper.

## Funding
This project was supported by the US Department of Agriculture (USDA) National Institute of Food and Agriculture award number: (2021-68008-34106).
