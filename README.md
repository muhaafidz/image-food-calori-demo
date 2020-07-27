# image-food-calori-demo
This project is entirely based on AxelAli project. But there are still things that need to change and requires a lot of time to configure it in order to run it successfully. So, I recreate his project for making the process simpler.
* NOTE: I use Windows environment for running this project. You may need to change all paths into UNIX style if you are using Linux or Mac.
Original source:

	https://github.com/AxelAli/Tensorflow-Image-Classifier-Web-Demo
	https://github.com/AxelAli/Tensorflow-Image-Classification

PREREQUISITE:
1. 	Install required software:
	
		-XAMPP (or any tools to do localhost)
		-Python 3.6.1 64 bit. (3.7,3.6.0 doesn't work with Tensorflow)
		-LightShot (*Optional: good snipping tool alternative to save Google Image in lazy way. Make sure save the image in jpg format)
		-Microsoft Visual C++ 2015 Redistributable Update 3 (install if required step in PREREQUISITE doesn't work)

2.	Run cmd command:

		python -m pip install --upgrade pip
		pip3 install -U pip virtualenv
		pip install tensorflow --upgrade
		pip install image
	
3.	Test the tensorflow whether it is work using cmd. If it display the tensorflow version, it means the prerequisite is done:
		
		python -c "import tensorflow as tf; print(tf.VERSION)"
	
	*If didn't work, locate the python directory and install appropriate version of tensorflow whl using CMD:
	
		cd C:\Users\<your pc name>\AppData\Local\Programs\Python\Python36
		                       or
		cd C:\Python36  *depend on your python directory
		
		pip install https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.11.0-cp36-cp36m-linux_x86_64.whl
	
	*Additional command if doesn't work:
	
		pip install ipykernel
		pip install tensorflow_hub

PREPARE THE PROJECT (Using XAMPP):

1.	Download the entire project from this github.

2.	Save the project in XAMPP httdocs directory. Eg:

		C:\xampp\htdocs\image-food-calori-demo-master

3.	Run the website through localhost. (The prediction won't work yet since there is no trained model in the project folder)
		
		http://localhost/image-food-calori-demo-master/
	
TRAIN THE IMAGE: 

1. 	Download a collection of images at any source.
2.  	Save the image at "..\tensorflow\data\<appropriate group image folder>\
   	*Make sure that save it in jpg format. And each of image group need to have at least 21 images and above.
    	*You also can create a new folder to add a new image group.
	
2.	"ocate tensorflow folder location in CMD. eg:
      
		cd C:\xampp\htdocs\image-food-calori-demo-master\tensorflow
	
	Train the image by executing this command using CMD:
	    
		python retrain.py --bottleneck_dir=./output/bottlenecks --how_many_training_steps 300  --model_dir=./output/inception --output_graph=./output/retrained_graph.pb --output_labels=./output/retrained_labels.txt --image_dir ./data/

	If it is successfull, the retrained_graph.pb file is created in output folder. This file is the model that is eesential to do image prediction.
	
TEST THE WEBSITE:

1.	Open the website through localhost.

		http://localhost/image-food-calori-demo-master/

2.	Try to upload some image. Enjoy!
