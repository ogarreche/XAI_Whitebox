# XAI_Whitebox
Whitebox methods

DeepLift is applied by using Shap.deepExplainer. See reference: https://shap-lrjball.readthedocs.io/en/latest/generated/shap.DeepExplainer.html

For LRP and IG. See Innvestigate: https://github.com/albermax/innvestigate


Note: for importing environment see the Importing Environments section https://conda.io/projects/conda/en/latest/user-guide/cheatsheet.html 


### Example: 

1 - Run the DNN_NSL_Example.ipynb for instructions.

The program Loads the NSL-KDD dataset, trains a DNN model, and apply IG, LRP and DeepLift. It outputs the Accuracy of the model and the most important lists for each one the XAI methods with its relative score.

2 - Descriptive Accuracy: Run descriptive_accuracy.ipynb

This program generates the graphs for Descriptive Accuracy. 

As an example: 

The X axis is the features removed.

x_axis_nsl = [0, 5, 10, 20, 40, 80] 

The y axis is the accuracy when such features are removed. You can get this values by running DNN_NSL_Example.ipynb and copying and paste the accuracies into the  descriptive_accuracy.ipynb.

y_axis_deeplift = [0.8429,	0.78984,	0.5903,	0.690888,	0.56132,	0.5355]

y_axis_ig = [0.8429,	0.76576,	0.81536,	0.5544,	0.6457,	0.49588]

y_axis_lrp = [0.8429,	0.81582,	0.7745,	0.58476,	0.48346,	0.50312]

plt.clf()
