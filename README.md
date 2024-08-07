# Stable Diffusion Image Generation and Editing
## Description

This code uses the Stable Diffusion model to generate and edit images based on text prompts. It includes examples for generating new images, inpainting (filling missing areas), and replacing backgrounds.
### Model
#### Overview
The CompVis/stable-diffusion-v1-4 model is a text-to-image generation model that uses a stable diffusion process to produce high-quality images from text prompts.
#### Key Features
Text-to-Image Generation: Generates images from text prompts.

Stable Diffusion Process: Refines and improves image quality during generation.

High-Quality Images: Produces images with realistic details and textures.

Version 1.4: Fine-tuned for better performance and image quality.
#### Applications
Artistic Image Generation: Generates artistic images from text prompts.

Image Editing: Edits and refines existing images based on text prompts.

Content Creation: Automates image generation for content creation.
#### Limitations
Dependence on Training Data: Quality of generated images depends on training data.

Potential Biases: May inherit biases present in training data.
#### Technical Details
Parameters: Approximately 1.4 billion parameters

## Installation

To run this code, you'll need to install the required libraries. Run the following commands:

```bash
!pip install torch torchvision transformers diffusers
!pip install pillow requests
```
## Usage
### Image Generation

To generate a new image based on a text prompt:
```Python
prompt = "A futuristic cityscape"
result = pipe(prompt=prompt).images[0]
result.save("generated_image.jpg")
```

<div style="display: flex; justify-content: space-between;">
  <img src="generated_image.jpg" width="300" />

</div>

### Inpainting
To fill a missing area in an image:
```Python
input_image = Image.open("input_image.png").convert("RGB")
mask_image = Image.open("mask_image.png").convert("L")
prompt = "Fill the missing area with a forest background"
result = pipe(prompt=prompt, init_image=input_image, mask_image=mask_image).images[0]
result.save("Painted_image.jpg")
```

<div style="display: flex; justify-content: space-between;">
  <img src="input_image.png" width="300" />
  <img src="mask_image.png" width="300" />
  <img src="Painted_image.jpg" width="300" />
</div>

### Background Replacement
To replace the background of an image:
```Python
prompt = "A beach with a sunset"
new_background = pipe(prompt=prompt).images[0]
original_image = Image.open("input_image.png").convert("RGB")
mask_image = Image.open("mask_image.png").convert("L")
combined_image = Image.composite(original_image, new_background, mask_image)
combined_image.save("path_to_save_combined_image.jpg")
```

<div style="display: flex; justify-content: space-between;">
  <img src="input_image.png" width="300" />
  <img src="mask_image.png" width="300" />
  <img src="new_background_image.jpg" width="300" />
</div>

### Models and Tokens
This code uses the CompVis/stable-diffusion-v1-4 model from Hugging Face. You'll need to replace with your own Hugging Face token.

### License
This code is licensed under the MIT License.
