# XAI_Whitebox
Whitebox methods


This work uses the following XAI methods:
 - DeepLift is applied by using Shap.deepExplainer. See reference: https://shap-lrjball.readthedocs.io/en/latest/generated/shap.DeepExplainer.html

- For LRP and IG. See Innvestigate: https://github.com/albermax/innvestigate


I uploaded tf23.yml if you want to used the same environemt as we used. 
Note: for importing environment see the Importing Environments section https://conda.io/projects/conda/en/latest/user-guide/cheatsheet.html 


### Example: 

1 - Run the DNN_NSL_Example.ipynb for instructions.

  The program Loads the NSL-KDD dataset, trains a DNN model, and apply IG, LRP and DeepLift. It outputs the Accuracy of the model and the most important lists for each one the XAI methods with its relative score.

2 - Descriptive Accuracy: Run descriptive_accuracy.ipynb

  This program generates the graphs for Descriptive Accuracy. There are further instructions in the program.
  
  As an example: 
  
  - The X axis is the features removed.
  
  - x_axis_nsl = [0, 5, 10, 20, 40, 80] 
  
  - The y axis is the accuracy when such features are removed. You can get these values by running DNN_NSL_Example.ipynb and copying and paste the accuracies into the  descriptive_accuracy.ipynb.
  
  - y_axis_deeplift = [0.8429,	0.78984,	0.5903,	0.690888,	0.56132,	0.5355]
  
  - y_axis_ig = [0.8429,	0.76576,	0.81536,	0.5544,	0.6457,	0.49588]
  
  - y_axis_lrp = [0.8429,	0.81582,	0.7745,	0.58476,	0.48346,	0.50312]

3 - Sparsity: Run Sparsity.ipynb

This program generates the graphs for Sparsity. Inside the program there are further instructions on how to use it.

For this program, you need copy and paste features scores from each IG, LRP, and Deeplift into the Sparsity.ipynb. You can get these values by running DNN_NSL_Example.ipynb and copying and paste the feature scores into the Sparsity.ipynb.

4 - Efficiency: For efficiency run DNN_NSL_Example.ipynb, look for the cells that performs XAI methods, and take note of how long does it take to run it. Change the sample number to measure the efficiency when using less or more samples.

5 - Stability: This experiment is divided into Local and Global stability. Run the DNN_NSL_Example.ipynb for both experiments as many times as you want to perform the stability experiment (I ran it three times). For Local Stability, set the sample size to a single sample, and for global use more than one sample (We used 2500). 

6 - Completeness: Run DNN_DL_NSL_Compleness_Example.ipynb. This program is a standalone one that do not depend on DNN_NSL_Example.ipynb. The outcome is the Completeness graph.

7 - Robustness: Run RF_DL_NSL_bar_example.ipynb. This program is a standalone one that do not depend on DNN_NSL_Example.ipynb. The outcome is a single example of biased and adversarial explanation, and the ocurrence bar plots.




