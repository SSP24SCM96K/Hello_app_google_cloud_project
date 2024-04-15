Step1: Download and Install Docker from https://www.docker.com/
NOTE: MAKE SURE TO INSTALL DOCKER VERSION GREATER THAN OR EQUAL TO 20.10.12 AND TO CHECK DOCKER VERSION GO TO CMD TERMINAL AND TYPE "docker -- version"

Step2: Download and Install GCloud SDK from https://cloud.google.com/sdk/docs/install
 
step3: Steps to create Gcloud Project
      a. Visit https://console.cloud.google.com/
      b. Login to Google Cloud Platform with a personal email ID. Do not use your hawk email ID as this would restrict configurations in further steps. 
      c. Create a new project
      d. Create a project named "flaskworldapp1" and navigate to your newly generated project dashboard.
      
Step 4: To deploy application to gcloud platform:

      a. You must have Docker & Google Cloud installed on your computer. Additionally, you have to edit .yaml file that is provided to you with your 
         gcloud Project ID and GCloud Project Name
      b. Type `docker` on CMD terminal and press enter to get all required information
      c. Type `docker build .` on cmd to build a docker image
      d. Type `docker images` on cmd to see the first docker image. After hitting enter. You will see Newest created image which will be always on the top of the list
      e. Now we can see newest created image has tag as <none> and its image id.
         type ‘docker tag <your newest image id> gcr.io/<your project id>/<project name> and hit enter and then type docker images. 
         you will see your image id with tag name
      f. Type `gcloud init` on cmd and it will prompt Create or select a configuration choose existing configurations and hit enter and
         it will prompt Choose a current Google Cloud project, choose your current gcloud project number and hit ent
      g. Type ‘gcloud auth configure-docker’ on cmd
      h. Type ‘docker push <your newest created tag> on cmd terminal and hit enter
      i.Go to container registry you will see your newly pushed docker image, click on that docker image, after clicking, 
        you will be able to see docker image id and on the right side you will see "⋮", left click on "⋮" there you will be 
        able to see option "deploy it to cloud run" click on that and it will navigate you to cloud run 
      j.In cloud run, edit container image url by hitting select you will see something like this select your latest id and hit select.
      k.Allow unauthorized access while creating new service
      l.Go to container, variables & secrets, connection, security and edit container port from 8080 to 80
      m.Click select to create service

  Step5: Set up GitHub
       a. Download and install git on your machine from https://git-scm.com/downloads 
       b. Create a GitHub account if you do not already have one or Sign in to your github account.
       c. Create a new repository named Hello_app_google_cloud and keep everything set to defaults and click on create repository and follow the steps
          mentioned in the PPT.

  Step 6: To push your code to GitHub code:
          a. git init
          b. git add .
          c.git commit -m “flask microservice”
          d.git remote add origin <github repo url>
          e.git push

   Step 7: Setting up the trigger:
            To automate the entire process of building a docker image, pushing the image to google cloud registry and deploying the image to google cloud run
            We can set up triggers in google cloud build which will trigger the build, push and deploy process automatically when you push any changes to github
            For this process, we need to link our google cloud project with github repo

 Step 8: To Link gcloud and GitHub
      a. Cloudbuild.yaml is a file that contains a series of steps that need to be executed for auto build, push and deploy
      b. Open cloudbuild.yaml in your editor
      c.Edit the project-id, image and service name accordingly
      d.Run the following commands
      e.git add .
      f.git commit -m “update cloudbuild”
      g.git push
      h.Once pushed successfully, you can view the changes in github

Step 9: Creating a trigger
      a. Open https://console.cloud.google.com/
      b. Open the project you have created
      c.Open cloud build from the left navigation
      d.Click on Triggers from left navigation and Click on Create trigger
      e. Create a name to the trigger
      f. Add the source for the trigger, this will be linking to your github repository
      g. Link up your repository and give access for Google Cloud Build to access your repository if needed
      h. Once you’ve successfully created a trigger, give the appropriate permissions for successful trigger
      i. Go to cloud build settings and enable the following options
          1. Cloud run
          2.Service account
          3.Cloud build

Step 10: Run Trigger
      a. Visit cloud build from your navigation pane and Go to triggers
      b. You can see that your trigger is now listed
      c. Run the trigger by clicking on “Run” button and approve the permission
      d. Now you can view the entire process of build, push and deploy
      e.You’ve successfully completed setting up automatic builds/ CI/CD pipeline

Step 11 : Verify Your Automatic Builds
      a. Open the project in your editor. 
      b. Open the html file. Update the body of html page.
      c. Run the following commands on cmd
        1.git status
        2.git add .
        3.git commit -m “update html”
        4.git push 
      d. Open your cloud build
      e. Refresh the same url. You will see updated your builds something like this:
 



          










          







    
    