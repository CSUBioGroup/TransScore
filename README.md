# TransScore

## **Source code for TransScore**

Please Cite
 

## Usage

### Task1: Compound-protein affinity prediction

the task aims to predict the affinity which represents the tightness of the compound-protein pair in the binding process

```jsx
python train.py -task affinity_prediction -dataset refined_set
```

### Task2: Compound conformation score

the task aims to score the conformation of a ligand generated by the docking software. the smaller the score, the better the conformation.

```jsx
python train.py -task score -dataset refined_set
```

### Specify hyperparameters

Taking the affinity prediction as an example, we can customize the hyperparameters for training(i.g. learning rate, batch size, number of epoch), for more information, please check source code of [args.py](http://args.py) .

```jsx
python train.py -task affinity -lr 0.001 -batch_size 64 -num_epochs 200
```

## **Run on your datasets**

**NOTICE: The dataset should be divided into the train set,  the val set and the test set.**

Please prepare the file for splitting datasets (protein-compound pair for train, val and test set) for training and a general_data file containing the label and protein-compound pair info. 

```jsx
# dataset splitting file 
pdbid,set
1AHW,train
1AKB,test
...

#general_data file for conformation score task
PDB code, conformation id,compound_smiles,label
1AHW,1-1,O=Cc1ccc(O)c(OC)c1,1.3
1AHW,1-2,O=Cc1ccc(O)c(OC)c1,3.23
1AHW,1-3,O=Cc1ccc(O)c(OC)c1,4.28
1AHW,1-4,O=Cc1ccc(O)c(OC)c1,1.37
1AHW,1-5,O=Cc1ccc(O)c(OC)c1,8.13
1AHW,2-1,O=Cc1ccc(O)c(OC)c1,0.76
1AKB,1-1,CCC[C@@H](O)CC\C=C\C=C\C#CC#C\C=C\CO,7.65
1AKB,1-2,CCC[C@@H](O)CC\C=C\C=C\C#CC#C\C=C\CO,1.25
1AKB,2-1,CCC[C@@H](O)CC\C=C\C=C\C#CC#C\C=C\CO,2.82
...

#general_data file for affinity prediction task
PDB code,compound_smiles,label
1AHW,O=Cc1ccc(O)c(OC)c1,7.9
1AKB,CCC[C@@H](O)CC\C=C\C=C\C#CC#C\C=C\CO,3.2
...

```

## Run the corresponding command line according to the prediction task
```jsx
#conformation score
python train.py -task conformation score -dataset your_dataset_name
#affinity prediction
python train.py -task affinity_prediction -dataset your_dataset_name

```

 

## **Dependencies**

Current code works on Linux/Mac OSx only, you need to modify file paths to work on Windows.

> pandas == 1.3.5
> 

python==3.7.11 

torch ==1.10.2+cu102 

torch-geometric==2.1.0

torch-scatter==2.0.8

torch-sparse==0.6.14 

rdkit==2022.3.5 

numpy==1.21.6
