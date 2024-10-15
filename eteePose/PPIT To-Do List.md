
[[PPIT mindmap.canvas|back to mindmap]]

[[PPIT Journal|Thought]]

## High priority
## Build CMT model
- [ ] Run CMT model with random data of the original size
- [ ] Run CMT model with random data of 13x24 size
- [ ] Run CMT model to generate data of 16x3
## PPIT 20240226
- [ ] Build CMT for joint angle
- [ ] Joint angle transformation [P28 script](<https://colab.research.google.com/drive/1svjEOd__8lIp3Cg1VhbnvcWSI-eEga3G#scrollTo=LqF6qrKgcWVV>)
### PPIT 2023-10-27
- [ ] change loss weight, [P28 script](https://colab.research.google.com/drive/1svjEOd__8lIp3Cg1VhbnvcWSI-eEga3G), [model_folder](https://drive.google.com/drive/folders/1STW2cjwIZGQjvMQJVy-BdmgyH3akl6wX)
### PPIT 2023-10-08
- [x] Change tensor to static [[PPIT Journal#Turn dynamic tensor to static, will it affect inference? PPIT To-Do List PPIT 2023-10-08|link]], [P26slide](https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2880ba37b5c_0_5), [data](https://drive.google.com/drive/folders/1CwikGRaKbSFFfZedrt2IZQx1Zie-XwLr)
- [x] change model to integer [[PPIT Journal#Integer Quantization problems|link]]
- [x] Use 2023-06 data for the model and remove Conv3D, [script](https://colab.research.google.com/drive/1lF5i3hp0tCt720EaATkZrxa_lh7SJpWo)

### Before 2023-10-08
- [x] Two keypoints structure [[PPIT Journal#Analysis|Analysis]]
		[visualisation script]  ^0cf778
	 - [x] check how far is 0.015 out of 32767,  about 3cm ^33c2b0
	- [x] Check result from P2 [html animation](<https://drive.google.com/file/d/17bCdELoaWgQav6FSkMIs5Z48XlIWE80W/view?usp=share_link>) ^260c7b
		- [x] Run the model again  [script](<https://colab.research.google.com/drive/1PnQCkgvPAa3tqBId69HA0guWafi2H7UV#scrollTo=MrRjC-Y-J0S4>)
		- [x] Need to save the original dataset.
		- [x] Plot predicted result and original dataset together 
	- [x] change input data to time series data 5 frames (analysis [P9](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g253cfbec774_0_0>)  , script [here](<https://colab.research.google.com/drive/1PnQCkgvPAa3tqBId69HA0guWafi2H7UV#scrollTo=HAA0O_g92Ef0>))   and check result
	- [x] change input data to time series data 10 frames (analysis [P11](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2542b364a73_0_10>)  , script [here](<https://colab.research.google.com/drive/1FFM0KJ20_Fkd8ToWMqAjqeWeyhTHn91h#scrollTo=Tum08jgLL49_>))  and check result 
	- [x] Would adding dropout help? (analysis in [P10](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2542b364a73_0_0>), script [here](<https://colab.research.google.com/drive/1hJr0s7OCj5ytdII7SKtmW5xW6CPtU6Un#scrollTo=jBzD7t8nX-Vq>) and check result. 
	- [x] Change the pressure map input to electrode signal input [P19 script](<https://colab.research.google.com/drive/1-CjhJjo_GvrQHfQwuE6fmCDO9I3fkY9x>), [P19 Result Slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g25744cf9cd7_0_8>), [P19 datafolder](<https://drive.google.com/drive/folders/1HXevsEb1wfwjgE4qP4JbZ8w8aGo614ic>), [[PPIT Journal#^7447ca|Thought analysis]]  ^d79b3f
	    - [x] Compare the two epoch in P19 to see the difference in visualisation. 
	- [x] Tune model to make train error is similar to validation error.  **Analysis P12-P14** in [slide](https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2521eccb78d_0_36),  [[PPIT Journal#^f66237|thought analysis]] ,data saved in [folder](https://drive.google.com/drive/folders/1yIC4jxyCNfRQR9kgt5zrASi1d0WQlyeH?usp=share_link)^6fcaaf
		- [x] reduce model size (5 time frame + dropout0.2) [P14script](<https://colab.research.google.com/drive/1y0N7MJEsdfrx15o7QMc3kFh-AL1iUtkM#scrollTo=IfQ3xP6-EY5r>).   
		- [x] adjust drop out [P12script](<https://colab.research.google.com/drive/14uLYgi9PS9uYRoxbj78yNbTOkZbrAToz#scrollTo=wGmqSv4SXrAc>)  
		- [x] add weight decay coefficients [P13script](<https://colab.research.google.com/drive/1kPRqY0J2WRpyeJN9XcHmbLwtAHOrNGOp#scrollTo=jBzD7t8nX-Vq>)  
		- [x] turn learning rate (for train set only)
		- [x] Combine all optimised parameters together  [script](<https://colab.research.google.com/drive/14XAwxSQi48ZSd7lO_BZGfpbRUl9sjLs_#scrollTo=wGmqSv4SXrAc>), [result in slide P17](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g256fdb30443_0_0>) , [data in folder](<https://drive.google.com/drive/folders/1SplY8GLzECioJZiEesX7AvthzopCZ3Yu>) 
	
	- [x] Separate trial data to feet only, lower body only and full body data. [script](<https://colab.research.google.com/drive/1-XUJmRn2Pnp5OgVeeGM52cAEFJK-s-nt#scrollTo=PWlbrkMCx-W->), [result in slide P16](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g256fdb30443_0_0>) , [data in folder](<https://drive.google.com/drive/folders/1xzI2CMYFTonebNwICMfFReUw3mFQcaKd>) ^07e376
		- [x] data processing
		- [x] train two keypoints again with these data.  
		- [x] visualisation

	- [x] Change time frame duration to 10 frames, with 7 at front and 3 at back, [P15 script](<https://colab.research.google.com/drive/1AZyDUDfAZ9B-P8lvH61deTgSyYRpsqTZ#scrollTo=HAA0O_g92Ef0>), [result in slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g256565c577e_0_21>), [data in folder](<https://drive.google.com/drive/folders/1uxh1Igdk_rffDikYvOd8xSoAcuLfcUDd>) ^793701
		- [x] data processing
		- [x] training
		- [x] visualisaton
- [ ] Jun2023 data processing [script](<https://colab.research.google.com/drive/1HBU3YVPgarjv0ktWh7Ltm-NK7CVYb4Vm>) and [source code](<https://drive.google.com/drive/folders/12kM3iV7f_cnoftfnRqRqZMDYx04ShjXM?usp=share_link>) ^9b2b06
	- [x] exclude missing data
	- [ ] extract the lower body input/output only
	- [ ] extract the feet input/output only
	- [ ] Add train set file by file to test whether i need to collect more data

- [x] 6 Key point structure (two feet) [[PPIT Journal#Six key points|Journal]]^1477a2
	- [x] Analyse the link distance and fix the shape of feet
	- [x] Use the similar structure with the best performed architecture in two key points [script](<https://colab.research.google.com/drive/1O26nSsQ5Wko7AxJWh8164NYc81WZq5NV#scrollTo=HAA0O_g92Ef0>), [slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g2589e8c670b_0_0>), [data](<https://drive.google.com/drive/folders/1BNm0uHEYW7CT_yFzGp-95uhIYRM_A236>) ^9fdfcf
	- [x] CNN structure optimisation. [P22script](<https://colab.research.google.com/drive/113WtUYZFzZy_Xt3MqMFSG3xIe_k2nPtC#scrollTo=MrRjC-Y-J0S4>) , [data](<https://drive.google.com/drive/folders/1bNBdkD_ub7SpDvXqIqyTOQfvGxPyeOF4>) , [slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g258fef92d0a_0_1>) [[PPIT Journal#Change structure to optimise 6 key points|Journal]]  ^5683c2
		- [x] Try full connection 
		- [x] change the shape output from (6,3, 1) to (3,6,1)
		- [x] change the shape output from (6,3, 1) to (1,3,6) 
		- [x] add more drop out 
		- [x] add pooling 
		- [x] small batch 
	- [x] Add link loss [P23script](https://colab.research.google.com/drive/1-yvvYZ3T0VxXvNwa7OIQs-yOezeHRCKS#scrollTo=0lWaUokvM2Pr), [P23GDrive](<https://drive.google.com/drive/folders/1DBl3DtHgNNKucWz94hYc7zbfe14yWWs7>)[[PPIT Journal|Journal]],  [slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g258fef92d0a_0_1>)

	- [x] Decide whether to add time series data based on  two key points analysis
- [x] 10 key point structure (lower body) [P24 script](<https://colab.research.google.com/drive/1owVtk2ahCw8NU1dLdayN4fFs7YnmZsP9#scrollTo=4N79EDAUjMXb>) ^b87de7
	- [x] Use same script as P23 but with only coordinate loss
	- [x]  Use same script as P23 but with only coordinate loss (full body)
- [x] Upper body [P25 script](https://colab.research.google.com/drive/1owVtk2ahCw8NU1dLdayN4fFs7YnmZsP9#scrollTo=not7NcI9si7q) [slide](<https://docs.google.com/presentation/d/1pY_B6-Ig_KGZVJCBx-IUggb7qSOtSjwMobfi9VyP33Q/edit#slide=id.g258fef92d0a_0_1>)
	- [x] change learning rate to lower to see if we can solve the NaN loss problem
## Medium priority



## Low priority
