# LEAR: Lexical Entailment Attract-Repel
Specialising Word Vectors for Lexical Entailment (Vulić and Mrkšić, 2017).

Contact: Nikola Mrkšić (nikola.mrksic@gmail.com)

This repository contains the code and data for the Lexical Entailment Attract-Repel (LEAR) method presented in [Specialising Word Vectors for Lexical Entailment](https://arxiv.org/abs/1710.06371). The word vectors which achieve the state of the art on the HyperLex dataset can be downloaded [here](https://drive.google.com/open?id=0B_pyA_IW4g-jdmRiR0EzTEVQcGc).


### Configuring the Tool

The LEAR tool reads all the experiment config parameters from the ```experiment_parameters.cfg``` file in the root directory. An alternative config file can be provided as the first (and only) argument to ```code/lear.py```. 

The config file specifies:
* the location of the initial word vectors (```distributional_vectors```);
* the sets of linguistic constraints to be injected into the vector space (```antonyms```, ```synonyms_sym```, ```synonyms_asym``` );

The config file also specifies the hyperparameters of the LEAR procedure (set to their default values in ```config/experiment_parameters.cfg```). 

The evaluation directory contains the SimLex-999 dataset (Hill et al., 2014), the SimVerb dataset (Gerz et al., 2016), and the HyperLex dataset (Vulić et al., 2017). 


### Running Experiments

```python code/lear.py config/experiment_parameters.cfg```

Running the experiment loads the word vectors specified in the config file and fits them to the provided linguistic constraints. The procedure prints the updated word vectors to the results directory as ```results/final_vectors.txt``` (one word vector per line). 


### References

The paper which introduces the LEAR procedure:
```
 @inproceedings{Vulic:2018naacl,
  author    = {Ivan Vuli\'{c} and Nikola Mrk\v{s}i\'c},
  title     = {Specialising Word Vectors for Lexical Entailment},
  booktitle   = {Proceedings of NAACL-HLT},
  year      = 2018,
  pages = 1134--1145,
 }
```

If you are using WordNet (Miller, 1995) constraints, please cite these papers. If you are using BabelNet constraints, please cite (Navigli and Ponzetto, 2012).


### Prerequisites
#### How to prepare the environment for running the program with Windows 10
To make tensorflow runnable on Windows without an nvidia card, some extra prerequisites are necessary:

1. Install nvidia CUDA from here: https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_local
2. Add the path of the Cuda Tookit/bin folder to hte PATH variable. 
3. Install Anaconda for Windows. In order to do this follow the instructions here: https://docs.anaconda.com/anaconda/install/windows/
4. In Anaconda create a new Python environment and install Tensorflow with DirectML package. Open the Anaconda console and follow the instructions described here: https://docs.microsoft.com/en-us/windows/win32/direct3d12/gpu-tensorflow-wsl#install-the-tensorflow-with-directml-package
5. Install the for the import needed packages in the Anaconda console using pip as well.
6. To be able to run the program in the PyCharm IDE, the Anaconda environment needs to be added as Python Interpreter:
    File->Settings->View All->Add->Add Existing; Choose the Folder where the lately created Anaconda environment was stored (e.q. *\AppData\Local\Programs\Anaconda\envs\directml)  



