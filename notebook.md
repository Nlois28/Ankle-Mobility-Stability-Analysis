Predictive Analytics for Athletic Performance: Ankle Mobility & Balance Deficits

The Project: I analyzed biomechanical data from 26 handball players to investigate how ankle joint mobility affects static and dynamic balance.
Key Insight: The study revealed significant differences in proprioception between flexible and inflexible players, providing a data-driven framework for injury prevention.
Ask
Questions to solve: 
1.	How is ankle flexibility distributed across the team, and what percentage of athletes fall into the 'High-Risk' (Inflexible) category?
2.	Does ankle stiffness impact static balance (Stable Surface) as severely as it impacts dynamic movement (Unstable Surface/Y-Balance)?
3.	In which specific direction (Anterior, Medial, or Lateral) do Inflexible athletes show the most significant performance drop?
4.	Is there a correlation between poor ankle mobility and Bilateral Asymmetry? 
5.	How much does leg length bias the raw reach scores, and how does 'Normalization' provide a more accurate athlete ranking?

clean
Tools Used: excel and tableau. 

I extracted from spss files the data and downloaded to .csv files. Then I saved them to .xlsx file.


Data Cleaning Steps:

•	Correction of Decimals (Dots vs Commas):
 Ctrl + H -> Find: . (dot) -> Replace with: , (comma) to ensure excel recognizes values as numbers for calculations.




•	Handling Missing Values:

Ctrl + H -> Find: 0  -> Replace with: null
I left them blank to use the average of the other two trials for that specific athlete to maintain data integrity.





•	Standardization of Trials (Calculated Fields):

I created  a new column for the Mean Score of each direction.
Formula: =(Trial1 + Trial2 + Trial3) / 3





•	Normalization (The Scientific Key):

I created  a column Normalized_Score for each direction.
 Formula: =(Mean_Score / leglength) * 100




•	Categorical Grouping (FL vs IN):

I created the Mobility_Group column based on Ankle Dorsiflexion.
•  Logic: =IF(Cell < 34,5; "Inflexible"; IF(Cell > 45; "Flexible"; "Intermediate"))





•	Integrity & Data Types:


 I ensured Age, Weight, Height are set as Number, Name, Group are set as Text, Converted Injury (0/1) to Yes/No for better visualization.

During the initial data entry phase, a formatting conflict was identified where numerical values were being recognized as text strings (leading to #DIV/0! and #VALUE! errors). This was due to inconsistent decimal separators and hidden non-breaking spaces within the dataset.
To resolve this and ensure data integrity for Tableau analysis, the following steps were taken:
1.	Data Scrubbing: Used the 'Find and Replace' function to eliminate all hidden whitespaces and non-numerical characters.
2.	Locale Optimization: Adjusted the spreadsheet settings to 'United States' to align the decimal point system with the raw data format (e.g., 76.8).
3.	Type Conversion: Applied a 'Paste Special > Multiply by 1' operation to force-convert all text-based entries into numerical formats, ensuring correct alignment and computational readiness.
4.	Verification: Validated that all metrics (Dorsiflexion means and Y-Balance reach) were correctly calculated before proceeding to the Median Split for group categorization (Inflexible vs. Flexible).



Data cleaning involved converting text-based numbers to numeric format by replacing dots with commas. To handle outliers and ensure a balanced 13-vs-13 group distribution, a median-split was performed after sorting the corrected mean dorsiflexion values."


1. Data Integrity & Outlier Management
•	Identification: Conducted a thorough audit of the dataset to identify extreme outliers and potential data entry errors. A specific case was noted where a score of 128.0% was recorded under unstable conditions—a physiological impossibility for this test.
•	Correction: Cross-referenced raw trial data to correct these anomalies. This ensured that the Composite Scores remained within a valid biological range (70%–95%), preventing skewed averages during the visualization phase.
2. Standardized Nomenclature
•	Transformation: Renamed all headers to follow a "snake_case" naming convention (e.g., Anterior_Asymmetry_Foam instead of Anterior Asymmetry f).
•	Objective: This step ensures seamless integration with BI tools like Tableau or Power BI and programming languages like Python/SQL, where spaces in headers can cause syntax errors.
3. Feature Engineering: The "Stability Index"
•	Innovation: Developed a custom KPI named the Stability Index to quantify the performance gap between stable and unstable surfaces.
•	Formula: Stability_Index = Norm_Anterior_Stable - Norm_Anterior_Foam
•	Insight: This allows for a direct comparison of "stability cost" across different mobility groups (Flexible vs. Inflexible).
4. Normalization (Data Scaling)
•	Process: Performed data normalization by scaling raw reach distances (cm) against each subject's Leg Length.
•	Formula: 
$$(Reach \text{ (cm)} / Leg Length \text{ (cm)}) \times 100$$
•	Rational: This eliminates anthropometric bias, allowing for a fair comparison between athletes of different height 
 
PHASE 3: ANALYZE
Objective: Transform processed data into meaningful biomechanical insights.
•	Data Aggregation: Utilized Tableau’s analytical engine to calculate the Mean (Average) performance of participants, rather than simple sums, to ensure a fair comparison between the "Flexible" and "Inflexible" cohorts.
•	Segmented Analysis: * Filtered data by Mobility_Group to isolate the impact of ankle dorsiflexion on balance.
o	Applied Comparative Visualization (Side-by-Side Bar Charts) to observe how each group reacted when transitioning from stable to unstable (foam) surfaces.
•	Correlation Exploration: Evaluated the relationship between Ankle_Dorsiflexion degrees and the Stability_Index.
o	Finding: A direct positive correlation exists between increased joint mobility and improved reach distance (Excursion) during foam trials.
•	Statistical Observations: Noted that while flexible subjects achieve greater reach, they also exhibit unique sway patterns, suggesting that mobility must be paired with neuromuscular control.
________________________________________
PHASE 4: SHARE (Data Visualization)
Objective: Create a high-impact Dashboard for stakeholder communication.
•	Dashboard Architecture: Designed a multi-pane interactive dashboard in Tableau featuring:
o	Demographic Overview: A summary of age, weight, and leg length to provide context.
o	Performance Deep-Dive: Bar charts illustrating "Directions with Foam," highlighting the performance gap between groups.
o	Asymmetry Analysis: Visualizing the reach difference between left and right limbs to identify potential injury risks.
•	Visual Best Practices:
o	Color Consistency: Implemented a unified color palette (Blue for Flexible, Orange for Inflexible) to reduce cognitive load for the viewer.
o	Clarity & Precision: Formatted all metrics to two decimal places and renamed technical headers (Aliases) into user-friendly terminology (e.g., "Anterior Stability").
o	Interactivity: Integrated "Use as Filter" actions, allowing users to select a specific group and see the entire dashboard update in real-time.
________________________________________
PHASE 5: ACT (Conclusion & Recommendations)
Objective: Provide actionable value based on the data.
•	Injury Prevention: Athletes falling into the "Inflexible" category should prioritize ankle mobility protocols, as the data shows a significant "Stability Cost" on unstable surfaces.
•	Training Insights: Coaches should use the Stability Index as a KPI for assessing an athlete's readiness to return to play after lower-limb injuries.
•	Future Research: Recommend expanding the sample size to include various sports disciplines to validate if these trends remain consistent across different types of athletic training.
