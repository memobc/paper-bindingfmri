# The Paper
This repository includes scripts and data for the following paper:

[**Cooper, R. & Ritchey, M. (preprint). Transformation of feature-specific neural activity to hippocampal spatial binding during episodic encoding.**]()

# Abstract
The hallmark of episodic memory is recollecting multiple perceptual details tied to a specific spatial-temporal context. To remember an event, it is therefore necessary to integrate such details into a coherent representation during initial encoding. Here we tested how the brain encodes and binds multiple, distinct kinds of features in parallel, and how this process evolves over time during the event itself. We analyzed data from 27 subjects who learned a series of objects uniquely associated with a color, a panoramic scene location, and an emotional sound while fMRI data were collected. By modeling brain activity at event onset and event offset, we were able to test how the neural signatures of individual features as well as the integrated event changed over the course of encoding. We observed a striking dissociation between early and late encoding processes: left inferior frontal and sensory signals at event onset tracked the amount of detail subsequently recalled and were dissociable based on distinct remembered features. In contrast, memory-related brain activity shifted to the left hippocampus at event offset, which was particularly sensitive to binding item color and sound associations with spatial information. These results provide evidence of simultaneous feature-specific neural responses at the start of episodic encoding that predict later remembering and show that the hippocampus acts to integrate these features into a spatially-coherent experience at an event transition.

# Resources
Scripts to run the task in Psychtoolbox as well as links to stimuli can be found [here](https://github.com/memobc/paper-orbitfmri).

The R script - `Encoding-BindingfMRI-Analysis.Rmd` - to run all analyses on single trial betas can be found in the [`analysis`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis) folder, and the corresponding report can be accessed [here](http://www.thememolab.org/paper-orbitfmri/reports/Encoding-BindingfMRI-Analysis.nb.html). The whole-brain parcellation - `bindingfmri_wholebrain_ROIs.nii` - and corresponding .csv file with ROI ID numbers can be found in the [`data`](https://github.com/memobc/paper-bindingfmri/tree/master/data) folder.

The workflow of the R analysis script is as follows:

1. Load all behavioral data from `AllSubjects_bindingfMRI-behavior.csv` and label each trial according to successful retrieval of i) color, ii) sound, iii) scene features, and iv) total number of details recalled (0-3).
2. Load single trial beta [files](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas) for all subjects, separately for onset and offset activity, removing influential betas and merging with behavioral data. 
3. Run linear mixed effect models, predicting onset and offset activity in each region from subsequent memory detail. Save whole-brain statistics as [`memorydetail_effects.csv`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-csv-results). Nifti maps of whole-brain t values can be found [here](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-t-maps).
4. Run linear mixed effect models, predicting onset and offset activity in each region from subsequent color, sound, and scene memory. Save whole-brain statistics as [`feature_effects.csv`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-csv-results). Nifti maps of whole-brain t values can be found [here](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-t-maps).
5. Visualize subsequent memory results for 5 regions - hippocampus, inferior frontal gyrus, ventral temporal cortex, auditory cortex, and retrosplenial/parahippocampal cortex. 
6. Run a linear mixed effects model predicting hippocampal onset and offset activity for each combination of features subsequently recalled.

# License

All data included in this project is licensed under the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/), and all code is licensed under the [MIT license](https://github.com/memobc/paper-orbitencoding/blob/master/LICENSE).

# Comments?

Please direct any comments to Rose Cooper, rose.cooper at bc.edu. Please feel free to use any of these scripts. Unfortunately I cannot provide support for you to adapt them to your own data. Notice a bug? Please tell me.
