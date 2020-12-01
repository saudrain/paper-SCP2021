# The Paper
This repository includes scripts and data for the following paper:

Audrain & McAndrews, Schemas provide a scaffold for neocortical integration at the cost of memory specificity over time

# Abstract
Memory transformation is increasingly acknowledged in theoretical accounts of systems consolidation, yet how memory quality and neural representation change over time and how schemas influence this process remains unclear.  In this fMRI study, participants encoded and retrieved schema-congruent and incongruent object-scene pairs using a paradigm that probed coarse and detailed memories over 10-minutes and 72-hours. When a congruent schema was available, details were lost over time as representations were integrated in the medial prefrontal cortex (mPFC), and enhanced post-encoding coupling between the anterior hippocampus and mPFC was associated with coarser memories.  Over time, pattern similarity in the hippocampus changed such that the posterior hippocampus represented specific details and the anterior hippocampus represented the general context of specific memories, irrespective of congruency. Our findings suggest schemas are used as a scaffold for accelerated consolidation of congruent information, and illustrate change in hippocampal organization of detailed contextual memory over time.

# The scripts
All scripts were coded and run in RStudio version 1.2.5033.

R scripts:
- R_SCP_behaviour_analysis.Rmd
  - contains code for the behavioural modelling and plots
- R_SCP_connectivity_analysis.Rmd
  - contains code for the resting state connectivity correlations with behaviour and plot
- SCP_mPFC_analyses.Rmd
  - contains code for modelling and plotting of the medial prefrontal cortex RSA analyses
- SCP_hippo_analyses.Rmd
  - contains code for modelling and plotting of the hippocampal RSA analyses

# The data
## The behavioural data
SCP_behavioural_data.csv
- subj: subject number
- delay: short = short delay, long = long delay
- congruency: R = congruent, UR = incongruent
- granularity: coarse = coarse memories, fine = detailed memories
- accuracy_gran: accuracy broken down by both congruency and granularity
- accuracy_rel: accuracy based on congruency, collapsed across granularity
- forgetting: proportion of trials forgotten across the short delay relative to the long delay (long delay% - short delay%, negative values mean worse memory over time), broken down by both congruency and granularity

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

This file accompanies R_SCP_connectivity_analysis.Rmd.

## RSA data for statistical models
RSA_output
- each csv file in this folder contains output from the RSA analysis
- Description of file names: [congruency_condition_delay_mask]
  -- congruency:
    --- R = congruent trials, UR = incongruent trials
  -- condition:
    --- samescene_fine = correlations were between detailed trials that shared the same background scene (e.g. big beach with other big beach trials)
    --- simscene_fine = correlations were between detailed trials that had similar scenes within the same context (e.g. between big beach and small beach trials)
    --- xcon_fine = correlations were between detailed trials of opposing contexts (e.g. big beach correlated with brown kitchen and white kitchen trials)
    --- wincon = within context correlations (e.g. correlations between trials paired with beaches, regardless of scene granularity)
    --- xcon = across context correlations (e.g. correlations between beach and kitchen trials, regardless of scene granularity)
  -- delay:
    --- short = short delay trials
    --- long = long delay trials
  -- mask:
    --- BNA_mPFC2: mPFC
    --- right_hippo_ant: right anterior hippocampus
    --- right_hippo_post: right posterior hippocampus
- Description of file contents:
  -- Columns from left to right: subject identifier, correlation number, mask, Pearson's correlation
  -- These are all across-run correlations, and have not been averaged in any way, or Fisher transformed

This data accompanies the SCP_mPFC_analyses.Rmd and SCP_hippo_analyses.Rmd scripts.

# License
All code in this repository is licensed under the MIT license.

The data included in this repository is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

# Inquiries
Please contact samantha.audrain at mail.utoronto.ca for questions, comments, or bugs.
