# U.S.-Patent-Phrase-to-Phrase-Matching

https://www.kaggle.com/competitions/us-patent-phrase-to-phrase-matching/leaderboard  
We got 50th prize.  
This is summary and codes.

# Summary

## Data strategy
・4fold MultiLabelStratifiedKFold  

# Model
## microsoft/deberta-v3-large
・TransformerHead + multisampledropout  
・optimizer = AdamW  
・epoch = 5  
・scheduler = CosineAnnealingLR  

## anferico/bert-for-patents
・TransformerHead  
・optimizer = AdamW   
・epoch = 5    
・scheduler = CosineAnnealingLR  

## Yanhao/simcse-bert-for-patent  
・TransformerHead + Mixout  
・optimizer = AdamW  
・epoch = 5    
・scheduler = CosineAnnealingLR  

## prithivida/bert-for-patents-64d    
・LSTMHead + Mixout  
・optimizer = AdamW  
・epoch = 5    
・scheduler = CosineAnnealingLR  

## funnel-transformer/large   
・ConvolutionHead + Mixout  
・optimizer = AdamW  
・epoch = 5    
・scheduler = CosineAnnealingLR

## google/electra-large-discriminator    
・AttenthionHead 
・optimizer = AdamW  
・epoch = 5    
・scheduler = CosineAnnealingLR

## Weight optimazation 
I use weight optimazation to maximize cv.  
 cv = 0.853  
 lb = 0.860
 
## Stacking 
6models pred 
 cv = 0.854  
 lb = 0.863

## PostProcess
anchor=target': score =1.0  
contain 'ing': score == 1.0   

# Some Settings 

## Loss
SmoothBCEWithlogitsloss  

# Not Worked
・Loss function(FocalLoss/MSELoss)   
・cocolomlarge  
・Roberta-large  
・Ernie-en-2.0-Large  
・MLM  
・AWP
