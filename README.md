# DualFraud
## Repo Structure

The repository is organized as follows:

 - `dataset/`: dataset folder
    - `synthetic_company`: Data of the synthetic company;
    - `synthetic_transaction`: Data of the synthetic transaction;
    - `real_company`: Data of the real-world company;
    - `real_transaction`: Data of the real-world transaction;
- `model/`: model folder
    - `DualFraud.ipynb`: data, model and training/testing code for DualFraud and DualFraud-S;
- `utils/`: functions folder
    - `synthetic_structsim.py`: generate structures for the synthetic dataset;
    - `featgen.py`: generate features for nodes in the synthetic dataset;



Detailed structure in `DualFraud.ipynb`: 

- `Set up`: required python packages

- `Data`: Data generation and process
  - `Synthetic Data`: Synthetic data generation;
  - `Real-World Data`: Data process for real-world data;
- `Model`: Model and train/test code
  - `Parameters`: parameters of the model;
  - `Layer`: Layer definition including GraphConvLayer, MLPAttentionNetwork and BiLSTMAttentionNetwork;
  - `Model`: Model definition of DualFraud;
  - `GNNExplainer`: [GNNExplainer](https://pytorch-geometric.readthedocs.io/en/latest/_modules/torch_geometric/nn/models/gnn_explainer.html) model from Pytorch geometric;
  - `DualFraud: Train/Test`: Training and testing code for DualFraud;
  - `DualFraud-S: Train/Test`: Training and testing code for DualFraud-S;
  - `Explainer`: explainer component to generate explainations for enterprises and transations. 



## Dataset

We build Synthetic and Real-world datasets for experiments:

|                                 | Nodes(Fraud%) | #Features | Relation                        | #Edges                                |
| ------------------------------- | ------------ | --------- | ------------------------------- | ------------------------------------- |
| Synthetic Enterprise            | 1143(10.5%)  | 8         | C-C                             | 1181                                  |
| Synthetic Transaction           | 4575(10.5%)  | 8         | T-T                             | 4749                                  |
| Real-world Enterprise(HAT)      | 13489(26.4%) | 89        | C-I-C<br/>C-C<br/>C-M-C<br/>ALL | 53874<br/>15908<br/>139413<br/>209195 |
| Real-world Transaction(BankSim) | 50000(1.2%)  | 23        | T-A-T                           | 206666                                |



## How to Run

You can download the project and and run the program as follows:

1. Unzip datasets in the dataset folder `\dataset`
2.  Install the required packages using the `requirements.txt`;

```python
pip install -r requirements.txt
```

3. Run code in `DualFraud.ipynb` to run DualFraud. 

\* To run the code, you need to have at least **Python 3.6** or later versions.



## Run on your Datasets

To run DualFraud on your datasets, you need to prepare the following data for enterprises and transactions separately:

- Multiple-single relation graphs with the same nodes where each graph is stored in adjacency matrix format;
- An array with node labels;
- A node feature matrix.

