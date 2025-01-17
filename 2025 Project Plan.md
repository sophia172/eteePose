
# Brain Storming Agenda

- ## Objective 
	- Identify potential B2B projects involvement 
	- Generate ideas for R&D projects for 2025 with their potential business impact
	- Outline key tasks for selected R&D projects

- ## B2B projects overview (5 mins)
	- LINN
		![[Pasted image 20250110105822.png]]![[Pasted image 20250110105847.png]]
	- BabyArk
		![[Pasted image 20250110110634.png]]
	- MBTS
		![[Pasted image 20250110110948.png]]![[Pasted image 20250110111338.png]] 
	- WTNC
		![[Pasted image 20250110112211.png]]
	- FLO
		baby seat filler ![[Pasted image 20250110113110.png]]

- ## B2B involvement requirement (30 mins)
	- **List challenges or gaps (15 minutes)** in the current B2B projects or HW R&D projects
	- **Idea Generation (10 minutes):**
			- Group the challenges into themes and brainstorm project ideas for each.
			- Focus on ideas that are achievable within 2 weeks.
	- **Business value with AI input?(5 minutes)**
		- "How could this project strengthen client relationships or expand market share?"
		- "What is the estimated ROI for this project?"
		- "What competitive advantage could this bring to the company?"
	- **Check and Rank ideas (5 minutes)** based on feasibility, impact, and alignment with your team’s strengths.

- ## R&D Projects Ideation (80 mins)
	- **Existing R&D Projects (5 mins)**
		- eteePose
		- ChatBot
		- Insole
	- **Problem Identification (15 mins):**
		- List challenges or gaps in AI that align with TG0's expertise.
		    - "What unsolved problems in AI excite you?"
		    - "What recent research inspires potential applications?"
		- **Idea Generation (15 mins):**
			- Group the challenges into themes and brainstorm project ideas for each.
			- Focus on ideas that are achievable within a year..
		- **Feasibility check** and potential problems/risks (5 mins).
			- available AI models
			- required data
			- technical expertise
		- **Business value with AI input (5 mins)**?
			- "How could this project strengthen client relationships or expand market share?"
			- "What is the estimated reward for this project?"
			- "What competitive advantage could this bring to the company?"
		- **Action Plan and Next Steps (5 minutes)**
			- Prioritisation: Vote on the most promising R&D projects.
		- **Task Breakdown and Assignment (20 minutes):**
			- Pick 1–2 promising R&D ideas and list initial tasks for implementation.


# [Miro Discussion Board](https://miro.com/welcomeonboard/V2F6alpGKzJwc2RZeFJsZUtZWENMWjIvYWRIcFBhZmE3NitjTW5NNkVhR3BvNXJqTjNzcE8wVHY1NFVVSDRBNHNWd3pibTFtWHdCcENreFg5N0JDVzQvZkpNZy9ENlQ0VytrSU9HSlZDTE5wOXg1UWxNeEdPWTl5MmVabEVHcWIhZQ==?share_link_id=160366750856)
# Brain Storming Summary

## Identify AI challenges/problems 
These projects are categorised after exploring all thoughts. 
### Pose Estimation
- Better Reservior Computing Algs/Opt.
- Investigate distillation from large vision models to smaller low-compute models
- Constrains in human skeleton. Pretrained variable with skeleton
- Human pose simulation/control (Robotic control)
### Data Collection
- Data collection issues such (Setup and time management)
- Base station/Light house signal block for data collection
- Available Database

### B2B
Based on our current NPD projects (FLO, LINN, WTNC, MBTS and BabyArc), Explore potential application/ Challenges
- Individual signal to pressure /location mapping in each project --> Automatic force jig with MLP map
- Commercial Use case
- General model to do the pressure/location mapping
- Sign Language recognition on LINN, Sound
- BabyArk & Filo  not possible collect data from infants
- Guitar, ML songs
- Guitar, mark the song, How good they are syncing with the music.
- LINN Mood Light

### MCU implementation
- No models was done in MCU in TG0 so far.
- Tiny ML model performance in MCU

## Project Ideas and Exploration

From the previous identified challenges and problems, Think about a project. 

