Enhanced Diffutoon Jupyter Notebook

{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github"
      },
      "source": [
        "[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/camenduru/Diffutoon-jupyter/blob/main/Diffutoon_jupyter.ipynb)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "VjYy0F2gZIPR"
      },
      "outputs": [],
      "source": [
        "# https://github.com/modelscope/DiffSynth-Studio/blob/main/examples/Diffutoon/Diffutoon.ipynb modified\n",
        "\n",
        "%cd /content\n",
        "!git clone https://github.com/Artiprocher/DiffSynth-Studio\n",
        "%cd /content/DiffSynth-Studio\n",
        "\n",
        "!pip install -q einops transformers controlnet-aux==0.0.7 sentencepiece imageio imageio-ffmpeg\n",
        "\n",
        "!apt -y install -qq aria2\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://civitai.com/api/download/models/229575 -d /content/DiffSynth-Studio/models/stable_diffusion -o aingdiffusion_v12.safetensors\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/guoyww/animatediff/resolve/main/mm_sd_v15_v2.ckpt -d /content/DiffSynth-Studio/models/AnimateDiff -o mm_sd_v15_v2.ckpt\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_lineart.pth -d /content/DiffSynth-Studio/models/ControlNet -o control_v11p_sd15_lineart.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11f1e_sd15_tile.pth -d /content/DiffSynth-Studio/models/ControlNet -o control_v11f1e_sd15_tile.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11f1p_sd15_depth.pth -d /content/DiffSynth-Studio/models/ControlNet -o control_v11f1p_sd15_depth.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_softedge.pth -d /content/DiffSynth-Studio/models/ControlNet -o control_v11p_sd15_softedge.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/Annotators/resolve/main/dpt_hybrid-midas-501f0c75.pt -d /content/DiffSynth-Studio/models/Annotators -o dpt_hybrid-midas-501f0c75.pt\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/Annotators/resolve/main/ControlNetHED.pth -d /content/DiffSynth-Studio/models/Annotators -o ControlNetHED.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/Annotators/resolve/main/sk_model.pth -d /content/DiffSynth-Studio/models/Annotators -o sk_model.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/lllyasviel/Annotators/resolve/main/sk_model2.pth -d /content/DiffSynth-Studio/models/Annotators -o sk_model2.pth\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M \"https://civitai.com/api/download/models/25820?type=Model&format=PickleTensor&size=full&fp=fp16\" -d /content/DiffSynth-Studio/models/textual_inversion -o verybadimagenegative_v1.3.pt\n",
        "!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/camenduru/Diffutoon/resolve/main/input_video.mp4 -d /content -o input_video.mp4"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {},
      "outputs": [],
      "source": [
        "config_stage_2_template = {\n",
        "    \"models\": {\n",
        "        \"model_list\": [\n",
        "            \"models/stable_diffusion/aingdiffusion_v12.safetensors\",\n",
        "            \"models/AnimateDiff/mm_sd_v15_v2.ckpt\",\n",
        "            \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "            \"models/ControlNet/control_v11p_sd15_lineart.pth\"\n",
        "        ],\n",
        "        \"textual_inversion_folder\": \"models/textual_inversion\",\n",
        "        \"device\": \"cuda\",\n",
        "        \"lora_alphas\": [],\n",
        "        \"controlnet_units\": [\n",
        "            {\n",
        "                \"processor_id\": \"tile\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "                \"scale\": 0.5\n",
        "            },\n",
        "            {\n",
        "                \"processor_id\": \"lineart\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11p_sd15_lineart.pth\",\n",
        "                \"scale\": 0.5\n",
        "            }\n",
        "        ]\n",
        "    },\n",
        "    \"data\": {\n",
        "        \"input_frames\": {\n",
        "            \"video_file\": \"/content/input_video.mp4\",\n",
        "            \"image_folder\": None,\n",
        "            \"height\": 1024,\n",
        "            \"width\": 1024,\n",
        "            \"start_frame_id\": 0,\n",
        "            \"end_frame_id\": 30\n",
        "        },\n",
        "        \"controlnet_frames\": [\n",
        "            {\n",
        "                \"video_file\": \"/content/input_video.mp4\",\n",
        "                \"image_folder\": None,\n",
        "                \"height\": 1024,\n",
        "                \"width\": 1024,\n",
        "                \"start_frame_id\": 0,\n",
        "                \"end_frame_id\": 30\n",
        "            },\n",
        "            {\n",
        "                \"video_file\": \"/content/input_video.mp4\",\n",
        "                \"image_folder\": None,\n",
        "                \"height\": 1024,\n",
        "                \"width\": 1024,\n",
        "                \"start_frame_id\": 0,\n",
        "                \"end_frame_id\": 30\n",
        "            }\n",
        "        ],\n",
        "        \"output_folder\": \"/content/output\",\n",
        "        \"fps\": 25\n",
        "    },\n",
        "    \"pipeline\": {\n",
        "        \"seed\": 0,\n",
        "        \"pipeline_inputs\": {\n",
        "            \"prompt\": \"best quality, perfect anime illustration, light, a girl is dancing, smile, solo\",\n",
        "            \"negative_prompt\": \"verybadimagenegative_v1.3\",\n",
        "            \"cfg_scale\": 7.0,\n",
        "            \"clip_skip\": 2,\n",
        "            \"denoising_strength\": 1.0,\n",
        "            \"num_inference_steps\": 10,\n",
        "            \"animatediff_batch_size\": 16,\n",
        "            \"animatediff_stride\": 8,\n",
        "            \"unet_batch_size\": 1,\n",
        "            \"controlnet_batch_size\": 1,\n",
        "            \"cross_frame_attention\": False,\n",
        "            # The following parameters will be overwritten. You don't need to modify them.\n",
        "            \"input_frames\": [],\n",
        "            \"num_frames\": 30,\n",
        "            \"width\": 1536,\n",
        "            \"height\": 1536,\n",
        "            \"controlnet_frames\": []\n",
        "        }\n",
        "    }\n",
        "}"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {},
      "outputs": [],
      "source": [
        "from diffsynth import SDVideoPipelineRunner\n",
        "\n",
        "config = config_stage_2_template.copy()\n",
        "config[\"data\"][\"input_frames\"] = {\n",
        "    \"video_file\": \"/content/input_video.mp4\",\n",
        "    \"image_folder\": None,\n",
        "    \"height\": 1024,\n",
        "    \"width\": 1024,\n",
        "    \"start_frame_id\": 0,\n",
        "    \"end_frame_id\": 30\n",
        "}\n",
        "config[\"data\"][\"controlnet_frames\"] = [config[\"data\"][\"input_frames\"], config[\"data\"][\"input_frames\"]]\n",
        "config[\"data\"][\"output_folder\"] = \"/content/toon_video\"\n",
        "config[\"data\"][\"fps\"] = 25\n",
        "\n",
        "runner = SDVideoPipelineRunner()\n",
        "runner.run(config)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {},
      "outputs": [],
      "source": [
        "import moviepy.editor\n",
        "moviepy.editor.ipython_display(\"/content/toon_video/video.mp4\")"
      ]
    }
  ],
  "metadata": {
    "accelerator": "GPU",
    "colab": {
      "gpuType": "T4",
      "provenance": []
    },
    "kernelspec": {
      "display_name": "Python 3",
      "name": "python3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}

Introduction

Welcome to the enhanced version of the Diffutoon Jupyter notebook! Originally created by camenduru.
I have taken the initiative to further develop this notebook to provide a more user-friendly experience.

In this version, you'll find an intuitive interface equipped with user-friendly forms that allow you to configure and control various settings without the need to interact directly with the underlying code. My goal is to make it as easy as possible for users of all skill levels to harness the power of the Diffutoon pipeline, enhancing accessibility and simplifying the process of generating stunning visual content.
Features

- User-Friendly Forms: Easily configure and run complex pipelines with a simple, intuitive UI.
- Enhanced Accessibility: Making the powerful Diffutoon pipeline accessible to users regardless of their coding expertise.
- Seamless Integration: Run the notebook directly from Google Colab with minimal setup.

Quick Start

- Open the Notebook: Click here to access the Enhanced Diffutoon Notebook.
- Configure Settings: Use the interactive forms to set up your processing pipeline.
- Run and Enjoy: Execute the notebook and watch as your configurations come to life, generating visually appealing results.

Connect with Me

    Twitter/X: https://x.com/bugonacci
    GitHub: https://github.com/bugonacci

Original Notebook

For reference or to see the original version, visit the Original Diffutoon Notebook. https://colab.research.google.com/github/camenduru/Diffutoon-jupyter/blob/main/Diffutoon_jupyter.ipynb

Enjoy Your Exploration and Creation

Thank you for visiting and using the Enhanced Diffutoon Notebook. Enjoy exploring and creating stunning visual content with ease!
