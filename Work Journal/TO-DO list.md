
---
# 2024
## Task
1. Find a new job
2. At least three new posts/notes every week
3. Finish two big event within WCC. 

[[Benefit Log]]

Today’s TODO list

```dataviewjs
function callout(text, type) {
    const allText = `> [!${type}]\n` + text;
    const lines = allText.split('\n');
    return lines.join('\n> ') + '\n'
}

const query = `
filter by function !task.file.path.includes('Work Plan')
filter by function !task.file.path.includes('TO-DO list')
filter by function task.status.type === 'IN_PROGRESS';
path includes ${dv.current().file.folder}
`;

dv.paragraph(callout('```tasks\n' + query + '\n```', 'in progress'));
```
```dataviewjs
function callout(text, type) {
    const allText = `> [!${type}]\n` + text;
    const lines = allText.split('\n');
    return lines.join('\n> ') + '\n'
}

const query = `
group by tags
filter by function !task.file.path.includes('Work Plan')
filter by function !task.file.path.includes('TO-DO list')
filter by function task.status.type === 'TODO';
path includes ${dv.current().file.folder}
`;

dv.paragraph(callout('```tasks\n' + query + '\n```', 'To do'));
```

```dataviewjs
function callout(text, type) {
    const allText = `> [!${type}]\n` + text;
    const lines = allText.split('\n');
    return lines.join('\n> ') + '\n'
}

const query = `

done after 21 days ago
group by tags
filter by function !task.file.path.includes('Work Plan')
filter by function task.status.type === 'DONE';
path includes ${dv.current().file.folder}
`;

dv.paragraph(callout('```tasks\n' + query + '\n```', 'Done'));
```
```dataviewjs
function callout(text, type) {
    const allText = `> [!${type}]\n` + text;
    const lines = allText.split('\n');
    return lines.join('\n> ') + '\n'
}

const query = `

filter by function !task.file.path.includes('Work Plan')
filter by function task.status.type === 'NON_TASK';
path includes ${dv.current().file.folder}
`;

dv.paragraph(callout('```tasks\n' + query + '\n```', 'Paused'));
```
- [[2024-05-19]]
- [[2024-05-16]]
- [[2024-05-15]]
- [[2024-05-14]]
- [[2024-05-13]]


