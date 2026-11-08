<h1>Excel-Net</h1>


## Demo Video - LinkedIn
<p align="center">
  <a href="https://lnkd.in/p/dkU2_Ub9">
    <img src="https://github.com/TomRea1/Excel-Net/blob/main/images/Thumbnail.png" alt="Excel-Net Demo - LinkedIn" width="800">
  </a>
</p>

## Overview

Excel-net is a tiny neural network built and trained exclusively in Excel. I recently started my job as a Data Scientist and I've been working on some projects with some pretty complex Power Query / Excel Formulas. I was blown away by how much you can do with Excel and it got me thinking about the fundamental operations required for neural networks. I decided I was going to give it a go and over the weekend I built out this xlsm. 

I would absolutely recommend playing around with this file / trying this project for yourself both to dive into the machine learning fundamentals and improve your Excel skills !  

---

## Key Features

- Formula driven forward and backward passes
- VBA based training
- VBA based network animations, loss logging and decision boundary logging
- Loss, ReLU and Decision Boundary Visualisations

---

## Architecture

Describe the overall architecture.

### Network Structure

```text
Input Layer (x1, x2)
    ↓
Hidden Layer (3 hidden neurons) 
    ↓
Output Layer (1 output - sigmoid)
```


## Training

Because the forward/backward passes are all dynamically calculated by the formulas, all that needs to be done to train the model is get VBA to iteratively fill in the x1, x2 values. I used the Fischer-Yates algorithm to cycle through the 4 combinations in the training data to try and recreate SGD. The model was trained on the XOR dataset. 

I chose this dataset because its not linearly separable - a linear regression model physically can't draw a decision boundary between the two classes. This network was a suitable architecture because it introduces the non-linearity required using ReLUs in the hidden layer. Three hidden neurons actually turned out to be overkill for this problem and the network often learns to only use two neurons to converge. 

I implemented Leaky ReLU to avoid dead neurons during the process of trying to make the model converge reliably. I found this combined with a weight initialisation of =RAND()*1-0.35 and a lr of 0.1 to be best.

## Running the Model 

```
1 Once downloaded, make sure your Excel file is macro enabled to begin. 

2 Delete the values in the 'Weights' column and replace them with your initial weights for training.

3 Do the same for the bias terms.

4 Once you're ready and you have your weights and biases initialised - press 'Train Model' to run. I would recommend setting them to =RAND()*1-0.3 ish. Copy that formula down for all of the weights and biases to initialise and then select all, CTRL C, CTRL SHIFT V on all values to copy and then paste their raw values. Make sure not to leave these cells formula populated or the weights will just always be random and the network can't learn.

```

If the network doesn't converge for you it is likely the weight initialisation. Due to the network's size, it can be quite sensitive to these starting weights. I would just reinitialise and run again, perhaps increase the epochs if you want to give it a chance to learn a more complex solution.


