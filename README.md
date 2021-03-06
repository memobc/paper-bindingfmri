# The Paper
This repository includes scripts and data for the following paper:

[**Cooper, R. & Ritchey, M. (2020). Progression from feature-specific brain activity to hippocampal binding during episodic encoding. _Journal of Neuroscience_, 40(8), 1701-1709**](https://www.jneurosci.org/content/40/8/1701)

# Abstract
The hallmark of episodic memory is recollecting multiple perceptual details tied to a specific spatial-temporal context. To remember an event, it is therefore necessary to integrate such details into a coherent representation during initial encoding. Here we tested how the brain encodes and binds multiple, distinct kinds of features in parallel, and how this process evolves over time during the event itself. We analyzed data from 27 human subjects (16 females, 11 males) who learned a series of objects uniquely associated with a color, a panoramic scene location, and an emotional sound while functional magnetic resonance imaging data were collected. By modeling how brain activity relates to memory for upcoming or just-viewed information, we were able to test how the neural signatures of individual features as well as the integrated event changed over the course of encoding. We observed a striking dissociation between early and late encoding processes: left inferior frontal and visuo-perceptual signals at the onset of an event tracked the amount of detail subsequently recalled and were dissociable based on distinct remembered features. In contrast, memory-related brain activity shifted to the left hippocampus toward the end of an event, which was particularly sensitive to binding item color and sound associations with spatial information. These results provide evidence of early, simultaneous feature-specific neural responses during episodic encoding that predict later remembering and suggest that the hippocampus integrates these features into a coherent experience at an event transition.

# Resources
Scripts to run the task in Psychtoolbox as well as links to stimuli can be found [here](https://github.com/memobc/paper-orbitfmri).

The R script - `Encoding-BindingfMRI-Analysis.Rmd` - to run all analyses on single trial betas can be found in the [`analysis`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis) folder, and the corresponding report can be accessed [here](http://www.thememolab.org/paper-bindingfmri/analysis/Encoding-BindingfMRI-Analysis.nb.html). The whole-brain parcellation - `bindingfmri_wholebrain_ROIs.nii`, which uses the 200-parcel atlas from [Schaefer et al. (2018)](https://github.com/ThomasYeoLab/CBIG/tree/master/stable_projects/brain_parcellation/Schaefer2018_LocalGlobal) - and corresponding .csv file with ROI ID numbers can be found in the [`data`](https://github.com/memobc/paper-bindingfmri/tree/master/data) folder.

The output of all whole brain linear mixed effects analyses can be found in the [`analysis`](https://github.com/memobc/paper-bindingfmri/tree/master/analysis) folder, which contains [csv files](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-csv-results) with statistics for every region, [nifti files](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-t-maps) showing whole brain t statistics and those that pass FDR-correction for multiple comparisons, and [png images](https://github.com/memobc/paper-bindingfmri/tree/master/analysis/wholebrain-images) visualizing the significant results.

The workflow of the main script - `Encoding-BindingfMRI-Analysis.Rmd` - is as follows:

1. Load all behavioral data from `AllSubjects_bindingfMRI-behavior.csv` and label each trial according to successful retrieval of i) color, ii) sound, iii) scene features, and iv) total number of details recalled (0-3).
2. Load single trial beta [files](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas) for all subjects, separately for [onset](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas/event-onset) and [offset](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas/event-offset) activity, removing influential betas and merging with behavioral data.
3. Run linear mixed effect models, predicting onset and offset activity in each region from subsequent memory detail for the upcoming or just-viewed event, respectively. Whole-brain statistics saved as `memorydetail_effects_onsetoffset.csv`.
4. Run control analyses showing that the results of (3) are robust by i) including memory on the immediately adjacent trial as a covariate - saved as `memorydetail_effects_covariate.csv` -, ii) showing that hippocampal memory correlates at the end of the event are not present [throughout](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas/6s-event) the encoding trial - saved as `memorydetail_effects_eventepoch.csv` -, and iii) showing that the results of the onset- and offset-based analyses look extremely similar to predicting activity during each [1s ITI](https://github.com/memobc/paper-bindingfmri/tree/master/data/single-trial-betas/1s-ITI) with memory for the upcoming or preceding event - saved as `memorydetail_effects_ITI.csv`.
5. Run linear mixed effect models, predicting onset and offset activity in each region from subsequent color, sound, and scene memory (3 regressors to capture unique feature effects). Whole-brain statistics saved as `feature_effects_onsetoffset.csv`.
6. Run control analyses showing that the hippocampal memory effect from (5) is not present throughout the encoding trial - whole brain results saved as `feature_effects_eventepoch.csv`.
7. Visualize and contrast subsequent memory results for 5 regions - hippocampus, inferior frontal gyrus, ventral temporal cortex, auditory cortex, and retrosplenial/parahippocampal cortex - at event onset and offset.
8. Run a linear mixed effects model predicting end-of-event hippocampal activity with each unique combination of features subsequently recalled. An exploratory analysis is also run in separate anterior and posterior segments.

# License

All data included in this project is licensed under the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/), and all code is licensed under the [MIT license](https://github.com/memobc/paper-orbitencoding/blob/master/LICENSE).

# Comments?

Please direct any comments to Rose Cooper, rose.cooper at bc.edu. Please feel free to use any of these scripts. Unfortunately I cannot provide support for you to adapt them to your own data. Notice a bug? Please tell me.
