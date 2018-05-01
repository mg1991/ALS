# ALS
Some things I want to try out regarding the Spark ml ALS-Implementation.


Point 1: Normalization  
  I think that by normalising the predicted scores in ALS one loses information.  
  Example: Costumer c has bought item i for x times, but ALS predicts a rating > x. If one normalizates the prediction one loses this information/ is forced to use a too broad "He has bought it, I won't show it again"-approach.
  So I'll try to change the algorithm to not normalize and test it.
  
 Point 2: Scoring of unknown customers via matrix multiplication  
  Let   
    - IF be the item-factor-matrix   
    - UF be the user-factor-matrix  
    - UI be the user-item-matrix  
 Then it seems to hold that UI'=UI * IF * FI, where UI' are the predictions. This approach works for customers unknow to the model while        training. 
