
# Status Update

## Goal
_To develop the high level to mid level layer as described in the NaViLa paper_

## Main Objective
_To develop the layer which acts as the brain of the robot dog, taking as input the present and past observations of the robot dog, along with the goal set by the user, and uses a VLM model behind the scenes, to output the next action to be taken_

### TL;DR of Main Objective Progress
_Explored various VLMs, built a simplistic layer serving as a starting point for the task_

## Subsections (Key Focus Areas)
- **Model Selection and Analysis**: Evaluating suitable VLMs for this task, checking their accuracy, score on benchmarks, and ease of integration
- **Information State**: Defining what the information state should be, if only image is sufficient or if other data helps, how many images to store in memory, etc. Also exploring on storing data such as distance to objects
- **Prompt and Output Processing**: Crafting prompts and preparing structured inputs from the information state for the VLM, and interpreting its outputs
- **Functional Integration**: Combining all parts into a working pipeline that produces actionable outputs from inputs

### TL;DR of Subsections
- **Model Selection and Analysis**: Tried instaling NVILA, did not work. Tried Qwen locally and Groq API—Groq has shown better results
- **Information State**: Haven’t explored alternatives yet; currently using past image inputs as per the paper
- **Prompt and Output Processing**: Initial version done for current setup, will change with the above two subsection changes
- **Functional Integration**: Basic version operational with current assumptions
---

## Detailed Status Report

🟩 Green – Progressing confidently  
🟨 Yellow – Progressing, but with open questions  
🟥 Red – Blocked, requires external input

---


### Topic 1: _Model Selection and Analysis_  
**Status**: 🟨 Yellow  
**Details**:  
Had tried to set up NVILA as done in the paper, however ran into many issues such as incompatible versions, model size too big for gpu, quantization dependency conflicts with the vila repository dependencies. Thus, tested both a local instance of Qwen 2.5 7B running on LM Studio and the Groq API. The Groq model has shown better quality.
**Help Needed**:  
- Should I continue efforts to get VILA running, or pivot to another model?  
- Is using an API-based model acceptable for now, or is a locally hosted model preferred for future development?  
- As fine-tuning will eventually be required, should I begin preparing a dataset (collection and labelling)?  
- Which of these priorities should I focus on next?

---

### Topic 2: _Information State_  
**Status**: 🟨 Yellow 
**Details**:  
Have implemented what the research paper has done, where they only use the past camera positions to make their states, and give it to a VLM for navigation.
**Help Needed**:  
- Incorporating a short-range infrared sensor (e.g., for distances up to 5m) would help improve navigation accuracy, should we consider this?  
- Is there value in adding a second camera for depth triangulation, similar to two eyes being present in humans?

---

### Topic 3: _Prompt and Output Processing_  
**Status**: 🟩 Green
**Details**:  
Prompt and Output Processing is implemented fully. Subject to change in the first two topics, this may also change to incorporate the changes. Further steps would be to make this more robust by including exception handling etc which is possible in an actual robot if it does not give a valid output.

---

### Topic 4: _Functional Integration_  
**Status**: 🟩 Green
**Details**:  
Functional Integration is also done fully. It is also subject to change based on changes in the first two topics, just like Prompt and Output Processing. Similar to it, further steps would be to make this more robust by including exception handling etc which is possible in an actual robot if it does not give a valid output.

---
