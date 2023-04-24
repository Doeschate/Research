
## 5.FMNIST_patched 


The corresponding code for the experiments is **DLGN_Fashion_MNIST_patched.ipynb**.  
The notebook **Parameters** tab contains all the variables that can be changed according to the need of the experiment. Defination and usage of all the variables are given as comment in the notebook.  


The folder contains **Saved_models** where all the pretrained models and error files are saved: 

For visualizing the results set both model_training and model_inference to False 

model_training = False #True --> to train a new model else False
model_inference = False #True --> to generate error files(error vs epoch plots) else false


To understand the models naming convention is as follows: 
DLGN_95_white_patch="DLGN_95_white_patch_no_extra_data_lr_.0001_epoch_1k_seed_365.npz"

DLGN_xx/ReLU_xx -> based on DLGN or DNN with ReLU model 
95_white_patch_no_extra_data -> it means 95% of the dataset is made corrupted by putting 4x4 white patch based on the classes and no extra data is used to replace the corrupted data. 
lr_.0001 -> learning rate 0.0001 
epoch = 1l and seed = 365


## How to Run

## To visualize pretrained model
**Step1:** Make necessary changes to the **Variable parameters** tab accordingly like setting num_hidden_nodes =[10,10,10] or [5,5,5] as in the model to be run.
 
**Step2:** Set both *model_training* and *model_inference* to False.

**Step3:** Run all the tabs till **Node Visualization**. Change  the file name to visualize accordingly in file_name_load=file_path+DLGN_95_white_patch.


**Step4:** Run all the tabs till before **Results** to get the visualization of nodes activity.

**Step5:** Change the error file name (error_file = error_dlgn_95_white_patch) in Error File update accordingly and run all rest of the cells to get the error vs epoch plots for train and test.


## To train a new model
**Step1:** Make necessary changes to the **Parameters** tab accordingly as per need to train the model.
 
**Step2:** Set both *model_training* and *model_inference* to True for training and generating error files.

**Step3:** **file_name1** and **error_file** can be uncommented and given any name of choice to save the model and error results


**Step4:** Run all the tabs till Inference. Then use the same visualization as above.


## Authors

- [@Doeschate](https://github.com/Doeschate)

