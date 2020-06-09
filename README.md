https://medium.com/@n.itvedant/deploy-machine-learning-model-in-heroku-using-flask-web-app-4e938065c4da

# Deploy-mahcine-learning-model-on-heroku
Medium Blog which describes step by step how you can deploy your machine learning model on heroku by creating web app using flask



This Story is all about how to deploy your machine learning model on heroku using flask web app :)
So the first question comes in your mind is Why we need to do this ?
— Whenever we create some model using machine learning algorithm it is only used by us on our local system, but we create any model for making other persons task easy, so how other person can use this model ?
if it is available and use full only in your local system :(
Hence, We require to deploy our model on any Platform from where other person can use it.
So, Let’s start it. There are basically
7 Steps to deploy your model on heroku
Step 1 : Train your model and dump (save) it into your disk
Step 2 : Create Web app Using Flask
Step 3 : Create HTML file to create UI for user
Step 4 : Create requirements.txt and Procfile
Step 5 : Commit the code in github
Step 6 : Create Heroku account
Step 7 : Deploy the model on heroku
Step 1 : Train your model and dump (save) it into your disk
Once your model training completed successfully dump your model using pickle module. The pickle module implements a fundamental, but powerful algorithm for serializing and de-serializing a Python object structure
Pickle model provides the following functions –
pickle.dump to serialize an object hierarchy, you simply use dump().
pickle.load to deserialize a data stream, you call the loads() function.
Example: Let’s apply Linear Regression on dataset and then save the model.

Trained Model using Machine learning
# save model into your disk
pickle.dump(lr,open(‘model.pkl’,’wb’))
# where first parameter is your model object and second parameter used to save your file using write binary format ( “model.pkl” is the name of the file you want to save, you can save it anywhere by just giving file location and .pkl extension)
# load the model to compare the result
model = pickle.load(open(‘model.pkl’,’rb’)) # read your file by read binary format
print(model.predict([[2000]]))
Step 2 : Create Web app Using Flask
Once your model is dump in your disk your file_name.pkl file is ready to use
create app.py file in your flask project and load the model, where your
- import pickle
- file = open(‘file_name.pkl’,’rb’)
- lr = pickle.load(file)
- file.close()
# Flask code to create app


app.py
Step 3 : Create HTML file to create UI for user
# To create HTML file > create folder name “templates” → inside it create html file “index.html”
This both app.py and templates folder both should be at same location or in same folder

index.html
Step 4 : Create requirements.txt and Procfile
# before commit the code In github you have to create some configuration file. This both file is must for deployment of your machine learning model
requirements.txt
This File contains all the packages required for your web app, so when it deploy into heroku it will automatically identify the package list and install in your app, but if some packages are missing then it will not getting deployed and generate log (error)
Add following list of packages with there version
Flask==1.1.1
Gunicorn==19.9.0
Itsdangerous==1.1.0
Jinja2==2.10.1
MarkupSafe==1.1.1
Werkzeug==0.15.5
Numpy>=1.9.2
Scipy>=0.15.1
Scikit-learn>=0.18
Matplotlib>=1.4.3
Pandas>=0.19
Procfile
Heroku apps include a Procfile that specifies the commands that are executed by the app on startup. Indirectly it tells to heroku which file should execute first :-
web: gunicorn app:app
Where , web: gunicorn # default syntax
# app:app #first app is your file name # second app is your flask name
Step 5 : Commit the code in github
Steps for commiting your code into github, Remember if you don’t have github account create github accout and follow the steps:-
Create a new github repository in your account
Open cmd ( command prompt)
Go to directory where your flask project is ?
Follow the below command //
git init
git add .
git commit –m “any message you want to save”
copy the url which is present in your repository file
git remote add origin your_url
git push –u origin master
Step 6 : Create Heroku account
If you don’t have heroku account then first create your heroku account
Go to “Heroku.com” and create your account
Step 7 : Deploy the model on heroku
Follow the below steps :-
Click on new button (present at left upper side) → click on create new app → give app_name as per your choice → click on create app
Download commnd line heroku (present at below in your heroku site) to see the log(error) of the model
Select Deployment Method as → GitHub Connect to GitHub
Connect your github repository
Once your repository connect successfully there are two deployment option ( automatic / manual)
Automatic ( when you commit something in ithub file it will automatically make changes in project )
Manual ( you have to manually make changes in the data of deployment)
Choose as per your choice
If deployment successfully done it is good but if it is not successfully done then check some error in log file
Open cmd (command prompt)→ type the command “heroku login” → heroku logs — app app_name
# where app_name →name given by you while creating app in heroku
You can open your app by clicking “Open app” button, which will provide you a unique URL which can be access globally
Thank You :)
