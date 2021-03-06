# ProtRA
Predictor for lipid accessibility and solvent accessibility of proteins 
## Introduction
In models.py, we provide the definition and implementation of the final model (Transformer light) and other models in the article.

driver.py is a simple demonstration of how to process input data and process models

prot.feat, prot.fasta are example files
### Quick start
We provide a prediction server to meet researchers' small batch sample prediction needs.
  
  http://www.songlab.cn/ProtRA/Introduction/
### Requirements
* PyTorch
* NumPy
### Feature generation
Our model requires One-hot encoded sequence information (20 bits), PSSM (20 bits) and predicted SS3 (3 bits) as input features.

The order of One-hot encoding is: ACDEFGHIKLMNPQRSTVWY,
we provide the seq2arr function in the driver.py file

PSSM and predicted SS3 were generated by [RaptorX-Property](https://github.com/realbigws/RaptorX_Property_Fast) aligning against database [uniclust30_2017_10](http://wwwuser.gwdg.de/~compbiol/uniclust/2017_10/). The file suffix is .feat, and we provide the load_feat function in the driver.py file
### Usage
First download the weights file we provided in Releases. Then use `torch.load(absolute path)` to load the model.

Our driver.py provides easier usage:
```bash
python driver.py --data prot --model_path absolute_path
```