| Project Name      | Description                                                                                                                                                                                                                                                                                                            | Type    | Feasibility | Market Score | Market Value                                                                                               | Priority |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----------- | ------------ | ---------------------------------------------------------------------------------------------------------- | -------- |
| ReservoirPose     | Use Reservoir computing for Human Pose Estimation (HPE)                                                                                                                                                                                                                                                                | R&D     | 5           | 5            | unicorn in the market                                                                                      | 5        |
| Humanoid etee     | Create a model to do human pose generation                                                                                                                                                                                                                                                                             | R&D     | 5           | 5            | baseline in AI field                                                                                       | 5        |
| SimuPose          | Simulate pressure data to do HPE training                                                                                                                                                                                                                                                                              | R&D     | 4.5         | 3            | N/A                                                                                                        | 5        |
| BodyBase          | Use IMU, LightHouse to collect body data                                                                                                                                                                                                                                                                               | R&D     | 5           | 3            | N/A                                                                                                        | 5        |
| BodyBase-G        | Use IMU, LightHouse, Camera to collect body data                                                                                                                                                                                                                                                                       | R&D     | 3           | 1            | N/A                                                                                                        | N/A      |
| LINN-sign         | Sign Language recognition using LINN dial                                                                                                                                                                                                                                                                              | B2B     | 1.7         | N/A          | N/A                                                                                                        | N/A      |
| LINN-translator   | Use LINN to do language translation speaker                                                                                                                                                                                                                                                                            | B2B     | 4           | 5            | market needs/existing hardware/simple API calls                                                            | 3        |
| LINN-assistance   | Use LINN as chatbot                                                                                                                                                                                                                                                                                                    | B2B     | 3.3         | 3.3          | market needs/existing hardware/simple API calls but strong competition                                     | 3.5      |
| WTNC-Judge        | AI judge on WTNC guitar to score user performance                                                                                                                                                                                                                                                                      | B2B     | 2           | N/A          | N/A                                                                                                        | N/A      |
| WTNC-composer     | Use AI to generate a song from random input from user                                                                                                                                                                                                                                                                  | B2B     | 2.7         | N/A          | N/A                                                                                                        | N/A      |
| Signal Map        | Automate the sensor signal to pressure/location mapping with AI                                                                                                                                                                                                                                                        | B2B/R&D | 4           | 4.7          | internal needs/ faster project timeline                                                                    | 5        |
| LINN-gesture      | Gesture recognition using LINN, emoji detection                                                                                                                                                                                                                                                                        | B2B     | 3           | 4            | N/A                                                                                                        | 3        |
| LINN-Hub          | Use LINN as a smart Hub                                                                                                                                                                                                                                                                                                | B2B/R&D | 1.5         | N/A          | N/A                                                                                                        | N/A      |
| Golf-Insole       | Compare user pressure with Professional's pressure to see how close these behaviours are in Golf                                                                                                                                                                                                                       | R&D     | 3.6         | 4.6          | lots of value to customer, also could easily be subscription model,market needs/existing hardware/unicorn? | 4.5      |
| Power-Check       | Reduce the power consumption of AI model                                                                                                                                                                                                                                                                               | R&D     | 4           | 1            |                                                                                                            | 2        |
| Reservoir-MCU     | Add Reservoir computing to MCU                                                                                                                                                                                                                                                                                         | B2B/R&D | 4           | 1            |                                                                                                            | 3        |
| eteeBot           | etee AI customer Service using LLM                                                                                                                                                                                                                                                                                     | R&D     | 5           | 1.5          | reduce internal workload                                                                                   | 5        |
| Signal Map-Auto   | Use camera to do 3D object reconstruction and ML to decide how to carry the signal to force mapping process                                                                                                                                                                                                            | R&D     | 1           | N/A          | N/A                                                                                                        | N/A      |
| etee-sign         | Sign Language recognition and speak it out using etee Controller                                                                                                                                                                                                                                                       | R&D     | 2           | 5            | N/A                                                                                                        | N/A      |
| Tangible-Learning | - coach / professional trains ai device with their data to perform an act<br>- device can give feedback to a new user<br>- new user tries to repeat and 'act', and the ai can show them, using their imu + pressure data compared to the coach/proffesional data, in real time, how close they were to the coaches act | B2B/R&D | 2           | N/A          | N/A                                                                                                        | N/A      |



## Challenge they run into in the project. 

## what kind of application do you see TG0 works on
## Are they going to be related to AI.