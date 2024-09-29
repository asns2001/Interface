## Maize Tassel Detector Backend

This is a flask backend with a custom model. Results are returned as a count of the maize tassel.

## Getting Started

- Make sure you have python version 3.9.13 downloaded
  - If you haven't installed Python 3.9.13 yet, you can download it from the [official Python website](https://www.python.org/downloads/release/python-3913/). Follow the instructions for your operating system and make sure to check the box to "Add Python to PATH" during installation.
- Ensure you cd into /Backend:
- Create a venv with python version 3.9.13 by specifying the path to the python 3.9.13 download.
  ```bash
  C:\Users\<your-username>\AppData\Local\Programs\Python\Python39\python.exe -m venv myenv
  ```
  - where `myenv` is the venv name
  - Replace <your-username> with your actual username and adjust the path if Python is installed in a different location.
- Ensure you have a cuda enabled GPU
  - Make sure your GPU is compatible with CUDA 11.7. You can check this on [NVIDIA’s CUDA GPUs page](https://developer.nvidia.com/cuda-gpus). 
- Activate the virtual environment(venv), you mist do the following in the venv
  - Run:
    ``` bash
    myenv\Scripts\activate
    ```
  - Verify the python version
    ```bash
    python --version
    ```
    - Make sure its python 3.9.13
- Get CUDA 11.7
  - Download CUDA 11.7
    - You can download CUDA 11.7 from the [NVIDIA CUDA Toolkit Archive](https://developer.nvidia.com/cuda-11-7-0-download-archive).
    - Go to the link above.
    - Choose your operating system (e.g., Windows).
    - Download the exe (local) installer for CUDA 11.7.
  - Install CUDA
    - Install CUDA 11.7:
    - Once you have downloaded the installer:
    - Run the installer. Make sure to choose "Custom (Advanced)" installation so you can select the components you want. Ensure that CUDA and cuDNN are selected.
    - OPTIONAL: Download Visual Studio for easier set up for future projects
  - Install cuDNN
    - You can download cuDNN from the [NVIDIA Developer website](https://developer.nvidia.com/cudnn). Make sure to select the version compatible with CUDA 11.7.
    - After downloading, you’ll need to manually copy the files to the CUDA installation folder:
    - Copy bin/* to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.7\bin.
    - Copy lib/* to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.7\lib\x64.
    - Copy include/* to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.7\include.
    - To verify that CUDA is installed correctly, open a terminal (or command prompt) and run:
      ```bash
      nvcc --version
      ```
      You should see details of CUDA 11.7 in the output.
  - Test CUDA with PyTorch
    - Install Pytorch, in the virtual environment, run:
      ``` bash
      pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117
      ```
    - Create a new file and put the code below in it and run it.
      ```python
      import torch
      print(torch.cuda.device_count())
      ```
    - If it returns 1 or more, CUDA is working correctly.
- Run the following

```bash
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117

pip install -r requirements.txt

python ./app.py
```
Once this is run, open the endpoint hosted at [http://localhost:5000](http://localhost:5000). It will be blank. 

There is a single post endpoint /upload, that takes a series of files and returns a string of the total count.

Prediction images are saved in `/runs`

**Open a new terminal for the frontend**
