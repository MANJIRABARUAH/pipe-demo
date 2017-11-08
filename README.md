# Heroku pipe demo with environtment vars

This project will demonstrate Heroku pipelines with config vars (environment variables).
After following this demo, you will have a project with multiple environments. Every environment will be the same in source code, but different in appearance, due to environment variables.

## Getting Started on Heroku

You can set up this demo without building it locally.

### Prerequisites

* Free Github account
* Free Heroku account
* At least two available projects in Heroku (Free account comes with 5 available projects)

### Steps

* Fork this Repo
* Log in to Heroku
* In the Heroku Dashboard, click New > Create new pipeline
  * Choose a name
  * Connect to github
  * Choose the forked github repo
* Your pipe is created, but needs apps. Create one in staging. Click Add App > Create new app. A new window opens
  * (optional) Choose a unique name
  * Click Create App
* Do the same for an app in the production stage.
* (optional) you can add a development stage by adding an app and transferring it to development stage (click the options button on the app). Development stage does not exist yet, but will be added automatically.
* Apps are created, lets add automatic deploys. Only the first app in your pipeline needs this. You don't want production to automatically build on every change.
  * Click on the name of the app in your first stage
  * Click tab Deploy
  * Scroll to Automatic deploys and click Enable Automatic Deploys

Lets add environment variables! (do this for every app in your stages)
* Click the name of the app (within the pipeline)
* Go to Settings tab
* Click Reveal Config Vars (list should be empty)
* Add a variable ENV_COLOR with a color name of your choosing (color hash codes should work as well)
* Add a variable ENV_NAME with a name for the stage (I used Development, Acceptance and Production for my stages)

Lets deploy!
* On the app that is connected to github, click the arrows (options)
* Click Deploy a branch
* Choose master and click Deploy
* When it is done deploying, click options again and click Open app in browser. It should have the color and text of your choosing

Lets promote! By promoting a stage, Heroku copies the build from one app to the next.
* On the active app, click Promote to Production
* When done, you can open the app and it should have a different color and text!

Something to consider:
* I hardcoded the links to my environments in the app.component.html. You can change the links to represent your stages. The format is: <appname>.herokuapp.com
* The variables I used (ENV_COLOR and ENV_Name) are needed for this project. You can choose your own name and values for your own project.
