# Pymaceuticals Inc. (Matplot-Challenge)

# DESCRIPTION: 
# The corresponding analysis summarizes the results of multiple anti-cancer medications and their effectiveness
# in treating Squamous Cell Carcinoma in mice over the course of 45 days. The pharmaceutical company that this analysis
# is being conducted for, wants to compare the performance of the drug Capomulin against other anti-cancer drug regimens.

# DATA USED:
# Data used during the process of the analysis were results from studies taken during the 45 day timepoint on mice receiving 
# various anti-cancer treatments, which included measurements of tumor volume. In addition, data involving general characteristics of
# the mice and the drug they received over the span of time were used to add more information of use to the analysis.


# Snippet of the Complete dataframe which was created through merging 'Mouse_metadata.csv' and 'Study_results.csv' located in the 'Resources'  file: 
#  used throughout the analysis, when referring to the entire dataset.
#  specifially used to calculate the number of unique mice, as well as unique drug regimens and their associated values.
    Mouse ID	Timepoint	Tumor Volume (mm3)	Metastatic Sites	Drug Regimen	Sex	Age_months	Weight (g)
0	b128	   0	            45.0	        0	                Capomulin	    Female	9	    22
1	f932	   0	            45.0	        0	                Ketapril	    Male	15	    29
2	g107	   0	            45.0	        0	                Ketapril	    Female	2	    29
3	a457	   0	            45.0	        0	                Ketapril	    Female	11	    30
4	c819	   0	            45.0	        0	                Ketapril	    Male	21	    25


# DataFrame used to visualize duplicate 'Mouse ID' and Timepoint:
# when dropping these duplicates from the dataset, it changes the total number of mice in the study from 249 to 248. 
    Mouse ID	Timepoint	Tumor Volume (mm3)	Metastatic Sites	Drug Regimen	Sex	Age_months	Weight (g)
107	    g989	        0	    45.000000	        0	            Propriva	    Female	21	    26
137	    g989	        0	    45.000000	        0	            Propriva	    Female	21	    26
329	    g989	        5	    48.786801	        0	            Propriva	    Female	21	    26
360	    g989	        5	    47.570392	        0	            Propriva	    Female	21	    26
620	    g989	        10	    51.745156	        0	            Propriva	    Female	21	    26
681	    g989	        10	    49.880528	        0	            Propriva	    Female	21	    26
815	    g989	        15	    51.325852	        1	            Propriva	    Female	21	    26
869	    g989	        15	    53.442020	        0	            Propriva	    Female	21	    26
950	    g989	        20	    55.326122	        1	            Propriva	    Female	21	    26
1111	g989	        20	    54.657650	        1	            Propriva	    Female	21	    26


# Dataframe used to  visualize various statistics involving the Tumor Volume, all of which were calculated through using summary statistic attributes such as .mean() and .std().

            Mean Tumor Volume	    Median Tumor Volume	       Tumor Volume Variance	Tumor Volume Std. Dev.	Tumor Volume Std. Err.
Drug Regimen					
Capomulin	        40.675741	        41.557809	                24.947764	            4.994774	            0.329346
Ceftamin	        52.591172	        51.776157	                39.290177	            6.268188	            0.469821
Infubinol	        52.884795	        51.820584	                43.128684	            6.567243	            0.492236
Ketapril	        55.235638	        53.698743	                68.553577	            8.279709	            0.603860
Naftisol	        54.331565	        52.509285	                66.173479	            8.134708	            0.596466
Placebo	            54.033581	        52.288934	                61.168083	            7.821003	            0.581331
Propriva	        52.322552	        50.854632	                42.351070	            6.507770	            0.512884
Ramicane	        40.216745	        40.673236	                23.486704	            4.846308	            0.320955
Stelasyn	        54.233149	        52.431737	                59.450562	            7.710419	            0.573111
Zoniferol	        53.236507	        51.818479	                48.533355	            6.966589	            0.516398


# Bar Plot generated using Pandas DataFrame.plot() method, which visualizes the number of times a Mouse Timepoint has been observed for each drug regimen given to the mice.
# Using the to_frame() method, I was able to turn a value_counts() dataseries into a dataframe (which in turn, became a bar plot). 
![Alt text](image-3.png) (use image.png link to view)


