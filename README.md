# The Paper
This repository includes scripts and data for the following paper:

Audrain & McAndrews, Schemas provide a scaffold for neocortical integration of new memories over time.

# Abstract
Memory transformation is increasingly acknowledged in theoretical accounts of systems consolidation, yet how memory quality and neural representation change over time and how schemas influence this process remains unclear.  In this multi-day fMRI study, participants encoded and retrieved schema-congruent and incongruent object-scene pairs using a paradigm that probed memory representations over 10-minutes and 72-hours. When a congruent schema was available, memory became coarser over time as representations were integrated in the medial prefrontal cortex (mPFC), aided by post-encoding coupling between the anterior hippocampus and mPFC. In the hippocampus, pattern similarity changed across 72-hours such that the posterior hippocampus represented specific details and the anterior hippocampus represented the general context of specific memories, irrespective of congruency. Our findings suggest schemas are used as a scaffold for accelerated consolidation of congruent information, and illustrate evolution in hippocampal organization of detailed contextual memory over time. 

# The Software
All scripts were coded and run in RStudio version 1.2.5033, using RNotebook. 

Rstudio can be downloaded here: https://www.rstudio.com/products/rstudio/download/ , and must be installed on your local machine in order to run these scripts. Installation of RStudio can take several minutes. 

# The scripts
R scripts:
- R_SCP_behaviour_analysis.Rmd
  - contains code for the behavioural modelling and plots of the main manuscript, as well as control proportion forgotten analysis, and plots of forgotten/incorrect trials according to each condition as outlined in the supplementary material. 
- R_SCP_connectivity_analysis.Rmd
  - contains code for the resting state connectivity correlations with behaviour and plot, in main manuscript. 
- SCP_RSA_context_mem_analyses.Rmd
  - contains code for modelling and plotting of the medial prefrontal cortex RSA analyses on context memory trials (main manuscript), and corresponding plots for hippocampal ROIs (supplementary material). 
- SCP_RSA_scene_mem_analyses.Rmd
  - contains code for modelling and plotting of the hippocampal RSA analyses on trials remembered with specificity (main manuscript), and corresponding plots for the mPFC ROI (supplementary material). 
- R_SCP_CongruencyBias.Rmd
  - contains code for modelling and plotting the behavioural control congruency bias analysis, as outlined in the supplementary material. 
- R_SCP_objectsim.Rmd
  - contains code for modelling and plotting the control RSA object pattern similarity analysis between context-related objects versus arbitrary objects, as outlined in the supplementary material.

