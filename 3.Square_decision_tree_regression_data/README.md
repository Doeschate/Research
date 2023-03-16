
## 3.Square_decision_tree_regression_data  

This is a 2D regression data as in figure data.png with the yellow top left patch being +1, bottom violet -1, top right dark green 0.2, and beneath that light green 0.5 as regression values.

The corresponding code for the experiments is **DLGN_Fixed_Node.ipynb**.  
The notebook Variable parameters tab contains all the variables that can be changed according to the need of the experiment.  
For this experiment, **model_type** is set to **Regression**.  

The folder contains subfolders with the naming convention as follows:  
**3.Layer_3_node_2_5L_epoch_3L5N_Beta_20** :  
Here, *Layer_3_Node_2* corresponds to Node 2 of Layer 3, whose weight in the gating layer only varies. Rest every node in both NPF and NPV is kept constant.  
*5L_epoch* is the number of epochs to train the model.  
*3L5N* is the model's total number of layers and nodes per layer.  
*Beta_20* is the beta value for the sigmoid function used as the gate. In some folders, *Beta_20_10k* represents the beta value for the layer corresponding to the varying node set to 20, whereas all other nodes are to 10k (on-off gate).  
Here the experiments are conducted by keeping all the nodes of NPF and NPV fixed expect a particular node of a particular layer. **freeze** variable is set to **True** and rest everything **False**.  
Making **freeze** as **False** and running all the cells will generate results where every node varies.  


**layer_num** and **node_num** denote the layer, and the node number of the node whose weights are only varying rest of all other nodes are fixed.

The first two prefixes in each folder represent the training process as follows:  
*No_node* refers to when none of the nodes in NPF and NPV is freezed. That is, their weights can vary. This can be achieved by keeping *freeze* and all other variables as *False*.  
*NPF_Fixed* -- Here, NPF is fixed at initialization, and only NPV is varying, done by setting *NPF_freeze* to *True* and the rest of all variables as *False*.  
*NPV_Fixed* -- Here, NPV is fixed at initialization, and only NPF is varying, done by setting *NPV_freeze* to *True* and the rest of all variables as *False*.  
*NPF_pretrained_Fixed* -- NPF is fixed after training the entire network with 1Lakh epoch, and only NPV is varying and trained from reinit, done by setting *NPF_pretrained_freezed* to *True* rest all variables as *False*.  
*NPV_pretrained_Fixed* -- NPV is fixed after training the entire network with 1Lakh epoch, and only NPF is varying and trained from reinit, done by setting *NPV_pretrained_freezed* to *True* rest all variables as *False*.  


Each folder contains *test_data/train_data* or prefix name (e.g., *NPV_Fixed*) folder with images corresponding to the hyperplane of the nodes of all the layers for each epoch represented as *Epoch_i_.png* for the ith epoch.  
*Best_epoch.pdf* represents the hyperplanes and the prediction corresponding to the epoch with the best validation accuracy.  
*path_value.txt* contains all the path values for the initial, middle, and last epoch.  
*changes_in_weights.png* shows how the weights and biases corresponding to the nodes change with epoch.  

## Authors

- [@Doeschate](https://github.com/Doeschate)

