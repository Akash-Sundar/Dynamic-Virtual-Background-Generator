# Text-Driven Dynamic Virtual Backgrounds for Video Calls

## Description

In the era of remote communication, enhancing the virtual meeting experience is paramount. Our project, Text-Driven Dynamic Virtual Backgrounds for Video Calls, aims to revolutionize video calls by integrating real-time dynamic virtual backgrounds that respond seamlessly to user movements. By leveraging state-of-the-art diffusion-based scene representation techniques trained on comprehensive 3D scene datasets, we create high-definition, textured environments directly from text prompts.

This innovative system not only generates immersive backgrounds but also ensures real-time adaptation to camera movements. As users shift their camera angle or position, the virtual environment mirrors these changes, providing a fluid and engaging experience. Our approach combines Neural Radiance Fields (NeRFs) with advanced optical flow and segmentation techniques, facilitating accurate background adaptation while keeping the user in focus.

The results of our efforts are significant: we achieved a 12.8% improvement in scene generation consistency, as measured by the Fréchet Inception Distance (FID) score, and demonstrated a 67% increase in consistency with well-crafted text prompts. This project represents a pivotal step towards redefining virtual communication, offering an immersive, adaptive space that faithfully replicates real-world dynamics.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Features](#features)
4. [License](#license)

## Installation
To set up the Text-Driven Dynamic Virtual Backgrounds for Video Calls project, follow the steps below:

### Prerequisites
Ensure you have Python (version 3.7 or later) installed on your system. You can check your Python version with:

```bash
python --version
```
### Setting Up a Virtual Environment (Optional)
It's recommended to create a virtual environment to manage dependencies for this project. You can create a virtual environment using venv:

```bash
# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# For Windows
venv\Scripts\activate

# For macOS/Linux
source venv/bin/activate
```

### Required Packages
You can install the necessary packages using pip. Ensure you have pip updated to the latest version:

```bash
pip install --upgrade pip
```

Then, install the required packages listed in requirements.txt by running:

```bash
pip install -r requirements.txt
```
### requirements.txt
The following packages will be installed:

```makefile
einops==0.6.1
diffusers==0.16.1
transformers==4.28.1
pytorch-lightning==1.5.0
torch==2.0.0
opencv-python==4.7.0.72
protobuf==3.20.3
wrapt==1.15.0
numpy==1.23.5
google==3.0.0
googleapis-common-protos==1.59.0
```

## Usage
To run the demo file, follow these instructions:

* Execute the demo script with the following command:

```bash
python demo.py --text "prompt" --input_path "path" --output_path "path"
```

* Update the parameters:

    - Replace "prompt" with a descriptive text prompt for the virtual room you want to create (e.g., "A cozy living room with large windows and a fireplace").
    - Replace "path" in --input_path with the path to the input video file you wish to modify (e.g., "./input/video.mp4").
    - Replace "path" in --output_path with the desired path where you want to save the output file (e.g., "./output/modified_video.mp4").

* Run the command, and the demo will process the input video according to the specified text prompt and save the modified output at the designated path.

Example Command:

```bash
python demo.py --text "A bright, modern kitchen with marble countertops" --input_path "./input/video.mp4" --output_path "./output/modified_video.mp4"
```

## Features

The methodology presented in this study leverages advanced neural architectures to generate dynamic virtual backgrounds through a series of iterative steps, enhancing both depth perception and visual fidelity. Here we outline the key features of our approach:

* Stable Diffusion Model Integration: Our method employs the Stable Diffusion 2 model, a state-of-the-art latent diffusion model that utilizes text prompts to guide image generation. By gradually adding noise and then removing it based on the input text, the model reconstructs images that are visually coherent and relevant to the specified scene.

* Latent Space Manipulation: The architecture incorporates a Variational Autoencoder (VAE) that compresses images into a latent space, allowing for efficient manipulation and eventual reconstruction of high-resolution images. This latent space facilitates improved control over the generated imagery, enabling more nuanced and detailed scene generation.

* Iterative Scene Generation: The pipeline involves an iterative scene generation process that includes rendering, refining, and repeating steps to create a comprehensive 3D mesh representation. This iterative method enhances the overall quality and depth of the generated scenes by continuously updating and integrating new visual elements.

* Depth Alignment Strategy: To ensure accurate integration of new and existing content in 3D space, we utilize a two-stage depth alignment strategy. This approach effectively estimates unobserved depth values through monocular depth prediction, facilitating a seamless fusion of the generated images and the existing mesh geometry.

* Panoramic Image Generation: Our method generates panoramic images through the creation of multiple perspective views. Using a multi-branch UNet architecture, we simultaneously denoise images to maintain consistency across various viewpoints. The integration of a Correspondence-aware Attention (CAA) block further enhances the alignment and coherence of the generated features across these views.

* Cross-Patch Attention Mechanism: By adapting the CPAttn mechanism from the MVDiffusion pipeline, we incorporate transformer modules that capture scene positional information. This allows for a more comprehensive understanding of spatial relationships within the scene, leading to improved consistency and realism in the generated images.

* Training and Fine-tuning: The proposed method employs a robust training regimen using the Matterport3D dataset, optimizing the performance of the attention layers through Mean Squared Error (MSE) loss. This ensures that the generated outputs are not only high in quality but also consistently reflect the input prompts.

* Performance Metrics Evaluation: We assess the model's performance using a combination of metrics, including Clip Score (CS), Inception Score (IS), FID Score, and user-assigned realism scores. These evaluations provide a comprehensive understanding of the model's effectiveness in generating high-quality and realistic scenes.

* Robust Text Prompt Handling: Our approach emphasizes the importance of well-structured text prompts for optimal performance. The model demonstrates adaptability to varying levels of detail in prompts, underscoring the significance of balancing descriptive elements to achieve desirable outputs.

* Future Directions for Integration: We acknowledge the potential for further enhancement by integrating other pre-trained models like DALL·E 2, which excels in generating diverse and creative solutions. Exploring these integrations remains a focus for future development, aiming to expand the capabilities of our pipeline for multi-view generation.

In summary, our methodology showcases a sophisticated approach to generating dynamic virtual backgrounds by effectively combining various neural network techniques and addressing challenges in scene representation and depth mapping. Through rigorous training and evaluation, we aim to push the boundaries of image generation in the context of 3D environments, providing a valuable contribution to the field.

![image](https://github.com/Akash-Sundar/Dynamic-Virtual-Background-Generator/assets/120504031/9fa0e704-81fd-4c99-9658-a4463ff25c1d)

## License
This project is licensed under the MIT License - see the LICENSE file for details.

