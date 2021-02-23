## DeepNN Slides

The material here is offered based on two of my lectures that are part of the Deep Neural Networks class at the Computer Science and Technology department at the University of Cambridge: https://mlatcl.github.io/deepnn/

The two lectures in question were: "Convolutional Neural Networks" and "Hardware Ecosystem". Links to these lectures (including a video) are available here:

https://mlatcl.github.io/deepnn/lectures/03-01-hardware.html
https://mlatcl.github.io/deepnn/lectures/04-01-convolutional-neural-networks.html

### Installation and usage

Depending on how you want to view/use these slides you should install them in different ways. I'll describe these three ways below.

#### 1. Simply to view slides

If you only want to locally view the slides on your own machine, and aren't interested in running (and experimenting) with the code that is embedded then it is all very easy.... Simply sync to this repo, and run the two Jupyter Notebooks you find locally. As long as those notebooks have access to to the directory they expect to contain the images they will render fine.

This assumes you have the Jupter Notebook software dependencies installed locally. 

Then you run from the command line something like: `jupyter notebook --no-browser --allow-root --ip=0.0.0.0 home/niclane/` where you replace the directory path (currently listed in that command as 'home/niclane') with the location where you have placed this repo. 

If you are unfamilar with using Jupter Notebooks as slides then this link provides some background, and you'll find more info on the web: https://medium.com/@mjspeck/presenting-code-using-jupyter-notebook-slides-a8a3c3b59d67

The name of the two slide / code decks you need for the two lectures are:

Lecture_1_hardware_public.ipynb
Lecture_2_convolution_public.ipynb

Note, that when viewing them you will likely see a few errors generated by the code unless you have all the necessary other pieces of software (and hardware, such as GPU) available.

#### 2. You have a GPU available, and you want to experiment with the slide code

For you to run code in the notebook I've decided to take the approach of using docker. The main reason for this is that for the hardware deck, I have code that as a demonstration runs on the GPU and CPU to make a few comparisons. And depending on the setup that people have (GPU drivers etc) the code (which is very simple) might not be portable.

So the first step, please install docker: https://www.docker.com/

Then if you have a nvidia GPU install the nvidia docker by consulting: https://github.com/NVIDIA/nvidia-docker 

If you have a different GPU then you'll need to investigate a docker solution for your GPU but it is likely quite possible. 

Next we are going to run the notebook and everything within the docker image. But you'll interact with it in your host machine via some localhost ports (in a browser). So if you open a command line and run: `docker run -it --rm --gpus all -p 8888:8888 -v $(pwd):/home/niclane niclane7/DeepNN_Slides:latest` then you'll be able to simply then go a browser (in the host, not the VM) and start to interact with the slides via the Jupter Notebook web interface. If you look at near the bottom of the ouput from running the above command you will see a URL provided you can enter in your browers to follow. 

Docker will download other dependencies that you need into the image.

I would point out that only the hardware slides have this GPU/CPU issue. You can run the CNN code examples on CPU directly without any problem.

#### 3. You have a CPU only available, and you want to experiment with the slide code

In this case you are able to run some of the hardware code (the parts that are note GPU specific) and all of the CPU code. While also being able to go through all of the slides of course. 

The steps are identical to above. The only exception is that please remove `--gpus all` from the above commands.

I would also highlight that it is possible to run all of these things completely locally, and just requires you to install all the dependencies locally. 

