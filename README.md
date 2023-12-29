# Multi-label-classifier-project
## Dataset:

Site: https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/

Dataset name: "Amazon Fashion" (5-core) and one part of "Clothing, Shoes and Jewelry" (5-core) dataset

Raw data look like this:

{
"image": ["https://images-na.ssl-images-amazon.com/images/I/71eG75FTJJL._SY88.jpg"], 
"overall": 5.0, 
"vote": "2", 
"verified": True, 
"reviewTime": "01 1, 2018", 
"reviewerID": "AUI6WTTT0QZYS", 
"asin": "5120053084", 
"style": {
	"Size:": "Large", 
	"Color:": "Charcoal"
	}, 
"reviewerName": "Abbey", 
"reviewText": "I now have 4 of the 5 available colors of this shirt... ", 
"summary": "Comfy, flattering, discreet--highly recommended!", 
"unixReviewTime": 1514764800
}

But I only take "reviewText" to label and train model
### Labels
11 labels:
- Good product
- Poor product	
- High-quality materials	
- Low-quality materials	
- Worth the price	
- Overpriced	
- Attractive appearance	
- Unattractive appearance	
- Correct size/fit	
- Too small	
- Too large
## Active learning loop

Step 1: First use the labeled data to train


### Model: Bert + fine-tuning

Step 2: Predict on new dataset, unlabeled data and get confident score

Step 3: If confident score more than 80%, integrate to the dataset. If lower, manually labeled it

Step 4: Re-train model on new dataset.

Step 5: repeat from step 2

## Compare model result:
With new, larger dataset, train on 3 different model-based:
- MLP-based model ![mlp_architecture json](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/48b556dd-891b-46bc-8feb-7d54e44184a3)

- LSTM-based model ![lstm_architecture json](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/f5a4b184-c730-49fd-aca1-42a112e29aa2)

- Bert + finetuning model ![4-Figure2-1](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/7a07a25b-5fcd-4d16-822c-e0a28ebfcbce)


### Result:
- MLP: ![image](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/35697ec5-ac86-445a-8528-15b9b9d77cbb)
- LSTM: ![image](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/8143a353-185c-46a3-a53a-2d2f4aa07c35)
- Bert+fine_tuning: ![image](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/8bb470a0-b10a-48a3-b081-d46fb4cdcfcd)

Dicussion:
- Consider result of Bert+fine_tuning when preparing dataset: ![image](https://github.com/somerandomguy-coder/Multi-label-classifier-project/assets/153010587/917eec25-21e0-4e2f-abd0-5bcc6f0614f3)
This could be due to the not well-prepared dataset using active learning method

- One more thing is that the MLP model have a remarkable result compared to LSTM model . This may be because of Neural Network work well on the token-level more than LSTM and done well in this specific problem 

