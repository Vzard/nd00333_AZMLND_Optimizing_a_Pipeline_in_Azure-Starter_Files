# Optimizing an ML Pipeline in Azure

## Overview

Two Azure ML paradigms are compared - Scikit vs AutoML based on accuracy. 
 
## Summary

Given features such as marital age,status,education level, etc  Predict whether a customer will be interested (y=1) or not y=0. y is the target/label. 
The best performing model was a AutoML VotingEnsemble algorithm (accuracy of 0.919 ) with validation_test = 0.2. Resule below. This compares with 0.916
at train data size = 0.2 for scikit learn model 

![image](https://user-images.githubusercontent.com/13240941/172673308-a7ed134c-b560-4411-adf6-847fadd095b1.png)

 ![image](https://user-images.githubusercontent.com/13240941/172680515-633fa7a6-ac32-4744-95d0-bed0a3f39069.png)


## Scikit-learn Pipeline

The Scikit pipeline in standard and intuitive

1. Create workspace
2. Set computing clusters
3. Parameter sampling policy
4. Set Termination policy
5. Setup scikit environment 
6. Set script config (where training algo is refered
7. Set Hyperdrive config
8. Run
9. Get Metrics

![image](https://user-images.githubusercontent.com/13240941/172682729-ef8fa58b-f523-4259-854c-e68ee261a2eb.png)

What are the benefits of the parameter sampler you chose?

Random parameter sampling is chosen since it is simple and a good start. It can handle discrete and continuous  sample spaces which suits
both C (continuous) and max iter(discrete)

Bandit Termination policy

Bandit policy is set with following inputs slack_factor = 0.1, delay_evaluation = 5, evaluation_interval = 1

## AutoML

1. Set the autoML config
2. validation test size =0.2 or 0.4
3. target label = y
4. Invoke the run
5. Get best model
6. Get model object (python)
7. use joblib to save model above

## Pipeline comparison
 
Using AutoML 
Accuracy with validation_data size =0.4 shows lesser than when
Validation_data_size = 0.2
2. Feature importance
Rank 4 and  5 of VS=0.4 becomes Rank 5 and 4 when VS=0.2

![image](https://user-images.githubusercontent.com/13240941/172682898-e5cd4320-cb10-446c-be28-8ea2c73bfeb4.png)

Hyperdrive  
Accuracy is lesser than AutoML (VS 0.4)
But accuracy with test size = 0.2 is more than accuracy with test size =0.4 (marginally)

![image](https://user-images.githubusercontent.com/13240941/172683193-83b30252-5af4-457a-87f3-55f8920d4f28.png)


1. Clearly train data size influences the accuracy. More experiments would have helped determine point of no return.
2. More experiments to be conducted to determine additional steps

## Future work
1. Employ pipeline calls to deploy. 
2. Save model, register and re-run 
3. Endpoint provisioning – elementary model as a service.
4. Hyperdrive runs with additional values in parameter space
5. Experiment with different sampling policies
6. And termination policy
7. Delve deeper into calibration metrics (for best AutoML model)

## Proof of cluster clean up
This is in code. 

![image](https://user-images.githubusercontent.com/13240941/172684071-32a1f5d2-8c1e-4ca1-8473-5d63982c4fea.png)

Remarks
![image](https://user-images.githubusercontent.com/13240941/172684337-e84052c3-7fe8-486b-bfe8-e86afc38619e.png)


