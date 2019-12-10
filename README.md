# GGAIL_readme
Contains readme file for CS394R Reinforcement Learning project
# GGAIL: running instruction

## Install Mujoco with GPU:

System: Ubuntu 16.04| Nvidia driver 418 | CUDA 10.0 | anaconda3 python3.6

1 Download mujoco200 using following instruction:
https://github.com/openai/mujoco-py#obtaining-the-binaries-and-license-key
* Note: 

  put license key at ~/.mujoco/mujoco200/bin/mjkey.txt rather than ~/.mujoco/mjkey.txt.
  
  add following lines in ~/.bashrc:
  
      export LD_LIBRARY_PATH=~/.mujoco/mujoco200/bin${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
      
      export MUJOCO_KEY_PATH=~/.mujoco${MUJOCO_KEY_PATH}
      
      export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia-418

* test using following command(if works, a graphical interface should show up):

      cd ~/.mujoco/mujoco200/bin

      ./simulate ../model/humanoid.xml

2 Install mujoco_py:

* WARNING: don't follow https://github.com/openai/mujoco-py/blob/master/Dockerfile, some dependency such as xorg, will destory your system.

* Run the following commands:

      sudo apt install curl
      
      sudo curl -o /usr/local/bin/patchelf https://s3-us-west-2.amazonaws.com/openai-sci-artifacts/manual-builds/patchelf_0.9_amd64.elf
      
      sudo chmod +x /usr/local/bin/patchelf

      pip install cffi

      sudo apt-get install libx11-dev

      sudo apt-get install libglew-dev
      
      sudo apt-get install libosmesa6-dev (optional for 18.04)

      pip install 'gym[all]'

* Test using file: mujoco_test.py

## Set up coding environment

* Download openAI baseline code from 
https://github.com/openai/baselines/tree/master/baselines/gail
* Install dependencies:

    sudo apt install libopenmpi-dev
  
    pip install mpi4py
  
    pip install tqdm
* Put my code file folder into /baselines/.
* replace following file folders:      
* run

    python -m baselines.ggail.GGAIL
