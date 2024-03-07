# Analysis and Classification of Illicit Texts to Support Police Espionage Management

All the files present in this repository were created and published by Franco Parra to obtain the degree of Civil Engineer in Computer Science at Universidad Técnica Federico Santa María in 2023.

## General Objective

Considering all the dangers associated with the lack of tools and control from guardians, as well as the uncontrolled exposure of minors on the Internet, the purpose of this thesis is to develop a text processing system capable of distinguishing sentences with malicious intent (manipulation, exploitation, or sexual abuse) towards minors using an artificial intelligence model called BERT.

## Specific Objectives

1. Determine the existing risks on the Internet and understand how they can trigger scenarios of manipulation, exploitation, or child sexual abuse.
2. Analyze the state of the art in the detection and prevention of grooming on the Internet to establish which data sources are used, what strategies are employed during data processing, and which models perform best.
3. Implement a BERT artificial intelligence model and adjust parameters to adapt it to the problem context and improve generalization capability.
4. Apply the solution in real cases and comment on the results to verify effectiveness and suggest future improvements.

## Description

In the `notebooks_with_results` folder, you will find the notebooks that originated the results described in the thesis. They are organized hierarchically according to the phase, so `notebooks_with_results/phase_1` refers to the first phase, while `notebooks_with_results/phase_2` refers to the second.

In `notebooks_with_results/phase_1`, there is a single directory: `notebooks_with_results/training`. There are a total of 12 files, each responsible for fine-tuning BERT. They are named using the following format: `<batching_size>BS_<message_batching_size>MBS_<learning_rate>LR_<epochs>E`. Their meanings are as follows:

1. `<batching_size>` is the batch size used during BERT training.
2. `<message_batching_size>` is the size of the message grouping.
3. `<learning_rate>` is the initial learning rate.
4. `<epochs>` is the number of epochs (iterations) to perform during training.

In `notebooks_with_results/phase_2`, there are two directories: `preprocessing` and `hypertuning_training`. In `notebooks_with_results/phase_2/preprocessing`, there is a single notebook that uses the results from the first phase to obtain the attentions of BERT. The naming convention follows the same pattern as described earlier.

On the other hand, in `notebooks_with_results/phase_2/hypertuning_training`, there are a total of 4 files, each responsible for hyper-tuning and training the architecture tasked with detecting suspicious conversations. They are named using the following format: `<batching_size>BS_<message_batching_size>MBS_<learning_rate>LR_<epochs>E_<seed>S`. Their meanings are the same as previously described, with the addition of `<seed>` representing the seed to control randomness.

## Next Steps

To recreate these models locally and continue the research, the `notebooks_as_templates` folder is defined, containing 3 notebooks:

1. `phase_1_training.ipynb`: Fine-tunes the BERT model.
2. `phase_2_preprocessing.ipynb`: Obtains the attentions of the model trained in `phase_1_training.ipynb` and generates a new dataset.
3. `phase_2_hypertuning_training.ipynb`: Hyper-tunes and trains the architecture responsible for detecting suspicious conversations.

The `inputs` folder contains a template of all inputs in the 3 notebooks, while `outputs` contains their outputs. It is important to note that **the PAN2012 dataset is not included** as it is private. However, it can be obtained by following [this](https://zenodo.org/record/3713280) link and sending an email request.

> All notebooks were modified to accept local files, as many of them were on the Kaggle cloud.