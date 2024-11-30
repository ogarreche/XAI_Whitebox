# XAI Whitebox Methods

This work uses the following XAI methods:

- DeepLift is applied by using Shap.deepExplainer. See reference: https://shap-lrjball.readthedocs.io/en/latest/generated/shap.DeepExplainer.html

- For LRP and IG. See Innvestigate: https://github.com/albermax/innvestigate

Other notes:

- I uploaded tf23.yml if you want to used the same environemt as we used. 
Note: for importing environment see the Importing Environments section https://conda.io/projects/conda/en/latest/user-guide/cheatsheet.html 


- Robustness is based on https://github.com/dylan-slack/Fooling-LIME-SHAP/

- The metrics are based on: https://ieeexplore.ieee.org/document/9230374

 ### Important
For results interpretation and analysis, please see our paper in (insert link when ready). Thank you! 

If this work helped, please consider citing us :) 

### Datasets:

Download one of the datasets. 

RoEduNet-SIMARGL2021: https://www.kaggle.com/datasets/7f91274fa3074d53e983f6eb7a7b24ad1dca136ca967ad0ebe48955e246c24ee 

CICIDS-2017: [https://www.kaggle.com/datasets/cicdataset/cicids2017](https://www.kaggle.com/datasets/usmanshuaibumusa/cicids-17)

NSL-KDD: [https://www.unb.ca/cic/datasets/nsl.html](https://www.kaggle.com/datasets/hassan06/nslkdd)


### Organization 

This github divides the experiment by folders considering the metrics analyzed and Base model folder. The program in the Base folder is necessary to obtain descriptive accuracy, sparsity, efficiency, and stability. In each folder there is a example program to run to get familiarized with the work.  

### Example: 

1 - Run the DNN_NSL_Example.ipynb for instructions (inside the folder Base_programs).

  The program Loads the NSL-KDD dataset, trains a DNN model, and apply IG, LRP and DeepLift. It outputs the Accuracy of the model and the most important lists for each one the XAI methods with its relative score.

2 - Descriptive Accuracy: Run descriptive_accuracy.ipynb (inside the folder Descriptive Accuracy).

  This program generates the graphs for Descriptive Accuracy. There are further instructions in the program.
  
  As an example: 
  
  - The X axis is the features removed.
  
  - x_axis_nsl = [0, 5, 10, 20, 40, 80] 
  
  - The y axis is the accuracy when such features are removed. You can get these values by running DNN_NSL_Example.ipynb and copying and paste the accuracies into the  descriptive_accuracy.ipynb.
  
  - y_axis_deeplift = [0.8429,	0.78984,	0.5903,	0.690888,	0.56132,	0.5355]
  
  - y_axis_ig = [0.8429,	0.76576,	0.81536,	0.5544,	0.6457,	0.49588]
  
  - y_axis_lrp = [0.8429,	0.81582,	0.7745,	0.58476,	0.48346,	0.50312]

3 - Sparsity: Run Sparsity.ipynb (inside the folder Sparsity).

This program generates the graphs for Sparsity. Inside the program there are further instructions on how to use it.

For this program, you need copy and paste features scores from each IG, LRP, and Deeplift into the Sparsity.ipynb. You can get these values by running DNN_NSL_Example.ipynb and copying and paste the feature scores into the Sparsity.ipynb.

4 - Efficiency: For efficiency run DNN_NSL_Example.ipynb (inside the folder Base_programs), look for the cells that performs XAI methods, and take note of how long does it take to run it. Change the sample number to measure the efficiency when using less or more samples.

5 - Stability: This experiment is divided into Local and Global stability (inside the folder Stability). Run the DNN_NSL_Example.ipynb (inside the folder Base_programs) for both experiments as many times as you want to perform the stability experiment (I ran it three times). For Local Stability, set the sample size to a single sample, and for global use more than one sample (We used 2500). 

For each time you run, you need to copy and paste the top k features you want to analyze. In the case of NSL-KDD we only took the top 20 feature names. You need to copy and past the extract list into the stability_local_NSL.ipynb and stability_global_NSL.ipynb, respectively. 

6 - Completeness: Run DNN_DL_NSL_Compleness_Example.ipynb (inside the folder Completeness). This program is a standalone one that do not depend on DNN_NSL_Example.ipynb. The outcome is the Completeness graph.

7 - Robustness: Run RF_DL_NSL_bar_example.ipynb (inside the folder Robustness). This program is a standalone one that do not depend on DNN_NSL_Example.ipynb. The outcome is a single example of biased and adversarial explanation, and the ocurrence bar plots.


### Note

1) The programs were tested on linux. If using windows, you might run in the error: "UnicodeDecodeError: 'utf-8' codec can't decode byte 0x96 in position 22398: invalid start byte
", please refer to: https://github.com/ogarreche/Ensemble_Learning_2_Levels_IDS/issues/1 


2) FOR THE CICIDS dataset: I suggest going to the Thursday-WorkingHours-Morning-WebAttacks.pcap_ISCX.csv file and manually changing the following labels with the weird characters (you can do control+F and change all). The idea here is just to group the different labels into similar groups:
Web Attack � Sql Injection to Web Attack
Web Attack � Brute Force  to Web Attack
Web Attack � XSS to Web Attack
And do the same that have the  �.



3) Why am seeing sligthly different results for robustness? 
It could be due to different versions of the python packages, sometimes when a package is updated the way that it handles number can vary slightly causing slightly different results. In my opinion, this is not necessarily a bad thing since the results are still consistent.

4) Some of these programs take a long time to complete (over a few days).
