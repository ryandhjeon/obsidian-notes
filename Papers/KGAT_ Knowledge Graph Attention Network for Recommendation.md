# KGAT: Knowledge Graph Attention Network for Recommendation
#### (2019) - Xiang Wang, Xiangnan He, Yixin Cao, Meng Liu, Tat-Seng Chua



<u>Pseudocode </u>

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
		
		
	
	

	