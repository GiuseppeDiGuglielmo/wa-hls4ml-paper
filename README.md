# wa-hls4ml-paper
Code for plots, models, data generation and other utilities relating to the paper "wa-hls4ml: A Benchmark and Surrogate Models for hls4ml Resource and Latency Estimation"

## Using this repo

This repo uses git submodules. To use this repo, you need to initialize and update the submodules using the following command in the root of the repository after cloning it:

Note that some of the submodules are large (>1GB)

```bash
git submodule update --init --recursive
```

## Surrogate Models & Training

The code used to train and evaluate the surrogate models as described in the paper are available in the `wa_hls4ml_models` directory. Please see [the README file](wa_hls4ml_models/README.md) in `wa_hls4ml_models` directory for more details on how to setup and train the models.

## Dataset Generation 

The code used to generate dataset is available in the `wa-hls4ml-search` directory. Please see [the README file](wa-hls4ml-search/README.md) in `wa-hls4ml-search` directory for more details on how to generate the dataset.

# Training, Validation, Test, and Exemplar Test Datsets

The datasets that were generated using the code in the `wa-hls4ml-search` directory are available on either Huggingface or the American Science Cloud's Fermi Data Platform. For more details on the datasets themselves, please see the Dataset cards included with each dataset (the README.md in the root of the dataset directories)

