# ThesisNotebooks
This is all the notebooks related to my experiments

Master thesis of Yiming YAN. Experimental part.

Division:

## 1. Train the PC model(Colab):

### 1.1 preprocessing

This preprocessing is usually different between different models. And we need to put Urbansound8k dataset files at correct location in google drive to run the code.
Our **Spec2_Conv2** model: In SpecConv2.ipynb
The processed data is put at location: ` `"drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/specConv1/specSTFT/"+f"fold{i + 1}"+"/X.npy"
OR` "drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/specConv1/specSTFT/"+f"fold{i + 1}"+"/y.npy"`
The folder name us "specConv1" but we actually use 2-D convolution here, therefore we name our model Spec_Conv2

Our **MFCC_Conv2** model: In MFCCConv2D.ipynb
processed data is stored like this:
`"/content/drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/mfccConv2d/mfcc40x80/"+f"fold{i + 1}"+"/X.npy"`

For other models, the same way, their features inputs are put here:
**LhoestCNN** model: **Lhoest.ipynb**
`"drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/MelConv1/mel/"+f"fold{i + 1}"+"/X.npy"`
**TrivediCNN** model: The **same** input as Lhoest model:
`"drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/MelConv1/mel/"+f"fold{i + 1}"+"/X.npy"`
**HHCNN** model: use ` "drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/MelConv1/mel/"+f"fold{i + 1}"+"/X.npy"` , the **same** as LhoestCNN
**RajoCNN** model: In **MFCC_RajoCNN.ipynb**
`"drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/mfccConv2d/mfcc40x80/"+f"fold{i + 1}"+"/X.npy"`
**PiczakCNN** model:**PiczakCNN.ipynb**
`"drive/MyDrive/Thesis_Keras/TenFoldDataset/datasetnpy/PiczakCNN/mel/"+f"fold{i + 1}"+"/X.npy"`

### 1.2 model training

You will see the model summary, num of parameters and 10-fold validation results here.
Our **Spec2_Conv2** model: In **Spec_Conv2.ipynb**
Our **MFCC_Conv2** model: In **MFCCConv2.ipynb**
**TrivediCNN** model:**TrivediCNN.ipynb**
**LhoestCNN** model:**Lohest.ipynb**
**HHCNN** model: In **HH_CNN.ipynb**
**RajoCNN** model: **MFCC_RajoCNN.ipynb**
**PiczakCNN** model:**PiczakCNN.ipynb**

**If you still feel too troublesome to read my outputs, I have copied and recorded the results in .txt files.**
**I recorded them to calculate standard deviation and mean accuracy.**

## 2. Train the embedded model(Edge Impulse):

1. Upload your training data to Edge Impulse. You have to label them on your own. But first, please create a new project following the guidance of Edge Impulse.

2. Configure your model according to what is defined for PC model approaches.

3. Click "Start training" in "NN Classifier", after training, you can also get the **estimated peak RAM usage** here.

4. Click "Model Testing", you will find **test results** here. This is **accuracy for embedded**. Not possible to perform 10-fold validation because Edge Impulse currently do not have this function.

5. Click "Deployment", select the suitable device and generate code to deploy on the board.

## 3.Evaluation

### 3.1 Accuracy

PC model: See part 1.2
Embedded model:
In Edge Impulse Platform:
See line 4 in Part 2.

### 3.2 Time

PC model: All time evaluations are in TimeEval.ipynb
DSP Time: (Total time for 100 samples)/100
Classification time: Make predictions on each fold. Actually, each fold tend to have almost the same classification time.
Embedded model: After the model is deployed on the board (as shown in Part 4), it will show the time consumption when running classification process automatically.

### 3.3 RAM

Embedded model:
See line 3 in Part 2.
