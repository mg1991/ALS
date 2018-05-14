# ALS
Some things I want to try out regarding the Spark ml ALS-Implementation.


Point 1: "Normalization " 
  I think that by "normalising" the predicted scores in ALS one loses information.  
  Example: Costumer c has bought item i for x times, but ALS predicts a rating > x. If one normalizates the prediction one loses this information/ is forced to use a too broad "He has bought it, I won't show it again"-approach.

The error function is error(u,i)= ( 1+ alpha &ast; r(u,i) ) * (Indicator( r(u,i)>0 ) - x(u) &ast; y(i))

Case 1: r(u,i)=0 => error is x(u) &ast; y(i) => x(u) &ast; y(i) must be near 0

Case 2: r(u,i)>0 => 

                  * The first time is linear in r(u,i)
                  * so the higher the rating, the nearer x(u)*y(i) has to be to 1
                  
But why use the indicator function and not r(u,i)? If one would use r(u,i) then Case 1 would be the same and in Case 2 the predicted rating x(u) &ast; y(i) has to be near r(u,i).
  
 Point 2: Scoring of unknown customers via matrix multiplication  
  Let   
    * IF be the item-factor-matrix   
    * UF be the user-factor-matrix  
    * UI be the user-item-matrix  
 Then it seems to hold that UI'=UI &ast; IF &ast; FI, where UI' are the predictions. This approach works for customers unknow to the model while        training. 