# Same Bar Plot as previous, except generated through pyplot. 
# Two lists of values were applied as the y-axis and x-axis, followed by formatting of the labels.
![Alt text](image-4.png) (use image.png link to view)

# Pie Chart created through using Pandas.
# Values for the sex of the mice were calculated using a values_count(), then were inserted into a dataframe to be used in the pie plot.  
![Alt text](image-5.png) (use image.png link to view) 

# Same Pie Chart as previous, except generated using pyplot.
# Calculated using two lists which were applied to the plt.pie() formula (amongst various formatting characterisitcs). 
![Alt text](image-6.png)


# Merged dataframe which visualizes drug regimens at the beginning of their timepoint to the end of their timepoint.
# To be used for quartiles, outliers, and boxplots.

    Mouse ID	Timepoint	Tumor Volume (mm3)	Metastatic Sites	Drug Regimen	Sex	    Age_months	Weight (g)
0	    a203	    45	        67.973419	                  2	        Infubinol	Female	    20	    23
1	    a251	    45	        65.525743	                  1	        Infubinol	Female	    21	    25
2	    a262	    45	        70.717621	                  4	        Placebo	    Female	    17	    29
3	    a275	    45	        62.999356	                  3	        Ceftamin	Female	    20	    28
4	    a366	    30	        63.440686	                  1	        Stelasyn	Female	    16	    29
                ...	...	...	...	...	...	...	...	...
244	    z435	    10	        48.710661	                  0	        Propriva	Female	    12	    26
245	    z578	    45	        30.638696	                  0	        Ramicane	Male	    11	    16
246	    z581	    45	        62.754451	                  3	        Infubinol	Female	    24	    25
247	    z795	    45	        65.741070	                  3	        Naftisol	Female	    13	    29
248	    z969	    45	        73.867845	                  4	        Naftisol	Male	    9	    30

# Using the merged dataframe and appending the final tumor volumes to an empty list, then the quartiles and outliers were visualized using a box plot. This was done using the lower and upper bounds of the values recorded.
![Alt text](image-2.png) 

# To visualize the tumor volume vs. time point (in a single mouse treated with capomulin), after selecting a specific mouse id and gathering data on its tumor volume throughout the course of its treatment process, a line plot can then be generated.
![Alt text](image-4.png) 

# Finally, for the last visualizations, we generated a scatter plot of mouse weight vs. the average observed tumor volume for all mice treated with capomulin. One without a visual of the linear regression and one with.

# No LR:
![Alt text](image-5.png) 

# LR: 
![Alt text](image-6.png) 

# Analysis: 

After analyzing the data, it appears that the drug regimen of Capomulin shows promise of being an effective drug to treat Squamous Cell Carcinoma in mice. Notably in the observation of a single mouse,
after the 20th day of treatment, a drastic change in tumor volume was observed. This could potentially mean
that Capomulin is effective in treating cancer, although more data would need to be analyzed to make any 
clear indication that this is true. 
In addition, the data suggests that weight plays a factor in tumor volume for mice. For example, of the mice in 
the Capomulin regimen, those with a larger weight appeared to have a larger tumor volume, as for those with a lower weight
had a smaller tumor. This data has importance because if the ultimate goal is to apply our findings to humans and the 
treatment of Squamous Cell Carcinoma, data could possibly indicate similar results which could help in the prevention
or limit the degree that this cancer can appear.

# Resources

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.duplicated.html 

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.plot.pie.html 

https://www.tutorialspoint.com/barchart-with-vertical-labels-in-python-matplotlib 

https://www.geeksforgeeks.org/how-to-create-pie-chart-from-pandas-dataframe/ 

https://www.geeksforgeeks.org/how-to-combine-two-dataframe-in-python-pandas/

https://sparkbyexamples.com/pandas/pandas-get-list-of-all-duplicate-rows/#:~:text=You%20can%20use%20df%5Bdf,duplicate%20rows%20in%20our%20DataFrame. 

https://www.educative.io/answers/how-to-convert-series-to-dataframe-in-pandas 

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.agg.html 

https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.linregress.html 
