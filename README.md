# The Paper

This repository includes scripts and data for the following paper:

[**Cooper, R. & Ritchey, M. (preprint). Transformation of feature-specific neural activity to hippocampal spatial binding during episodic encoding.**]()

# Abstract

# Resources

Scripts to run the task in Psychtoolbox as well as links to stimuli can be found [here](http://www.thememolab.org/paper-orbitfmri/).

The R script - `Encoding-BindingfMRI-Analysis.Rmd` - to run all analyses using the single trial [`data`](https://github.com/memobc/paper-bindingfmri/tree/master/data) can be found in the [`analysis`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis) folder.

The workflow of this analysis script is as follows:

1. Load all behavioral data from `AllSubjects_bindingfMRI-behavior.csv` and label each trial according to successful retrieval of i) color, ii) sound, iii) scene features, and iv) total number of details recalled (0-3).
2. Load single trial betas [files](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas) for all subjects, separately for onset and offset activity, removing influential betas and merging with behavioral data. 
3. Run linear mixed effects models, predicting onset and offset activity in each region from subsequent memory detail. Save whole-brain statistics as [`memorydetail_effects.csv`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-csv-results). NIfTI maps of whole-brain t statistics can be found [here](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-t-maps).
4. Run linear mixed effects models, predicting onset and offset activity in each region from subsequent color, sound, and scene memory. Save whole-brain statistics as [`feature_effects.csv`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-csv-results). NIfTI maps of whole-brain t statistics can be found [here](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-t-maps).
5. Visualize subsequent memory results for 5 regions - hippocampus, inferior frontal gyrus, ventral temporal cortex, auditory cortex, and medial temporal cortex. 
6. Run a linear mixed effects model predicting hippocampal onset and offset activity for each combination of features subsequently recalled.

# License

All data included in this project is licensed under the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/), and all code is licensed under the [MIT license](https://github.com/memobc/paper-orbitencoding/blob/master/LICENSE).

# Comments?

Please direct any comments to Rose Cooper, rose.cooper at bc.edu. Please feel free to use any of these scripts. Unfortunately I cannot provide support for you to adapt them to your own data. Notice a bug? Please tell me.
