# Cotton-Disease-Detection
Agriculture is an important backbone for any country and India is considered to be an agro-based country.It not only boosts various industries such as food industry and textile industry but when it comes to textile industry cotton producing crops hold a special position amongst all other textile crops.Though growing cotton is not an easy task and it requires a lot of expertise and farmers have to face a lot of hardships in the process.After facing so many hardships, if their crops get exposed to diseases and are not treated timely then it affects the crops and also life of farmers to a great extent.So, it will be better to have an AI agent take care of the plants to let us know if the crops are suffering from any disease or so.This can be identified by looking at the leaves of the plant.

## About Project
- Predict cotton plan disease based on the input image.
- Dataset link: https://www.kaggle.com/datasets/janmejaybhoi/cotton-disease-dataset
- Train data: 1951 images. Validation data: 253 images. Test data: 106  images
- Trained using CNN and VGG16 architectures (TRANSFER LEARNING).
- VGG16 offered accuracy: 0.9959  - loss: 0.0250 - val_loss: 0.1015 - val_accuracy: 0.9340 for 20 epochs.
- Application predicts the uploaded image into 1 of the category: "diseased cotton leaf" , "diseased cotton plant" , "fresh cotton leaf" , and "fresh cotton plant"
- Images captured from drone/camera can be used to predict the cotton disease. Whereas, the manual intervention of detecting cotton disease would be difficult for large area of land.

# Data Description:
The dataset consists of 4 selected different Disease of cotton plant such as 
- "Diseased cotton leaf"
- "diseased cotton plant"
- "fresh cotton leaf"
- "fresh cotton plant"
- Each folder is named, and contains around 500+ images of that particular category. Based on the given image, we need to classify the cotton disease detection.

- you can download the dataset from kaggle: https://www.kaggle.com/datasets/janmejaybhoi/cotton-disease-dataset

## Data Visualization
we can use OpenCV to see what kind of data we are dealing with.We can run the following commands to view any random image data.
The dataset consists of images belonging to four classes namely Diseased Cotton Leaf, Fresh Cotton Leaf, Diseased Cotton Plant and Fresh Cotton plant.

## Dataset Creation
we used ImageDataGenerator Module of the Keras Image Preprocessing Library.This will load the images along with their labels for us in a format which is recognizable by Keras for further training process.We simply have to create the train_generator and test_generator and and then when we run them they will create the dataset.

## Model Training
- After creating the dataset next step is to pass our training data for our Deep Learning model to learn to identify or classify different classes of images.
- We have used a VGG-16 pretrained model and have applied transfer learning.We have modified the last dense layer of the VGG model according to our needs.We will not train the entire VGG model but only certain layers which we have added to our pre-existing model.
- The loss function used was “categorical_crossentropy” and optimizer used was “Adam”.For training the model we used Keras API with tensorflow at backend.The model showed good performance achieving a decent accuracy

## Initialize the Git Repositry
 - git init
 - git add .
 - git commit -m "first commit"
 - git branch -M main
 - git remote add origin <github_url>
 - git push -u origin main 

 ### To update the modification or modification on github repositry
 - git add .
 - git commit -m "proper message"
 - git push -u origin main 

 ## Create a file "Dockerfile" with below content
     FROM python:3.9
     COPY . /app
     WORKDIR /app
     RUN pip install -r requirements.txt
     ENTRYPOINT [ "python" ]
     CMD [ "app.py" ]  

### To Build the Docker Image on DockerHub
 docker build -t "docker_profile_name/app_name": latest .   

### To run the container Image
 docker container run -d -p "port number:EX-5000" "docker_profile_name/app_name": latest

### To Upload the Docker Image on DockerHub
  docker push "docker_profile_name/app_name": latest

### Create a "Procfile" with following content
 web:gunicorn main:app     

## To configure with AWS Elastic Beanstalk need to upldate .ebextensions folder in the project as :
     .ebextensions\python.config:
                     option_settings:
                       "aws:elasticbeanstalk:container:python":
                         WSGIPath:application.py:application 

## How to run ? 
1. Clone/Download the project from github
2. Follow above "Trained prediction model link" step
3. create new conda/python environment, activate the environment created and install application dependencies via terminal command in root directory of the application by "pip install -r requirments.txt", update the depenencied based on Environment.
4. Run application.py file.




