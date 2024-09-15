# ComfyUI_Notes
## InstantID
1. SDXL only
2. InstantID is for applying strong styling. there are other far better models for realistic images
3. to minimize the difference between result image and original image
   1. to load batch images rather than single image
   2. to decrease the weight in "Apply InstantID"
   3. to add IPAdapter (Face ID model)
   4. to add second IPAdapter with desired style image sample


Questions
- what is "CLIP Vision"? what is the difference between "CLIP" and "CLIP Vision"?
- what does "cfg" do in KSmapler? why with more conditioning, cfg should be lower?


## InstantID Advanced Node
- it has two components - IPAdapter embedding, ControlNet
- IPAdapter apply up to 25% and ControlNet takes care of the rest
- rule of thumb: keep low weight on IPAdapter to make the result stay close to the prompt
![image](https://github.com/user-attachments/assets/ee8f3a39-ca0a-443b-94e7-eee99eefe982)


## Metadata Selection
### Guidance
- start point: 3.5
- generally higher guidance generates more polished and saturated images

### Realistic Metadata
- Sampler: DPM_ADAPTIVE, DPMPP_2M, IPNDM, DEIS, DDIM, UNI_PC_BH2, *EULER
- Scheduler: SGM_UNIFORM, SIMPLE, BETA, *DDIM_UNIFORM


### Illustrations
- Sampler: EULER, DPM_ADAPTIVE, DEIS, DDIM
- Scheduler: SGM_UNIFORM, SIMPLE, BETA, DDIM_UNIFORM

### Others
- Scheduler "KARRAS": good to give it a try, sometimes it generates good image


- 