## 2024-04-28
- [x] Prepare some document to send to university of sheffield
- [ ] Add fine tuning func to e2e
## 2024-04-22
- [x] Debug for GPU NaN problem
- [x] Read SelfSupervisedL paper
## 2024-04-15
- [ ] partition for PPIT data
- [x] Read deep learn finish chapter 9
- [x] End2end ML project writing 
- [x] Sort out GPU *afternoon*
- [x] Set up autodownload for VM *afternoon*
- [x] check PPIT model running on PC to tweak code 
- [x] Read 1-bit
- [x] Umat discuss objective and send email 
![[Error Corrector To-Do List#Error corrector on regression]]
- [ ] Rebuilt seamless 

**Q**: How to locate working directory from a sub directory script


## 2024-04-08
- [x] Onboarding 
- [x] memorise the management module
- rehabilitaion. with hospital.possible grant application. I 
- they can manufacture the material for in loughborough university. 



## 2024-04-03
- [x] 3-year plan for ML project in TG0
	- scope
	- timelines
	- deliverables
	- Milestone
	- key risk
- [ ] end-to-end ML project setup
- [x] Daemon mat setup with new model 
	- Need to check the hardware
	- Base model ready
- [x] Intern's project plan
	- Talk with Harvey about his etee tracker setup.
	- etee tracker (one tracker connect to one dongle) use steam firmware and we can not add it.
	- BLE location resolution is 30 cm 
	- RSSI location is < 10 m
- Need to think about how to log ML architecture each time I run the training process. 
## 2024-03-28

1. read paper, write summary
2. figure out how to run VM in the background
3. write the end2end ML project
## 2024-03-25

**Paper note**: Find the error bound of the corrector. This is a way to measure the stability of the legacy AI system. 



## 2024-03-22 TODO list
- [x] Figure out the Vertex AI problem
	1. Change the template colab file to test script
	2. Run code again in Vertex AI UI
- [x] Write and clean a document about Vertex AI set up

## 2024-03-08 week TODO list
- [x] Create model for angle prediction


## 2024-2-26 week TODO list
	9:30 -- 11:00 Read paper, write one summary
	11:00 - 13: 00 PPIT model
	15:00 -- 17:00 Paper change and submit
- [ ] Prepare a document to explain the work required for AIDOG 
- [ ] PPIT model
	- [ ] build inception and diffusion model
	- [ ] build LSTM
- [ ] Check how Sora works and how to use it (Wednesday share)
- [ ] Check embeded AI
- [x] Change paper to submit to another journal
	- [ ] add more photos about hte hardware set up
	- [ ] we do not need muscle sensor, cite other's paper. 
	- [ ] 
## 2024-02-19 week TODO list
- [x] PPIT model
- [x] Two meetings 
- [x] R&D report
- [ ] read a paper and write summary
- [x] QMUL: change loss to mean squared error.
- [x] QMUL: pnlot showing different fits in parallel fitting, mean and variance.
- [x] QMUL: details of B-spline, show where the knots are in plot.
- [x] QMUL: add residuals in the exafs fit and sum fit.
I have added some details to the R&D report regarding the AI enhancement part of the mat. 
Regarding the questions:
1. The video demos of the PPIT model is in this folder. Files are in HTML format and cna be opened through safari/chrome. The result is not very accuracy --> at least not at demo level. 
   2. The algorithm is currently running at the speed of less than 100 ms for one time frame, meaning 10 Hz. The measurable accuracy is calculated as +- 10 cm for each joint in each axis (x,y,z). 
   3. My opinion is working on the model development side in the next 1 month with the new MoCap data from Kingston University. Nothing needs to be changed on the hardware sensor side. The ML work requires consistent Hardware. The evolving version of the hardware requires ML work to start another iteration from data collection which is time consuming. 
   4. If we are to implement the same thinking on insoles, with the input of Gyro. It requires us to do another round of data collection.  The data collecton needs
      - at least 8 etee tracker;
      - 3 light house;
      - outdoor setup for data collection.
      The insole will support only standing up posture. There is no evidence to show that we can achieve a posture of bending knees. This needs to be verified after the PPIT model with more data. 
      Models and software need to be redesigned to fit the insole pressure and gyro data.
   5. KU is currently working on the paper, planned to be submitted to ECCV. The draft is 80% done. The deadline for the submission is 7th March. 



- [x] Panel question. FT event workflow 
- [x] Meetup registration. Ask members to fill in another google form. 
## 2024-02-12 week TODO list
- [x] change xas code to include selection of Axis
- [x] read the lower bound paper and add the content in paper, add lower bound information.
- [x] Check on deep stream grant application

## 2024-02-04 week TODO list 
- [x] Paper highlights 
- [x] Paper introduction 
- [x] Publish ft event speaker
- [ ] Look through bound paper
- [x] Swift panel prepares 
- [ ] PPIT model
- [x] Ming wants grant ideas
- [x] Ming sent a email. Grant draft. Need to look through it
- [x] PPIT data process
- [x] Chase up email to insta deep 
- [x] Announce the ft event
- [x] Announce FT event on LinkedIn. Feel Julia to publish it on Twitter and Instagram 
	The importance of the problem need to be addressed in the whole paper. I need to present it as the most important problem in 
	### CFDX
	1. Project outsider.
	2.sample from the lab are going to be the data
	1. research team in house in cfdx. fair and facebook
	2. 2 persons , 7 person in total s, preseed round, 2 grants, advance precision medicine, blood bio mark, biomark, 2 years runwasy
		
## 2024-01-22 week TODO list
- [x] Encrypt evaluate property 
- [x] paper
- [x] LinkedIn msg
- [x] Read a chapter of book. Write summary 
- [x] Put Ling in contact with Ming. 
- [ ] Wrap XAS code to one software
- [ ] Change spline to Bspline
- [x] Email Ling Xiao

entry to barrier
market size and secondary market size, feature
risk management

it's a bit risky

Virtual Reality based Mirror Threapy for Storke Reabilitation. TG0 worked with University of South Wales and Hobbs Rehabilitation, wining the Medtech Navagator Grant.   
2. VR based Social Anxiety. TG0 has worked with BU on a three year PhD project  
3. PPIT, AI-based body movement analysis

## 2024-01-15 week TODO list
- [x] go through KTP Funding
- [x] Write summary about the paper
- [x] Monday night: clean code, add energy shift, look through papers. 
- [x] Go through the slide once
- [x] Funding pitch to company
- [x] STM32 simulated board
- [x] Prepare FT event documents
- [ ] Encrypt evaluate property 
- [x] paper

digital is a new department. coporate department. work for key global account. komitomo. 900 companies glaobly. 
The maturlity of different companies. built. 

start to build data team. 25 memebers last year around consulting/marketing/customer experience. pM function? delivery team and consulting team are separately. 

How many people (10 + 3 (business analysis/marketing consultant)) in the current consulting firm? How many people in the delivery team (15 3+2 data+2 data + 3-4 projects ) looking for a (1 marketing related project PM, 2-3 data engineer. ). web 


the work might work on connecting to LLM. Our data scientist. Looking into the current trends, different sectors so we are the first person to know about it and tell everyone about the function. 
delivery team 

tension from senior management team.

Check the future career of an AI consultant 
STM32 test



## 2024-01-08 week TODO list 
- [x] data chase up and preprocessing for Kingston
- [x] Modify my cv and submit for two jobs 
- [x] Read paper and write summary
- [x] Prepare interview slide
- [ ] look for grant opportunity
- [x] PPIT paper monitoring
- [x] LMC0
- 
## 2024-01-02 week TODO list 
- [x] 10:00-11:00 note on one book chapter Deep learning 20-1 and publish on yingliu.site and Linkedin
- [x] 11:00 - 12:00 write summary about a chapter in 
- [x] Return Dimitri’s email about funding opportunities. 
- [x] 21:00 - 22:00 paper figures
- [ ] ask James with correct data file, preprocess data
- [x] application to hugging face
- [x] gym
- [ ] violin practice if neighbour is not home 
- [ ] 

# 2023
## 2023-12-18 week TODO list
- [x] email to  FT asking about event plan 10:00-10:30
- [ ] Write an post about xx 10:30 - 12:00
- [ ] Change cv 12:00-1:00
- [ ] Write cover letter 12:00-1:00
- [ ] Apply for one job 
- [ ] 
- [x]  Reply all emails 10:00 - 10:30
- [x] Read the paper about Pfam dataset
- [x] write about Pfam dataset 10:0-11:00
- [x] Write error corrector paper 11:00-1:00
- [x] Write protein script instruction 
- [x]  Read the protein questions again and write down a plan 11:30 - 12:00
	- [x] check if i can reduce dataset by alignment
	- [x] Check if one family has similar domian alignment, take 10 as example
	- [x] missing data, outlier? check from pca outlier

	- Explain the method I used 
	- a set of experiment to prove the method works
	- result and analysis 
- [ ] Work as planed with protein questions 12:00 - 
## 2023-12-13 week TODO list
- [x] Write a summary about UniRep. 
- [x] Error corrector paper 2:00pm - 4:30
- [x] Write a section about transformer Finish by 12:30
- [x] Lunch from 12:30 to 1:00 pm
- [x] Pilar send WWCode info 10:00
- [x] GitHub info upload data 10:30 11:00
- [x] Call visa 10:00
- [x] Contact instadeep 10:00
- [x] Write a chapter about Pfam 11:00-12:30
- [x] Write a plan for protein classification 12:30-1300
- [ ] Write error corrector paper with algorithm for centroid classifier. 
- [x] Work on protein classification task. Normalise data. PCA of feature to view it? T-SNE to view it? 
## 2023-12-04 week TODO list

- [x] Write PPIT Final report
- [x] Write a chapter about the protein review paper
- [x] Prep for two PPIT meeting. Write agenda
- [x] Write a summary about segmentation of protein sequence
- [x] Finish up the final report 


- [x] Send Kingston an email to chase after data and paper
- [x] Write a paragraph to describe what is  attention
- [x] Apply for one job
- [x] Ebay sold item check 
- [x] AirPod fix
- [x] WriteASummary about using RNN in NLP
- [x] make a slideFor PRITFinal report
## 2023-11-27 week TODO list
- [x] Write Financial Times the email 
- [x] Advertise the WWCode event on LinkedIn
- [x] Write my bio
- [x] Write mini-KTP application
- [x] Make a WWCode talk poster
- [ ] 

## 2023-11-20 week TO DO list


 - [x] Figure out PPIT UI running
 - [x] add model inference in UI
 - [x] submit a CV to apple
 - [x] submit a CV to playstation
 - [x] write an email to thank Debra
 - [ ] Publish WWCode Sahana’s talk event. 
 - [ ] Reply bhara’s email from Kingston 
 - [x] Test PPIT UI on Mat. Retrain model and add to both UI and STM 32, can I use quantised model on python. Is it faster?
 - [ ] Write mini-KTP application
 - [ ] Write PPIT final report
 - [ ] write error corrector paper
 - [x] InstaDeep job application 1-3 pm 
 - [ ] read statistic book



## 2023-11-13 week TO DO list

 - [x] Go though python workshop
 - [x] Get relay 
 - [x] larch code change
 - [x] sort out attendee of PPIT data collection
 - [x] write mini-KTP application
 - [x] write EXAFS fitting code
 - [x] Check on skeleton movement with STM32 and UNITY
 - [x] Prepare python workshop and email
 - [x] Change EXAFS code to k space
 - [x] Maximum likelihood and least square


## 2013-10-16 week TO DO list
Ask about archery 
 - [x] change archery booking
 - [x] send oliver and qinghua the mini-KTP program
 - [x] write NN for PPIT with new data and only conv-2D


## 2023-10-08 week TO DO list
before 12: write email to Kingston
12:00 -- 1:00 CV change and submit
12:30 -- 1:00 summary about the week
3:00 -- 6:30 error corrector paper
7:30 -- 11:00 life in test prep


- [ ] Contact Alston to discuss possible help with his project.
![[PPIT To-Do List#PPIT 2023-10-08]]
![[Journal paper#EC paper to-do list]]


![[2023-07-17#2023-07-17 to-do list]]
![[2023-07-03#2023-07-03 to-do list]]
![[2023-06-26#2023-06-26 to-do list]]
![[2023-06-19#2023-06-19 to-do list]]
![[General]]
# Fun tasks

## Error corrector

![[Error Corrector To-Do List#High priority]]

## PPIT

[[PPIT Journal|thought]]

![[PPIT To-Do List#High priority]]

## Exoplanet

![[Exoplanet To-Do List#High priority]] ^df6833