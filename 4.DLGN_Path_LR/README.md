
## 4.DLGN_Path_LR  

This is a 2D regression data as in figure data.png with the yellow top left patch being +1, bottom violet -1, top right dark green 0.2, and beneath that light green 0.5 as regression values.

The corresponding code for the experiments is **DLGN_Path_LR.ipynb**.  
The notebook **Variable parameters** tab contains all the variables that can be changed according to the need of the experiment. Defination and usage of all the variables are given as comment in the notebook.  
For this experiment, **model_type** is set to **Regression**.  

The folder contains **Saved_models** where all the pretrained models are saved: 

The first two prefixes in each model represent as follows:  
*No_node* refers to when none of the nodes in NPF and NPV is freezed. That is, their weights can vary. This can be achieved by keeping *freeze* and all other variables as *False*.  
*NPF_Fixed* -- Here, NPF is fixed at initialization, and only NPV is varying, done by setting *NPF_freeze* to *True* and the rest of all variables as *False*.  
*NPV_Fixed* -- Here, NPV is fixed at initialization, and only NPF is varying, done by setting *NPV_freeze* to *True* and the rest of all variables as *False*.  
*NPF_pretrained_Fixed* -- NPF is fixed after training the entire network, and only NPV is varying and trained from reinit, done by setting *NPF_pretrained_freezed* to *True* rest all variables as *False*.  
*NPV_pretrained_Fixed* -- NPV is fixed after training the entire network, and only NPF is varying and trained from reinit, done by setting *NPV_pretrained_freezed* to *True* rest all variables as *False*.  


For training or inference or both set the flags of training/inference to True for DLGN model and any of the Path_LR or DLGN_LR model accordingly with which DLGN loss we want to compare. Mostly loss of DLGN no node fixed is compared with hybrid DLGN_LR loss and DLGN NPF_Fixed and NPF_pretrained_Fixed loss is compared with Path_LR counter part loss.

### Set Training or inference or both

### For the DLGN model

train_model = False #Set to true if training a model and False if only infer a trained model

infer_model = True #Set to true if infer a pretrained model or infer along with training


### For the Path_LR model

train_lr = False #Train the Path_LR model

infer_path_lr = False #Infer the Path_LR model


### For the DLGN_LR hybrid model

train_dlgn_lr = False #Train the hybrid DLGN_LR model (DLGN_LR_FC)

infer_dlgn_lr = True #Infer the hybrid DLGN_LR model (DLGN_LR_FC)


**All Pretrained MODELS** tab in the code contains all the pretrained model names as variables

Any of the models (file_name_load) can be uncommented to infer the pretrained DLGN (NPF-NPV) model by setting infer_model = True and train_model = False

 Any of the models (file_name_load_lr) can be uncommented to infer the pretrained Path_LR (NPF-gates as feature to LR ) model by setting infer_path_lr = True and train_lr = False

To infer the DLGN and (Path_LR models or DLGN_LR) both and to compare the loss of two pre-trained models(DLGN vs (Path_LR or DLGN_LR)) set train_model = False, infer_model = True and (train_lr = False, infer_path_lr = True or train_dlgn_lr = False,infer_dlgn_lr = True) and uncomment any of the below pairs(file_name_load for DLGN and (file_name_load_lr for Path_LR or file_name_load_dlgnlr)) with similar training grounds

To understand the models naming convention is as follows: 
file_name_load = file_path + "R_NPF_Fixed_0.2L_3L5N_Beta_1000_npf_seed_1_npv_seed_1.npz"

R_ -> Regression square tree shaped data, NPF_Fixed/NPF_pretrained_Fixed/No_node -> npf model fixed at random or pretrained of not fixed while NPV is trained from init (same naming for NPV_Fixed/pretrained)
0.2L -> no of epochs = 0.2Lakh=20k, 3L5N -> 3 Layer network with 5 nodes in each Layer, Beta_1000 -> beta value 1000, npf_seed 1 npv_seed 1


## How to Run

## To infer pretrained model
**Step1:** Make necessary changes to the **Variable parameters** tab accordingly like setting num_hidden_nodes =[5,5,5] or [2,2,2] as in the model to be run.
 
**Step2:** Follow the "Training/Inference Flag" guidelines and set True/False values accordingly.

**Step3:** Uncomment the blocks (e.g. line 181(file_name_load),182(file_name_load_dlgnlr)) following the instructions given in **All Pretrained MODELS** tab

**Step4:** Run all the tabs till **Losswise comparision of DLGN and LR or DLGN_LR models** and before **Results**.

**Step5:** **Result Visualization** tab contains all the function and their definition which can be used to get desired results for visualization as follows:

### set the variables

enter_path = (0,0,0)  #enter the path

plot_epoch = 5000 #enter the epoch no. till which result is needed

enter_epoch = 5000 #enter the epoch no. whose results are needed

weight_model_type = "DLGN"  #Path_LR --> for Path_LR, DLGN_LR for DLGN_LR and DLGN for DLGN


### Plot the test data actual and predicted
data_pred_scatter_plot(predictions_lr) #predictions_lr --> for Path_LR model,predictions_dlgn_lr --> for DLGN_LR model,predictions_dlgn --> for DLGN model 

### To check if NPF*NPV giving expected output
check_sanity(weight_model_type,enter_epoch)

### To print the path values, data fraction covered by the path, mean, s.d of the portion covered by the path
 _,path_val=print_any_path(plot_epoch,enter_epoch,weight_model_type,find_path=enter_path)

### To plot all the path values with epoch, data fraction covered by the path, mean, s.d of the portion covered by the path
plot_all_paths(plot_epoch,enter_epoch,weight_model_type)

### Path value visualization of one path
plot_path_value_variation(enter_path,plot_epoch,weight_model_type)

### To show the portion of the data covered by the path in the dataset
show_path_hyp(enter_path,enter_epoch,weight_model_type)

### All node hyperplane visualization
show_node_hyp(enter_epoch,weight_model_type)

## To train a new model
**Step1:** Make necessary changes to the **Variable parameters** tab accordingly as per need to train the model.
 
**Step2:** Follow the "Training/Inference Flag" guidelines and set True/False values accordingly.

**Step3:** DLGN model will be saved with names as per the parameters automatically using the tab **Storing the trained output** and for the DLGN_LR or Path_LR model give the name accordingly in line 55 file_name_load_dlgnlr= file_path+"dlgn_lr_model.npz" or line 56 file_name_load_lr = file_path+"Path_LR_test.npz"


**Step4:** Run all the tabs till **Losswise comparision of DLGN and LR or DLGN_LR models** and before **Results**. Then use the same functions as above to infer the models.


## Authors

- [@Doeschate](https://github.com/Doeschate)

