# IBM Digital Tech Tutorial: Build your own Art Expert with Visual Recognition

## This hands on tutorial uses Watson Studio and Watson Visual Recognition to identify the artist of your favorite paintings.

![](/screenshots/intro-0.png)

## Learning objectives

After completing this tutorial you will be able to:
* Create a Visual Recognition model in Watson Studio running on IBM Cloud
* Capture images of paintings by artists such as Rubens, Renoir, van Gogh and Macke and zip them into a class (provided)
* Train a model to identify the artist of a painting
* Score the identified artist

## Prerequisites
This tutorial can be completed using an IBM Cloud Lite account.
1. Sign up for an [IBM Cloud account](https://cloud.ibm.com/registration).
2. Fill in the required information and press the **Create Account** button.
3. After you submit your registration, you will receive an email from the IBM Cloud team with details about your account. In this email, you will need to click the link provided to confirm your registration.
4. Now you should be able to log into [IBM Cloud](https://cloud.ibm.com/login).

## Hands on Tutorial Overview

#### Step 1 - Capture Images
We have created four zip files of paintings. You will use these pictures to identify the corresponding artist: Rubens, Renoir, van Gogh and Macke. These images will be used as your training set.

#### Step 2 - Set up Watson Studio
Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts. You will create a Watson Studio account and create a Visual Recognition project.

#### Step 3 - Build a Visual Recognition model
You will create a Watson Visual Recognition model to identify images in several classes.

#### Step 4 - Test the model
You will use sample pictures to confirm your model.

#### Step 5 - Implement your model in your application
Embed your model into an application using code snippets.

## Create a Watson Studio Service Instance

* Open a Web browser and navigate to https://cloud.ibm.com

* Click on the **Create resource** button in the upper right.

    ![](/screenshots/dashboard-0.png)

* In the left menu select **AI** and click on the the **Watson Studio** service tile

    ![](/screenshots/catalog-0.png)
* Select a region: **Dallas**

    ![](/screenshots/watson-studio-0.png)

* Click the **Create** button in the lower right.

* After the Watson Studio service is created, click on **Get Started** or visit Watson Studio at https://dataplatform.cloud.ibm.com/

    ![](/screenshots/watson-studio-1.png)

* Click again on **Get Started**

    ![](/screenshots/watson-studio-2.png)

## Create a Watson Studio Project
Projects are your workspace to organize your resources, such as assets like data, collaborators, and analytic tools like notebooks and models.

* Click on **Create a project**

    ![](/screenshots/watson-studio-3.png)

* Select the **Create an empty project** tile

    ![](/screenshots/watson-studio-4.png)

* Give your project a name: **My Visual Recognition Project**
* Click on **Add** to define a Cloud Object Storage instance

    ![](/screenshots/watson-studio-5.png)

* Create Cloud Object Storage: You will store images and training data in a Cloud Object Storage bucket
* Select the **Lite** plan 
* Click on the **Create** button and then **Confirm** to create a Cloud Object Storage instance

    ![](/screenshots/cloud-object-storage-0.png)
    ![](/screenshots/cloud-object-storage-1.png)

* Click on **Refresh** on the New project tab

    ![](/screenshots/watson-studio-6.png)

* Click on **Create** to create the new project

    ![](/screenshots/watson-studio-7.png)

* Click on **Add to project** and select **Visual Recognition model** on the **Choose asset type** popup.

   ![](/screenshots/watson-studio-8.png)

* Your project needs to be associated with a Watson Visual Recognition Service instance
* Click on the **here** link in the popup to Associate a Watson Visual Recognition service.

    ![](/screenshots/watson-studio-9.png)

## Create a Watson Visual Recognition Service 
* Select the **Lite** plan
* Click on the **Create** button and then **Confirm** to create the Visual Recognition Service instance

    ![](/screenshots/visual-recognition-0.png)
    ![](/screenshots/visual-recognition-1.png)

* Select **Classify Images - Create Model** on the **Custom Models** page

    ![](/screenshots/watson-studio-10.png)

You are ready to set up your project with Watson Visual Recognition. 

## Create a Visual Recognition Model
* The **Default Custom Model** name is not descriptive so let's rename it
* Click on the **pencil** icon to edit the name
* Rename the model to **Painters**

    ![](/screenshots/visual-recognition-2.png)

## Upload training data to your Watson Studio project
* Four zip files have been prepared which contain paitings by the artists. Download the zip files [here](https://github.com/Beate-IBM/digital-tech-tutorial-visual-recogniton/tree/master/classes)
    * macke.zip
    * vangogh.zip
    * renoir.zip
    * rubens.zip

* Click on the **Browse** button
* An operating system native File Dialog will open
* Multi-select the four zip files **macke.zip, rubens.zip, renoir.zip, vangogh.zip**
* Upload these zip files to your Watson Studio project

    ![](/screenshots/visual-recognition-4.png)

* You can see that four new classes were created, **macke**, **renoir**, **rubens** and **vangogh**
* This custom classifier does not contain a Negative zip file. It is recommended but not required
 
## Train your Watson Visual Recognition Custom Classifier

 * Click on the **Train Model** button

    ![](/screenshots/visual-recognition-5.png)

 * Wait (between 10 min and 2 hours) for the model to train on the images and come back.

    ![](/screenshots/visual-recognition-6.png)
  
 * Once the model has been trained, click on the **here** link or on the **Painters** link at the top to view and test your model.

    ![](/screenshots/visual-recognition-7.png)

## Review and Test

* Click on the **Test** tab

    ![](/screenshots/visual-recognition-8.png)

* Test your Watson Visual Recognition custom classifier with sample images

* Visit the [testdata](https://github.com/Beate-IBM/digital-tech-tutorial-visual-recogniton/tree/master/testdata) directory and download the image files onto your local hard drive. These images were not part of the training set and will be used to validate the visual recognition model.
* Return to the **Test** tab in the Watson Studio project
* There are two techniques to upload the images into the Test page:
    * Drag the individual images from your local file browser into the Test page
    * Click on the browse link to open a file selection dialog

    ![](/screenshots/visual-recognition-9.png)

* The trained custom classifier model will analyze the images

    ![](/screenshots/intro-0.png)

* Inspect the Confidence scores returned by the Watson Visual Recognition Custom Classifier

## Implement the Watson Visual Recognition custom model in your applications

You can incorporate this Watson Visual Recognition Custom Classifier model into your applications using a variety of programming languages - Java, Node, Python, Ruby, Core ML

* Click on the **Implementation** tab to review the code snippets
* Click on the the name of your Associated Service

    ![](/screenshots/visual-recognition-11.png)

* Click on the **Credentials** tab

    ![](/screenshots/visual-recognition-12.png)

* Copy your **apikey** for use in the curl example below

* Use the code snippet to classify images against your model.

    **Classify an image (GET)**

    curl -u "apikey:{apikey}" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://az334033.vo.msecnd.net/images-4/roses-vincent-van-gogh-1890-2c442b97.jpg&version=2018-03-19&classifier_ids=Painters_1893624237"

## Congratulations

You have completed the Visual Recognition Lab.






