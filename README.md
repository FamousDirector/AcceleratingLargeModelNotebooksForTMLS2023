# Notebooks on how to Accelerate Large AI model inference
This repository was created to add code examples to be used alongside the workshop 
"Accelerating Large Models In Production: A Practical Guide"
presented at Toronto Machine Learning Summit 2023 by James Cameron. [Slides and notes can be found here](https://docs.google.com/presentation/d/1uIPgECdBn_rDhQtKED9Ia4li_wAVUNGuiwMuSkotdWA/edit?usp=sharing)

## Disclaimer
This repository is meant to serve as a starting point for new projects.
Always to be used only as a reference.

## System Requirements
- 4 core CPU (min 3.0 GHz)
- 8 GB System Memory
- Nvidia GPU w/ CUDA Compute Capability >=7.0
- 6GB Memory minimum

## Installation

### Setting up the environment
We need to install docker and docker-compose.
Please follow the instructions from [here](https://docs.docker.com/engine/install/) (Docker) 
and [here](https://docs.docker.com/compose/install/) (Docker Compose).

Next we need to install the Nvidia Container Toolkit.
Please follow the instructions from [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html).

Set the `nvidia` Docker runtime as default:
```
sudo tee /etc/docker/daemon.json <<EOF
{
  "default-runtime": "nvidia",
  "runtimes": {
    "nvidia": {
      "path": "/usr/bin/nvidia-container-runtime",
      "runtimeArgs": []
    }
  }
}
EOF
```

Restart Docker:
```
sudo service docker restart
```

Then test the installation:
```
docker run nvcr.io/nvidia/cuda nvidia-smi
```

You should see a similar output:
```
Tue Mar 29 12:38:23 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.81       Driver Version: 472.39       CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA RTX A3000    Off  | 00000000:01:00.0 Off |                  N/A |
| 25%   46C    P8    12W / 100W |    319MiB /  6144MiB |    18%       Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

## Running the project

To start the services, run the following command:
```
bash run.sh
```

### Accessing the Notebooks
Navigate to [http://localhost:8888/lab](http://localhost:8888/lab)

