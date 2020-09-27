# SetToGraphPaper
This repository holds the code for the paper: https://arxiv.org/abs/2002.08772.

## Data
Before running the code for the jets experiments, the data should be downloaded using the following commands:

```
cd SetToGraphPaper
python download_jets_data.py
```

This script will download all the data from Zenodo links. 



## Code

### Prerequisites

You can use the following code to install a compatible environment (using anaconda), make sure to change the cuda toolkit version to the one that fits.
```
conda create -n s2g_env -c pytorch pytorch=1.5 cudatoolkit=10.2 torchvision  
conda activate s2g_env
CUDA=cu102  # for cuda 10.2
pip install torch-scatter==latest+${CUDA} -f https://pytorch-geometric.com/whl/torch-1.5.0.html
pip install torch-sparse==latest+${CUDA} -f https://pytorch-geometric.com/whl/torch-1.5.0.html
pip install torch-cluster==latest+${CUDA} -f https://pytorch-geometric.com/whl/torch-1.5.0.html
pip install torch-spline-conv==latest+${CUDA} -f https://pytorch-geometric.com/whl/torch-1.5.0.html
pip install torch-geometric
conda install -c conda-forge -c anaconda tqdm easydict rdkit uproot
```


### Running the tests

The folder main_scripts contains scripts that run different experiments:
1. To run the main paticle-physics jets experiment with our chosen hyper-parameters, run the one of the following:
```
python main_scripts/main_jets.py --method=lin2  # for S2G
```
or 
```
python main_scripts/main_jets.py --method=lin5  # for S2G+
```
or change `--method=...` with `--baseline=siam/siam3/gnn/mlp` for running a baseline. 

2. To run the Delaunay triangulation with our hyper-parameters, run the main_delaunay.py script with the options `--many_sizes`/`--one_size` for n=50 or n\in{20,...,80}.
Example:
```
python main_scripts/main_delaunay.py --one_size --method=lin2
```