# The data
## The behavioural data
SCP_behavioural_data.csv
- subj: subject number
- delay: short = short delay, long = long delay
- congruency: R = congruent, UR = incongruent
- granularity: coarse = coarse memories, fine = detailed memories
- cond: congruency x granularity interaction terms 
- accuracy_gran: accuracy broken down by both congruency and granularity
- accuracy_rel: accuracy based on congruency, collapsed across granularity
- prop_forgetting: refers to proportion forgotten across long delay relative to short, short-long/short for accuracy_gran scores
- include: subjects with 0 are outliers with very high coarse congruent memory across long delay 
- CB_order: counterbalancing order, subjects with 1 did short delay followed by long delay, subjects with 2 had long delay followed by short delay
- DK: for coarse memories, these numbers refer to number of trials where subjects said 'don't know' to context question. For detailed memories, it's the number of trials where they got the coarse context correct but answered 'don't know' for the scene question. 
- incorrect: for coarse memories, this refers to number of trials where the subject chose the wrong context. For detailed memories, it refers to number of trials where subject answered the coarse context qusetion correctly but got the scene question incorrect. 
- total_forgot: total number of trials forgotten, including incorrect and 'don't know' trials
- R_enc: number of trials judged as related/congruent at encoding 
- UR_enc: number of trials judged as unrelated/incongruent at encoding 
- DK_perc: % of total congruent/incongruent trails (as judged at encoding) where subject answered 'don't know'
- incorrect_perc: % of total congruent/incongruent trials (as judged at encoding) where subject made incorrect response 
- total_forgot_perc: total % forgotten (including incorrect and 'don't know' responses) 

This file accompanies R_SCP_behaviour_analysis.Rmd

## Data for the connectivity correlations with behaviour
SCP_connectivity_data.csv
- subj: subject number
- CB: counterbalancing condition, noncb= short delay followed by long delay, cb= long delay followed by short delay
- YOE: years of education
- hand: handedness
- ESL?: English as second language
- include_rest: 0= does not have a rest scan or bad rest scan, 1 = good rest scan to include_rest
- post_pre_AH_mPFC: post encoding resting state connectivity minus pre encoding resting state connectivity between the anterior hippocampus and mPFC
- related_enc_short: % of stimuli judged as congruent during encoding for the short delay
- unrelated_enc_short: % of stimuli judged as incongruent during encoding for the short delay
- total_accuracy_short: total % accuracy across the short delay (congruent coarse + congruent fine + incongruent coarse + incongruent fine/out of 80 trials)
- related_accuracy_short: % of congruent trials retained across short delay ((coarse congruent + fine congruent) / # of trials judged as congruent during encoding)
- unrelated_accuracy_short: % of incongruent trials retained across short delay ((coarse incongruent + fine incongruent) / # of trials judged as incongruent during encoding)
- fine_accuracy_short: % of trails remembered with detail across the short delay (congruent detailed + incongruent detailed / out of 80 trials)
- coarse_accuracy_short: % of trails remembered coarsely across the short delay (congruent coarse + incongruent coarse / out of 80 trials)
- fine_related_short: % of congruent trials remembered with detail across short delay (# of detailed congruent trials across short delay / # of trials judged as congruent at encoding)
- fine_unrelated_short: % of incongruent trials remembered with detail across short delay (# of detailed incongruent trials across short delay / # of trials judged as incongruent at encoding)
- coarse_related_short: % of congruent trials remembered coarsely across short delay (# of coarse congruent trials across short delay / # of trials judged as congruent at encoding)
- coarse_unrelated_short: % of incongruent trials remembered coarsely across short delay (# of coarse incongruent trials across short delay / # of trials judged as incongruent at encoding)
- related_enc_long: % of stimuli judged as congruent during encoding for the long delay
- unrelated_enc_long: % of stimuli judged as incongruent during encoding for the long delay
- total_accuracy_long: total % accuracy across the long delay (congruent coarse + congruent fine + incongruent coarse + incongruent fine/out of 80 trials)
- related_accuracy_long: % of congruent trials retained across long delay ((coarse congruent + fine congruent) / # of trials judged as congruent during encoding)
- unrelated_accuracy_long: % of incongruent trials retained across long delay ((coarse incongruent + fine incongruent) / # of trials judged as incongruent during encoding)
- fine_accuracy_long: % of trails remembered with detail across the long delay (congruent detailed + incongruent detailed / out of 80 trials)
- coarse_accuracy_long: % of trails remembered coarsely across the long delay (congruent coarse + incongruent coarse / out of 80 trials)
- fine_related_long: % of congruent trials remembered with detail across long delay (# of detailed congruent trials across long delay / # of trials judged as congruent at encoding)
- fine_unrelated_long: % of incongruent trials remembered with detail across long delay (# of detailed incongruent trials across long delay / # of trials judged as incongruent at encoding)
- coarse_related_long: % of congruent trials remembered coarsely across long delay (# of coarse congruent trials across long delay / # of trials judged as congruent at encoding)
- coarse_unrelated_long: % of incongruent trials remembered coarsely across long delay (# of coarse incongruent trials across long delay / # of trials judged as incongruent at encoding)

SCP_connectivity_data_long.csv
- subj: subject number
- CONN order: subject number within the CONN toolbox used for the connectivity analysis 
- age: age of each subject 
- gender: gender of each subject 
- hand: handedness
- ESL?: English as second language
- include_rest: 0= does not have a rest scan or bad rest scan, 1 = good rest scan to include_rest
- congruency: R = congruent, UR = incongruent
- granularity: coarse = coarse memories, fine = detailed memories
- post_pre_AH_mPFC: post encoding resting state connectivity minus pre encoding resting state connectivity between the anterior hippocampus and mPFC
- accuracy_gran: accuracy broken down by both congruency and granularity across the long delay

These files accompany R_SCP_connectivity_analysis.Rmd.

## RSA data for statistical models
RSA_output
- each csv file in this folder contains output from the RSA analysis
- Description of file names: [congruency_condition_delay_mask]
  - congruency:
    - R = congruent trials, UR = incongruent trials
  - condition:
    - samescene_fine = correlations were between detailed trials that shared the same background scene (e.g. big beach with other big beach trials)
    - simscene_fine = correlations were between detailed trials that had similar scenes within the same context (e.g. between big beach and small beach trials)
    - xcon_fine = correlations were between detailed trials of opposing contexts (e.g. big beach correlated with brown kitchen and white kitchen trials)
    - wincon = within context correlations (e.g. correlations between trials paired with beaches, regardless of scene granularity)
    - xcon = across context correlations (e.g. correlations between beach and kitchen trials, regardless of scene granularity)
    - contextO = correlations between arbitrary objects with incongruent backgrounds
    - arbO = correlations between context-related (kitchen or beach objects) objects with incongruent backgrounds 
    - arbcontextO = correlations between context-related objects and arbitrary objects with incongruent backgrounds 
  - delay:
    - short = short delay trials
    - long = long delay trials
  - mask:
    - BNA_mPFC2: mPFC
    - right_hippo_ant: right anterior hippocampus
    - right_hippo_post: right posterior hippocampus
- Description of file contents:
  - Columns from left to right: subject identifier, correlation number, mask, Pearson's correlation
  - These are all across-run correlations, and have not been averaged in any way, or Fisher transformed


This data accompanies the SCP_RSA_context_mem_analyses.Rmd and SCP_RSA_scene_mem_analyses.Rmd and R_SCP_objectsim.Rmd scripts.

# Running the scripts 
To run these scripts, you will need to download and save the associated .csv files (described under "The Data" section) and the RSA_output folder on your local machine. 

You will need to change the path in each script to point to wherever you saved the data on your local machine (denoted by ###### CHANGE PATH FOR YOUR DATA ####### within each script). 

You will also need to download the function summarySEwithin2.R and save it in the same folder as the downloaded scripts, in order to be able to calculate wtihin-subject standard error bars for the plots. 

Running these scripts will reproduce the stasticial analyses (ANOVA tables, pairwise comparison tables, correlation tests etc.), as well as plots of the data used in the main manuscript and supplementary material. Each script should take no more than a few minutes to run. 

# License
All code in this repository is licensed under the MIT license.

The data included in this repository is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

# Inquiries
Please contact samanthaaudrain at gmail dot com for questions, comments, or bugs.
