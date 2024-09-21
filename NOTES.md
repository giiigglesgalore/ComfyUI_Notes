# ComfyUI_Notes
## InstantID
1. SDXL only
2. InstantID is for applying strong styling. there are other far better models for realistic images
3. to minimize the difference between result image and original image
   1. to load batch images rather than single image
   2. to decrease the weight in "Apply InstantID"
   3. to add IPAdapter (Face ID model)
   4. to add second IPAdapter with desired style image sample
4. InstantID Advanced Node
- it has two components - IPAdapter embedding, ControlNet
- IPAdapter apply up to 25% and ControlNet takes care of the rest
- rule of thumb: keep low weight on IPAdapter to make the result stay close to the prompt
![image](https://github.com/user-attachments/assets/ee8f3a39-ca0a-443b-94e7-eee99eefe982)

Questions
- what is "CLIP Vision"? what is the difference between "CLIP" and "CLIP Vision"?
- what does "cfg" do in KSmapler? why with more conditioning, cfg should be lower?


## Unet
![image](https://github.com/user-attachments/assets/1f075bb1-dd4a-4697-83f0-b076c2a9086c)
- composed by a series of block at ever step.


## FLUX: Metadata Selection
### Samplers and Schedulers
- Realistic style
  - Sampler: DPM_ADAPTIVE, DPMPP_2M, IPNDM, DEIS, DDIM, UNI_PC_BH2, *EULER
  - Scheduler: SGM_UNIFORM, SIMPLE, BETA, *DDIM_UNIFORM
- Illustrations
  - Sampler: EULER, DPM_ADAPTIVE, DEIS, DDIM
  - Scheduler: SGM_UNIFORM, SIMPLE, BETA, DDIM_UNIFORM
- Scheduler "KARRAS": good to give it a try, sometimes it generates good image


### Guidance
- start point: 3.5
- generally higher guidance generates more polished and saturated images
- for more cinenmatic and realistic image, lower guidance is more recommended
- for illustration, higher guidance gives stronger style
- for logo and text, lower guidance generates better result
- to avoide value 1, as guidance is probably multiplied to some other value at some point and multiplying by one doesn't change anything
- the default node doesn't allow negative value for guidance, but using below node, negative value can be applied
  ![image](https://github.com/user-attachments/assets/828a1b3a-f2e6-4e89-af1c-6b1b7bf92f73)


### Base and Max Shift
- defalut Max/Base Shift: 1.15/0.5
- shift is related to image size
- the aspect ratio of generated image will change how the shift is applied
  - at 1:1 ratio, Base Shift as no effect and only Max Shift is used
  - in Portrait and Landscape mode, both start to have a greater impact
- higher shift introduces more noise but generates more details. the noise can be reduced by applying more steps (more steps means more processing time)
- it is ok not stress too much about Base/Max Shift


### Attention Patching (FLUX Attention Seeker node in ComfyIU Essential)
- it is used to change the weight of the clip encoder but it is a bit of a placebo
- clip L usually has lower effect, so can be useful to steer the composition a little
- FLUX is not very good with styles, especially with long prompt



![image](https://github.com/user-attachments/assets/29f152c4-9b0f-4338-9ee1-87045c977909)
Q: query
K: Key
V: Value
- the porportion between the query and key determines the relevance of the embedding, the two are compared and the result is applied to the value to obtain the actual weight of the block.
- the product of this operation is finally multiplied to the output matrix that basically prepares the rsult for the next block
- conclusion:
  - if you want to change the behaviour of a block, you can change the proportion between query and key.
  - if you increase the weight of both query and key, you only change their magnitude but not the relationship
  - if you instead wish to change only the weight of the block, you work mostly with value out or both


## Hand Fixing
### MeshGraphormer
- unable to detect baby's hands

  
#### mask type
- based on depth 
- tight bboxes
- original



 
