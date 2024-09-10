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
