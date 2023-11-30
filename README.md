# Snake AI


in this project we have 3 main stages 
	1 is the game with pygame which basically doesa loop and return the state of the game and according to that we should know the reward, if game over or not and the score
 	2 is the model with PyTourch whs is basically predicts the action that should be made according to the state we are in in this is where the ai will learn
  	3 is the agent which is basically the combination of both it knows the state of the game and forwords it to the model , first it does the training basically tryies to get a prediction from the model and makes it and gets the feedback from the game to know if it was bad or good and then retrun it to the agent





## REWARD ##
eat food 	+10
game over 	-10
else 		  0





## MOVEMENT ##
 1 [1,0,0]=>straight
 2 [0,1,0]=>rightturn
 3 [0,0,1]=>left turn
so now we dont run into the problem where the snake will turn 180 degrees in the same square and eat it self + it is only 3 action so less computational effort for the agent 




## STATES ##
[danger straight,danger right,danger left,				# the sate is an 11 value array the danger tells me where can i go so i can only go where the danger is 0
 direction left, direction right,direction up, direction down,		and the direcion is all zeros ecsept the the one where the head is moving 
 food left, food right, food up, food down]				and the food tells the model where the food is location again all of those are boolian nbrs so 0 or 1




 ## MODEL ##
neural network with the 11 state values as input and a hidden layer and the outup are 3 neurons which [ , , ] and those can be any nunber and the result will bacially be the max off them so [9,7,4] will bacially give me the movement of straight or [1,0,0] since 9 is max




## TRAINING ### DEEP (Q) LEARNING ##
   Q Value = Quality of action 

   0. init Q Value(init model)
   1. choose action (model.precict(state))		# Exploration vs Exploitation
				##(or random move)##		
   2. perform action
   3. measure reward
   4. update Q Value(+train model)

      

		## Loss ##### Bellman Equation ##### Mean Square Error ##
newQ(s,a) = Q(s,a) + A[R(s,a) + B*max(Q'(s',a')) - Q(s,a)] ====> Q    = model.predict(state0)=====>	loss = (Q-newQ)^2
													newQ = R + B.max(Q(state1))


where :	newQ(s,a) is the new Q value for thate sate and action
	Q(s,a) is ghe current Q value
	A is the learnig rate
	R(s,a) is the reward for taking that action at that state
	B is the discount rate
	max(Q'(s',a')) is the Maximum expected future reward given the new s' state and all possible action at the new state 






## to activate ##
anaconda   	cd ...				
		conda activate snake_env	# dont forget to pip install the important libraries (pytourch, numpy, matplotlip, pygame)
		code .
		python agent.py			#to run the ai	

  
##   ENJOY   ##
