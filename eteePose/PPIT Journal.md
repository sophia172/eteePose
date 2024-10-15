[[PPIT mindmap.canvas|PPIT mindmap]]

# Q: hip rotation angle is wrong 
A: mainly x-axis big jumps in plot, line385 r2[0] --> frame_rotations["hips"][0] --> kpts["hips_angles"] --> still comes from root get_hips_position_and_rotation --> root rotation thetaz-->root_v --> frame_pos[root_define_joints[1]][0], --> neck x axis jump -->thetaz and thetay

When vector is close to one axis would cause the detected angle varies a lot. I just need to change the angle calculation sequence from Decompose_R_ZXY to Decompose_R_ZYX



# Start with keypoints

## Two keypoints

### Questions
- I need to check whether the error for two keypoints are big or not.  Then, I need to test whether adding time information would help the key points performance. 
- It is important to add drop out. And I forgot about it. 

	**Analysis**
	1. Result shows that adding time series input improved the loss for validation set dramatically. The longer the time series is, the more accurate train set error gets, validation error seems stable with time series.
	2. Drop out brings the train and val loss closer for this small dataset.
	3. The **drop out** performance is even better than adding the time series. 
	4. Use 5 frames as it gives the best result so far


- **Q**: I need to tune the train and validation set loss to equal. 
		![[PPIT To-Do List#^6fcaaf]]
		**Analysis P12-P14** in [slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2521eccb78d_0_36>), data saved in [folder](<https://drive.google.com/drive/folders/1yIC4jxyCNfRQR9kgt5zrASi1d0WQlyeH?usp=share_link>)
		1.  Weight decay makes a difference, 0.003 is the best
		2. drop out seemed improving the performance with 0.2, but not obvious difference between 0.2, 0.3 and 0.4.
		3. reduce model size improved the performance dramatically! Removing Decoder and some of encoder helps
		4. change to 10 time frame helps
		5. restrict training data helps a little but not much
 ^f66237

- **Q**: bidirectional RNN style for CNN. The output does not have to be the last time stamp, it can be the time stamp in the middle.
		![[PPIT To-Do List#^793701]]
		**Analysis**
	1. It helps the validation a bit. not dramatically but observable
	2. It doesnot help with the train set error. So I do not think we need 10 time-frames
- **Q**: I am currently using the full trial data for model training. What if I use only the lower body data?
		![[PPIT To-Do List#^07e376]]
		**Analysis**
	1. restrict training data helps the validation a little but not much.
	2. It does not help with the training set error

- **Task**: Combine the analysed parameters together.
	- 

- **Q** : Is that going to make a difference if I use electrode data?
		![[PPIT To-Do List#^d79b3f]]
		**Analysis** ^7447ca
		When loss is 0.7, the keypoints fits GroundTruth very well.

## Six key points

^019bd3

### Same CNN as optimised 2 key points
![[PPIT To-Do List#^9fdfcf]]
**Analysis**
- Behaviour is much worse than 2 key points. It might be because I accidently changed the training data split

### Change structure to optimise 6 key points
![[PPIT To-Do List#^5683c2]]
**Analysis**
- Fully_connection_1 increased the parameters dramatically from 500k to 50m
- Fully_connection_2 kept the parameters roughly the same from 500k to 623k
### - The link is much smaller than reality when link range is right


## Lower body key points


# Turn dynamic tensor to static, will it affect inference? 
[[PPIT To-Do List#PPIT 2023-10-08|link]],[P26slide](https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2880ba37b5c_0_5),
If i define my batch size to be 32, but in reality i only need to predict 1 frame, Is that going to be a problem?
**Answer:** 
1. It actually affected the prediction. So the batch size need to be aligned. 
2. In real life, the prediction is one by one, So i can train a model first, use their weights. load it to the new model and assign the batch to be 1.

## Integer Quantization problems 
[[PPIT To-Do List#PPIT 2023-10-08|link]], [P26slide](https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2880ba37b5c_0_5),
The integer quantization requires two part to be quantized, first is integer the weight, the second is to quantize the variable data (such as model input/output and intermediates between layers)
**Problem:**
1. You need to provide either a dictionary with input names and values, a tuple with signature key and a dictionary with input names and values, or an array with input values in the order of input tensors of the graph in the representative_dataset function. Unsupported value from datase






# Jun2023 collected data processing

1. I need to extract the data which can be used to train for foot only. That is set 1, Th gesture E, F in set 2.
2. I also need the data to train for low body, that is set 1, the gesture E in set 2 and set 3. 
3. To find out whether I need to collect more data, I need to plot a curve showing the error/train size.
![[PPIT To-Do List#^9b2b06]]

## MIT transformed architecture 
[script](<https://colab.research.google.com/drive/1P6-DJ_ny4Y2Ec9mQIJVZ9qzXqLuCTcXn#scrollTo=48kW1c2F5l1R>)



