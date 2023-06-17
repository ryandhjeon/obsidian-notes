# KGAT: Knowledge Graph Attention Network for Recommendation
#### (2019) - Xiang Wang, Xiangnan He, Yixin Cao, Meng Liu, Tat-Seng Chua



<u>Training Pseudocode </u>

Set random seeds
Configure logging
Load data
Load pre-trained embeddings for user and item
Construct KGAT and move it to GPU
Initialize Adam optimizers
Initialize Metrics tracking
**for** $l=1$ to $numEpoch$ **do**
	Set training mode
	**for** $l=1$ to $numCFBatch$ **do** 
		Generate batch of CF data
		Compute CF loss
		**If** the loss is Nan, log 'error' and exit
		Backpropagate the loss && Update model parameters
		Log the progress every iteration interval
	**for** $l=1$ to $numKGBatch$ **do**
		Generate batch of KG data
		Compute KG loss
		**If** the loss is Nan, log 'error' and exit
		Backpropagate the loss && Update model parameters
		Log the progress every iteration interval
	**Update** attention mechanism 
	Log total training time for the $epoch$
	**If** epoch == $numEpoch$
		Compute CF metrics
		Log metrics
		Update the $bestRecall$ and check for early stopping
		Break the loop if model should stop
		Save the model for the best recall
	Save the metrics to a file
	Log the best CF
		

<u>Predict Pseudocode </u>

Determine GPU
Load Data
Construct the KGAT
Load the pre-trained model
Move the model to GPU
Parse the list of Ks from args
Evaluate the model for CF scores and metrics
Save the CF scores to a file
Print CF evaluation metrics
	

	