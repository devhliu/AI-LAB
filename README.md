# AI-lab: The Ideal Development Environment for Data Scientists to Develop and Export Machine Learning Models


![All in one solution for data science](AI-lab_logos.png)
<!-- TOC -->

- [AI-lab: The Ideal Development Environment for Data Scientists to Develop and Export Machine Learning Models](#ai-lab-the-ideal-development-environment-for-data-scientists-to-develop-and-export-machine-learning-models)
	- [1.1. Description](#11-description)
	- [1.2. USAGE](#12-usage)
	- [1.3. Launch an IDE and Start Developing](#13-launch-an-ide-and-start-developing)
		- [1.3.1. Jupyter notebook](#131-jupyter-notebook)
		- [1.3.2. VS Code](#132-vs-code)
	- [Do you have any suggestions?](#do-you-have-any-suggestions)

<!-- /TOC -->



## 1.1. Description
This project is reserved for creating a new development environment using docker for developing AI models in data science, in particular, computer vision.

I hand-crafted AI-lab to take advantage of docker capability and to have a reproducible and portable development environment. AI-lab allows you developing your artificial intelligence based computer vision application in Python using the most used artificial intelligence frameworks.

AI-lab is meant to be used to building, training, validating, testing your deep learning models, for instance is a a good tool to do transfer learning. It includes:

	- Ubuntu 18.04
	- NVIDIA CUDA 10.1
	- NVIDIA cuDNN 7.6.0
	- OpenCV 4.1.0
	- Python 3.6
	- Most used AI framework:
    	- TensorRT
      	- TensorFlow
      	- PyTorch
      	- ONNX
      	- Keras
      	- ONNX-TensorRT
    	- Jupyter-lab
    	- VS Code integration with remote development
    	- numpy
    	- matplotlib
    	- scikit-learn
    	- scipy
    	- pandas
    	- and more

## 1.2. USAGE

To install AI-lab you must have `docker-ce` installed on your machine to be able to use the pre-configured development environment. To do that, simply follow the steps to install [docker for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/), or select the suitable version depending on your OS.


* Pull AI-lab from Docker Hub

	```bash
		docker pull aminehy/ai-lab
	```

* Run the AI-lab and start your development

	* Move to your application folder
	``` bash
		cd path/to/folder/application
	```

	* then run AI-lab
	``` bash
		xhost +

		docker run -it --rm -v $(pwd):/workspace \
		--runtime=nvidia -w /workspace \
		-v /tmp/.X11-unix:/tmp/.X11-unix \
		-e DISPLAY=$DISPLAY \
		-p 8888:8888 -p 6006:6006 aminehy/ai-lab:latest
	```

## 1.3. Launch an IDE and Start Developing
### 1.3.1. Jupyter notebook

If AI-lab runs correctly on your machine then `Jupyter notebook` should run automatically. If this is not the case, launch it from the terminal with this command

```bash
jupyter notebook --allow-root --port=8888 --ip=0.0.0.0 --no-browser
```

### 1.3.2. VS Code

[VS Code](https://code.visualstudio.com/) offers the possibility to develop from inside docker container (thus, inside AI-lab), through the extension [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack). Read more in details [here](https://code.visualstudio.com/docs/remote/containers).



Two configuration folders `.devcontainer` and `.vscode` (inside `vscode_remote_dev`) are necessary to be able to use VS Code inside AI-lab. These two folders are hidden and must live in the directory of your application so that VS Code automatically detect AI-lab configuration. Therefore, you need to copy them inside your application folder.

To get these folders, first clone this repository and move to it
```bash
	git clone https://github.com/amineHY/AI-lab.git
	cd /AI-lab
```

Copy the two folders to your application folder, for instance `/path_to_folder_application`
``` bash
	sudo cp -R AI-lab/vscode_remote_dev/.* /path_to_folder_application
```

Finally, move to your application folder and launch VS Code
```bash
	cd /path_to_folder_application
 	code .
 ```

## Display the Memory Usage of the GPU

Depending on you developing, you might want to watch the memory consumption of your GPU. You can do that thanks to `gpustat`.
``` bash
watch -n0.5 -c gpustat --c -cupP
```


## Do you have any suggestions?

Please contact me and let me know [LinkedIn](https://www.linkedin.com/in/aminehy/).