* Results Dataset (containing inputs and outputs used to train and evaluate both surrogate models)
  * [HuggingFace](https://huggingface.co/datasets/fastmachinelearning/wa-hls4ml)
  * [Fermi Data Platform](https://amsc.fnal.gov:2880/amsc/axess/wa-hls4ml/)
* Projects Dataset (containing the full AMD Vitis/Vivado projects for each sample in the Results Dataset. See the .csv files in the root of the dataset directory for mappings from each sample in the results dataset to the location of the corresponding project tarball)
  * [HuggingFace](https://huggingface.co/datasets/fastmachinelearning/wa-hls4ml-projects)
  * [Fermi Data Platform](https://amsc.fnal.gov:2880/amsc/axess/wa-hls4ml-projects/)

## Plots & Analysis

The code used to generate the plots from the paper are in a few different places.

* Results for the GNN and Transformer based surrogate models are available in the `wa_hls4ml_models` directory
  * The results plots for the GNN (Fig. 9 and Fig. 10 in the paper) are available in the [`wa_hls4ml_models/GNN/utils/plot.py`](wa_hls4ml_models/GNN/utils/plot.py) code, which has helper functions in the [`wa_hls4ml_models/GNN/utils/Utils.py`](wa_hls4ml_models/GNN/utils/Utils.py) script.
  * The results plots for the Transformer (Fig. 11 and Fig. 12 in the paper) are available in the [`wa_hls4ml_models/transformer/plot.py`](wa_hls4ml_models/transformer/plot.py) script, which is used at training time to generate the plots via the [`wa_hls4ml_models/transformer/run.py`](wa_hls4ml_models/transformer/run.py) script.
  * The code used to generate the results plots for the Baseline MLP (Fig. 7 and Fig. 8 in the paper) is currently in the process of being added to this repo.  
* The used to generate the plots showing the dataset distribution (Fig. 2 and Fig. 3 in the paper) are available in the [`wa-hls4ml-search/plots/generate_plots.ipynb`](wa-hls4ml-search/plots/generate_plots.ipynb) script. Be warned that the notebook loads and processes a large dataset, so generating the plots in this notebook take a while to run. Additionally, if you output the plots as PDFs, they are very large, so it is recommended to output them as PNGs instead.
* The code used to generate the plots comparing the GNN and transformer predictions to the actual values (Fig. 13 through Fig. 18) is in [`wa_hls4ml_models/GNN/utils/plot.py`](wa_hls4ml_models/GNN/utils/plot.py) and [`wa_hls4ml_models/transformer/plot.py`](wa_hls4ml_models/transformer/plot.py).
* The code used to generate the plot showing the distribution of labels within the train, validation, test, and exemplar datasets (Fig. 4) is available in the [`wa_hls4ml_models/notebooks/exemplar_dataset_visualization.ipynb`](wa_hls4ml_models/notebooks/exemplar_dataset_visualization.ipynb) script. 
* Figures 1, 5, and 6 were generated in either Google Slides or Keynote, the files for which are included in [figures](figures/) as .pptx, .svg, and .key files as they are available (some were automatically converted, so there may be slight inaccuracies comapred to the figures in the paper), as well as the generated .pdf files used in the paper.

## Using the surrogate models

The current recommended method to use the surrogate models is to use the [rule4ml](https://github.com/IMPETUS-UdeS/rule4ml) python package, which as of version `0.2.0` implements a slightly updated version of the GNN model trained on the same datasets.

Please see the repository linked above for code, examples, and documentation of how to use rule4ml. 

## Paper and Citation

You may view the paper on arXiv [here](https://arxiv.org/abs/2511.05615). The paper has been accepted by ACM's Transactions on Reconfigurable Technology and Systems (TRETS) Journal for their special issue on Open Source Tools. It is currently in the process of being published, and the citation will be updated when it is available. 

If you use or extend this work, citing this paper is highly encouraged and appreciated. Please use the following citation:

```bibtex
@misc{hawks2025wahls4mlbenchmarksurrogatemodels,
      title={wa-hls4ml: A Benchmark and Surrogate Models for hls4ml Resource and Latency Estimation}, 
      author={Benjamin Hawks and Jason Weitz and Dmitri Demler and Karla Tame-Narvaez and Dennis Plotnikov and Mohammad Mehdi Rahimifar and Hamza Ezzaoui Rahali and Audrey C. Therrien and Donovan Sproule and Elham E Khoda and Keegan A. Smith and Russell Marroquin and Giuseppe Di Guglielmo and Nhan Tran and Javier Duarte and Vladimir Loncar},
      year={2025},
      eprint={2511.05615},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2511.05615}, 
}
```

## Licenses

The surrogate models are available under the Creative Commons Attribution Non Commercial 4.0 license. 

The original code used to train the model is copyright the original authors [Jason Weitz](https://orcid.org/0009-0004-6315-3562) and [Dmitri Demler](https://orcid.org/0009-0009-9453-9755) of [University of California San Diego](https://ucsd.edu/) available under the Apache License 2.0. The rule4ml implementation is copyright the rule4ml authors, [Hamza Ezzaoui Rahali](https://orcid.org/0000-0002-0352-725X) and [Mohammad Mehdi Rahimifar](https://orcid.org/0000-0002-6582-8322) of [Université de Sherbrooke](https://www.usherbrooke.ca/), available under the GNU General Public License v3.0. The code used to generate the dataset is copyright [Fermilab](https:www.fnal.gov), available under the Apache License 2.0.

Some figures in the [`figures`](figures/) are copyright [Jason Weitz](https://orcid.org/0009-0004-6315-3562) and [Dmitri Demler](https://orcid.org/0009-0009-9453-9755) of [University of California San Diego](https://ucsd.edu/) (The figures representing the surrogate model architectures, Fig. 5 and Fig 6.). The remaining figure (The figure representing the proposed codesign workflow using wa-hls4ml, Fig. 1) is authored by [Ben Hawks](https://orcid.org/0000-0001-5700-0288) and copyright [Fermilab](https://fnal.gov), and all figures included in the directory are licensed under Creative Commons Attribution-NonCommercial 4.0 International.

## Contact

This README.md was authored by [Ben Hawks](https://orcid.org/0000-0001-5700-0288) and copyright [Fermilab](https://fnal.gov). The Repository (not including submodules) is licensed under the Creative Commons Attribution-NonCommercial 4.0 International license.

If you would like to reach out with questions about the project, paper, code, or any potential collaboration or extension regarding this work, please reach out to any of the following people. 

[Benjamin Hawks](https://orcid.org/0000-0001-5700-0288), Fermi National Accelerator Laboratory, USA - [bhawks@fnal.gov](mailto:bhawks@fnal.gov)

[Audrey Corbeil Therrien](https://orcid.org/0000-0001-6698-8400) - University of Sherbrooke, Canada - [audrey.corbeil.therrien@usherbrooke.ca](mailto:audrey.corbeil.therrien@usherbrooke.ca)

[Hamza Ezzaoui Rahali](https://orcid.org/0000-0002-0352-725X), University of Sherbrooke, Canada - [hamza.ezzaoui.rahali@usherbrooke.ca](mailto:hamza.ezzaoui.rahali@usherbrooke.ca)

[Mohammad Mehdi Rahimifar](https://orcid.org/0000-0002-6582-8322), University of Sherbrooke, Canada - [mohammad.mehdi.rahimifar@usherbrooke.ca](mailto:mohammad.mehdi.rahimifar@usherbrooke.ca)
