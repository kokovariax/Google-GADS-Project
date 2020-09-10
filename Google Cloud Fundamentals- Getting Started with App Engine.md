
**Google Cloud Fundamentals- Getting Started with App Engine**

You can list the active account name with this command:
```
gcloud auth list

```

You can list the project ID with this command:
```
gcloud config list project
```


Initialize your App Engine app with your project and choose its region:
```
gcloud app create --project=$DEVSHELL_PROJECT_ID
```
#When prompted, select the region where you want your App Engine application located.


Clone the source code repository for a sample application in the hello_world directory:
```
git clone https://github.com/GoogleCloudPlatform/python-docs-samples
```


Navigate to the source directory:
```
cd python-docs-samples/appengine/standard_python3/hello_world
```

Execute the following command to download and update the packages list.
```
sudo apt-get update
```


Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.
```
sudo apt-get install virtualenv

//If prompted [Y/n], press Y and then Enter.

virtualenv -p python3 venv
```

Activate the virtual environment.

```
source venv/bin/activate
```

Navigate to your project directory and install dependencies.
```
pip install  -r requirements.txt
```


Run the application:
```
python main.py
```
Please ignore the warning if any.
In Cloud Shell, click Web preview (Web Preview) > Preview on port 8080 to preview the application.


Navigate to the source directory:
```
cd ~/python-docs-samples/appengine/standard_python3/hello_world
```


Deploy your Hello World application.
```
gcloud app deploy

//If prompted "Do you want to continue (Y/n)?", press Y and then Enter.
//This app deploy command uses the app.yaml file to identify project configuration.
```

Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com
```
gcloud app browse
```

Copy and paste the URL into a new browser window.



App Engine offers no option to Undeploy an application. After an application is deployed, it remains deployed, although you could instead replace the application with a simple page that says something like "not in service."

However, you can disable the application, which causes it to no longer be accessible to users.

In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine > Settings.

Click Disable application.

Read the dialog message. Enter the App ID and click DISABLE.
