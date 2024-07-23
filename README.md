Enhanced Diffutoon Jupyter Notebook


        "                download_model(\"AnimateDiff\")\n",
        "\n",
        "    print(\"Selected models downloaded and installed.\")\n",
        "\n",
        "# Run the function to setup and download models\n",
        "setup_and_download()\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "cellView": "form",
        "id": "mqNjaPwvKwZu",
        "outputId": "9070ed9b-9ca1-4fa6-a407-774281555b8e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Downloaded stable_diffusion model.\n",
            "Downloaded AnimateDiff model.\n",
            "Selected models downloaded and installed.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 322
        },
        "id": "XrtMysRY5AM_",
        "outputId": "0a8a03c2-51e6-4583-f0c8-e7246fc08d8e",
        "cellView": "form"
      },
      "outputs": [
        {
          "output_type": "error",
          "ename": "HTTPError",
          "evalue": "503 Server Error: Service Unavailable for url: https://civitai.com/api/download/models/224732?type=Model&format=SafeTensor&size=pruned&fp=fp16",
          "traceback": [
            "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
            "\u001b[0;31mHTTPError\u001b[0m                                 Traceback (most recent call last)",
            "\u001b[0;32m<ipython-input-3-95c82360dbf3>\u001b[0m in \u001b[0;36m<cell line: 34>\u001b[0;34m()\u001b[0m\n\u001b[1;32m     32\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     33\u001b[0m \u001b[0;31m# Call the download function\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 34\u001b[0;31m \u001b[0mdownload_model\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mmodel_url\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mtarget_file\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m",
            "\u001b[0;32m<ipython-input-3-95c82360dbf3>\u001b[0m in \u001b[0;36mdownload_model\u001b[0;34m(url, output_path)\u001b[0m\n\u001b[1;32m     18\u001b[0m     \u001b[0;31m# Stream download with progress bar\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     19\u001b[0m     \u001b[0mresponse\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mrequests\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mget\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0murl\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mstream\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;32mTrue\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 20\u001b[0;31m     \u001b[0mresponse\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mraise_for_status\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m  \u001b[0;31m# Check that the request was successful\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m     21\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     22\u001b[0m     \u001b[0;31m# Get the total file size from the response headers\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
            "\u001b[0;32m/usr/local/lib/python3.10/dist-packages/requests/models.py\u001b[0m in \u001b[0;36mraise_for_status\u001b[0;34m(self)\u001b[0m\n\u001b[1;32m   1019\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   1020\u001b[0m         \u001b[0;32mif\u001b[0m \u001b[0mhttp_error_msg\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m-> 1021\u001b[0;31m             \u001b[0;32mraise\u001b[0m \u001b[0mHTTPError\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mhttp_error_msg\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mresponse\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m   1022\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   1023\u001b[0m     \u001b[0;32mdef\u001b[0m \u001b[0mclose\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
            "\u001b[0;31mHTTPError\u001b[0m: 503 Server Error: Service Unavailable for url: https://civitai.com/api/download/models/224732?type=Model&format=SafeTensor&size=pruned&fp=fp16"
          ]
        }
      ],
      "source": [
        "#@markdown ### Model Download Configuration\n",
        "model_url = \"https://civitai.com/api/download/models/224732?type=Model&format=SafeTensor&size=pruned&fp=fp16\" #@param {type:\"string\"}\n",
        "target_directory = \"/content/DiffSynth-Studio/models/stable_diffusion\" #@param {type:\"string\"}\n",
        "file_name = \"AniMesh.safetensors\" #@param {type:\"string\"}\n",
        "\n",
        "import os\n",
        "import requests\n",
        "from tqdm.notebook import tqdm\n",
        "\n",
        "# Define the full target path for the file\n",
        "target_file = os.path.join(target_directory, file_name)\n",
        "\n",
        "# Create the directory if it does not exist\n",
        "os.makedirs(target_directory, exist_ok=True)\n",
        "\n",
        "# Function to download the model\n",
        "def download_model(url, output_path):\n",
        "    # Stream download with progress bar\n",
        "    response = requests.get(url, stream=True)\n",
        "    response.raise_for_status()  # Check that the request was successful\n",
        "\n",
        "    # Get the total file size from the response headers\n",
        "    total_size = int(response.headers.get('content-length', 0))\n",
        "\n",
        "    # Write the file to the target location with progress bar\n",
        "    with open(output_path, 'wb') as f:\n",
        "        for chunk in tqdm(response.iter_content(chunk_size=8192), total=total_size//8192, unit='KB', unit_scale=True):\n",
        "            if chunk:  # Filter out keep-alive new chunks\n",
        "                f.write(chunk)\n",
        "\n",
        "    print(f\"Model downloaded and saved to {output_path}\")\n",
        "\n",
        "# Call the download function\n",
        "download_model(model_url, target_file)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "9SLm0x_n6UB1",
        "cellView": "form"
      },
      "outputs": [],
      "source": [
        "#@markdown ### Model Download Configuration for \"lora\"\n",
        "model_url = \"https://civitai.com/api/download/models/339595?type=Model&format=SafeTensor\" #@param {type:\"string\"}\n",
        "target_directory = \"/content/DiffSynth-Studio/models/lora\" #@param {type:\"string\"}\n",
        "file_name = \"Anime Outline.safetensors\" #@param {type:\"string\"}\n",
        "\n",
        "import os\n",
        "import requests\n",
        "from tqdm.notebook import tqdm\n",
        "\n",
        "# Define the full target path for the file\n",
        "target_file = os.path.join(target_directory, file_name)\n",
        "\n",
        "# Create the directory if it does not exist\n",
        "os.makedirs(target_directory, exist_ok=True)\n",
        "\n",
        "# Function to download the model\n",
        "def download_model(url, output_path):\n",
        "    # Stream download with progress bar\n",
        "    response = requests.get(url, stream=True)\n",
        "    response.raise_for_status()  # Check that the request was successful\n",
        "\n",
        "    # Get the total file size from the response headers\n",
        "    total_size = int(response.headers.get('content-length', 0))\n",
        "\n",
        "    # Write the file to the target location with progress bar\n",
        "    with open(output_path, 'wb') as f:\n",
        "        for chunk in tqdm(response.iter_content(chunk_size=8192), total=total_size//8192, unit='KB', unit_scale=True):\n",
        "            if chunk:  # Filter out keep-alive new chunks\n",
        "                f.write(chunk)\n",
        "\n",
        "    print(f\"Model downloaded and saved to {output_path}\")\n",
        "\n",
        "# Call the download function\n",
        "download_model(model_url, target_file)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "GWNwiqoZxQw4",
        "cellView": "form"
      },
      "outputs": [],
      "source": [
        "#@markdown ### General Model Configuration\n",
        "device = 'cuda' #@param [\"cuda\", \"cpu\"]\n",
        "input_video_file = \"/content/input_video.mp4\" #@param {type:\"string\"}\n",
        "output_folder = \"/content/output\" #@param {type:\"string\"}\n",
        "fps = 25 #@param {type:\"integer\"}\n",
        "\n",
        "#@markdown ### Processing Parameters\n",
        "seed = 0 #@param {type:\"integer\"}\n",
        "prompt = \"animated cartoon clay character, character cartoon made of clay, clay material, clay, clay toon, 3D clay, animated\" #@param {type:\"string\"}\n",
        "negative_prompt = \"verybadimagenegative_v1.3\" #@param {type:\"string\"}\n",
        "cfg_scale = 8.0 #@param {type:\"number\"}\n",
        "clip_skip = 2 #@param {type:\"slider\", min:0, max:10, step:1}\n",
        "denoising_strength = 1.0 #@param {type:\"number\"}\n",
        "num_inference_steps = 20 #@param {type:\"slider\", min:5, max:50, step:1}\n",
        "animatediff_batch_size = 24 #@param {type:\"integer\"}\n",
        "animatediff_stride = 10 #@param {type:\"integer\"}\n",
        "unet_batch_size = 2 #@param {type:\"integer\"}\n",
        "controlnet_batch_size = 2 #@param {type:\"integer\"}\n",
        "cross_frame_attention = False #@param {type:\"boolean\"}\n",
        "\n",
        "# Construct the complex configuration JSON\n",
        "config_stage_2_template = {\n",
        "    \"models\": {\n",
        "        \"model_list\": [\n",
        "            \"models/stable_diffusion/epiCRealism.safetensors\",\n",
        "            \"models/AnimateDiff/mm_sd_v15_v2.ckpt\",\n",
        "            \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "            \"models/ControlNet/control_v11p_sd15_lineart.pth\"\n",
        "        ],\n",
        "        \"textual_inversion_folder\": \"models/textual_inversion\",\n",
        "        \"device\": device,\n",
        "        \"lora_alphas\": [\n",
        "            {\n",
        "                \"model\": \"models/lora/ClayAnimation.safetensors\",\n",
        "                \"scale\": 2.0\n",
        "            },\n",
        "        ],\n",
        "        \"controlnet_units\": [\n",
        "            {\n",
        "                \"processor_id\": \"tile\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "                \"scale\": 1.0\n",
        "            },\n",
        "            {\n",
        "                \"processor_id\": \"lineart\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11p_sd15_lineart.pth\",\n",
        "                \"scale\": 1.0\n",
        "            }\n",
        "        ]\n",
        "    },\n",
        "    \"data\": {\n",
        "        \"input_frames\": {\n",
        "            \"video_file\": input_video_file,\n",
        "            \"image_folder\": None,\n",
        "            \"height\": 768,\n",
        "            \"width\": 768,\n",
        "            \"start_frame_id\": 0,\n",
        "            \"end_frame_id\": 64\n",
        "        },\n",
        "        \"controlnet_frames\": [\n",
        "            {\n",
        "                \"video_file\": input_video_file,\n",
        "                \"image_folder\": None,\n",
        "                \"height\": 768,\n",
        "                \"width\": 768,\n",
        "                \"start_frame_id\": 0,\n",
        "                \"end_frame_id\": 64\n",
        "            },\n",
        "            {\n",
        "                \"video_file\": input_video_file,\n",
        "                \"image_folder\": None,\n",
        "                \"height\": 768,\n",
        "                \"width\": 768,\n",
        "                \"start_frame_id\": 0,\n",
        "                \"end_frame_id\": 64\n",
        "            }\n",
        "        ],\n",
        "        \"output_folder\": output_folder,\n",
        "        \"fps\": fps\n",
        "    },\n",
        "    \"pipeline\": {\n",
        "        \"seed\": seed,\n",
        "        \"pipeline_inputs\": {\n",
        "            \"prompt\": prompt,\n",
        "            \"negative_prompt\": negative_prompt,\n",
        "            \"cfg_scale\": cfg_scale,\n",
        "            \"clip_skip\": clip_skip,\n",
        "            \"denoising_strength\": denoising_strength,\n",
        "            \"num_inference_steps\": num_inference_steps,\n",
        "            \"animatediff_batch_size\": animatediff_batch_size,\n",
        "            \"animatediff_stride\": animatediff_stride,\n",
        "            \"unet_batch_size\": unet_batch_size,\n",
        "            \"controlnet_batch_size\": controlnet_batch_size,\n",
        "            \"cross_frame_attention\": cross_frame_attention,\n",
        "            # The following parameters will be overwritten. You don't need to modify them.\n",
        "            \"input_frames\": [],\n",
        "            \"num_frames\": 30,\n",
        "            \"width\": 768,\n",
        "            \"height\": 768,\n",
        "            \"controlnet_frames\": []\n",
        "        }\n",
        "    }\n",
        "}\n",
        "\n",
        "# Print out the configuration for verification\n",
        "print(config_stage_2_template)"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# RUN"
      ],
      "metadata": {
        "id": "PHl_XtTZR8LY"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "mjnMbiRmxQw5",
        "cellView": "form"
      },
      "outputs": [],
      "source": [
        "#@markdown ### Video Input Configuration\n",
        "video_file = \"/content/input_video.mp4\" #@param {type:\"string\"}\n",
        "output_folder = \"/content/toon_video\" #@param {type:\"string\"}\n",
        "start_frame_id = 0 #@param {type:\"integer\"}\n",
        "end_frame_id = 64 #@param {type:\"integer\"}\n",
        "frame_height = 768 #@param {type:\"integer\"}\n",
        "frame_width = 768 #@param {type:\"integer\"}\n",
        "fps = 25 #@param {type:\"integer\"}\n",
        "\n",
        "from diffsynth import SDVideoPipelineRunner\n",
        "\n",
        "# Load the base configuration\n",
        "config_stage_2_template = {\n",
        "    \"models\": {\n",
        "        \"model_list\": [\n",
        "            \"models/stable_diffusion/epiCRealism.safetensors\",\n",
        "            \"models/AnimateDiff/mm_sd_v15_v2.ckpt\",\n",
        "            \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "            \"models/ControlNet/control_v11p_sd15_lineart.pth\"\n",
        "        ],\n",
        "        \"textual_inversion_folder\": \"models/textual_inversion\",\n",
        "        \"device\": \"cuda\",\n",
        "        \"lora_alphas\": [\n",
        "            {\n",
        "                \"model\": \"models/lora/ClayAnimation.safetensors\",\n",
        "                \"scale\": 2.0\n",
        "            },\n",
        "        ],\n",
        "        \"controlnet_units\": [\n",
        "            {\n",
        "                \"processor_id\": \"tile\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11f1e_sd15_tile.pth\",\n",
        "                \"scale\": 1.0\n",
        "            },\n",
        "            {\n",
        "                \"processor_id\": \"lineart\",\n",
        "                \"model_path\": \"models/ControlNet/control_v11p_sd15_lineart.pth\",\n",
        "                \"scale\": 1.0\n",
        "            }\n",
        "        ]\n",
        "    },\n",
        "    \"data\": {\n",
        "        \"input_frames\": {\n",
        "            \"video_file\": video_file,\n",
        "            \"image_folder\": None,\n",
        "            \"height\": frame_height,\n",
        "            \"width\": frame_width,\n",
        "            \"start_frame_id\": start_frame_id,\n",
        "            \"end_frame_id\": end_frame_id\n",
        "        },\n",
        "        \"controlnet_frames\": [\n",
        "            {\n",
        "                \"video_file\": video_file,\n",
        "                \"image_folder\": None,\n",
        "                \"height\": frame_height,\n",
        "                \"width\": frame_width,\n",
        "                \"start_frame_id\": start_frame_id,\n",
        "                \"end_frame_id\": end_frame_id\n",
        "            },\n",
        "            {\n",
        "                \"video_file\": video_file,\n",
        "                \"image_folder\": None,\n",
        "                \"height\": frame_height,\n",
        "                \"width\": frame_width,\n",
        "                \"start_frame_id\": start_frame_id,\n",
        "                \"end_frame_id\": end_frame_id\n",
        "            }\n",
        "        ],\n",
        "        \"output_folder\": output_folder,\n",
        "        \"fps\": fps\n",
        "    },\n",
        "    \"pipeline\": {\n",
        "        \"seed\": 0,\n",
        "        \"pipeline_inputs\": {\n",
        "            \"prompt\": \"animated cartoon clay character, character cartoon made of clay, clay material, clay, clay toon, 3D clay, animated\",\n",
        "            \"negative_prompt\": \"verybadimagenegative_v1.3\",\n",
        "            \"cfg_scale\": 8.0,\n",
        "            \"clip_skip\": 2,\n",
        "            \"denoising_strength\": 1.0,\n",
        "            \"num_inference_steps\": 20,\n",
        "            \"animatediff_batch_size\": 24,\n",
        "            \"animatediff_stride\": 10,\n",
        "            \"unet_batch_size\": 2,\n",
        "            \"controlnet_batch_size\": 2,\n",
        "            \"cross_frame_attention\": False,\n",
        "            \"input_frames\": [],\n",
        "            \"num_frames\": 30,\n",
        "            \"width\": frame_width,\n",
        "            \"height\": frame_height,\n",
        "            \"controlnet_frames\": []\n",
        "        }\n",
        "    }\n",
        "}\n",
        "\n",
        "# Create and run the video pipeline runner\n",
        "runner = SDVideoPipelineRunner()\n",
        "runner.run(config_stage_2_template)"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# WATCH PREVIEW and EJOY!"
      ],
      "metadata": {
        "id": "SMbF28Q3SJ7F"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "w-wOV0ZHxQw6",
        "cellView": "form"
      },
      "outputs": [],
      "source": [
        "#@markdown ### Display Processed Video\n",
        "video_path = \"/content/toon_video/video.mp4\" #@param {type:\"string\"}\n",
        "\n",
        "import moviepy.editor as mp\n",
        "\n",
        "# Display the video in the notebook\n",
        "video_clip = mp.VideoFileClip(video_path)\n",
        "video_clip.ipython_display(fps=24, maxduration=240)"
      ]
    }
  ],
  "metadata": {
    "accelerator": "GPU",
    "colab": {
      "gpuType": "L4",
      "machine_shape": "hm",
      "provenance": [],
      "collapsed_sections": [
        "-83R1mA3O_mz",
        "Y_MIfttKPPYp",
        "PHl_XtTZR8LY",
        "SMbF28Q3SJ7F"
      ],
      "include_colab_link": true
    },
    "kernelspec": {
      "display_name": "Python 3",
      "name": "python3"
    },
    "language_info": {
      "name": "python"
    }
  },

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
