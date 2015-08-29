# tnj-runners
A sample mean-r managed solution for the tnj-runners microservices/service oriented architecture for Tampa Node.js on Friday, August 28, 2015!

# Prerequisites
1. Node.js 0.10+
2. Git
3. MongoDB installed locally
4. RabbitMQ server installed locally

# Recommended Tools
1. WebStorm
2. Robomongo
3. Postman

# Instructions
1. Clone this repo
2. npm install -g mean-r gulp node-sass
3. meanr build
4. meanr update
5. Establish the following environment variables, either through a WebStorm config or directly on your ~/.bash_profile (or System settings in Windows)
  * (Required) NODE_ENV
    * Value: Set it to "dev"
  * (Optional) RUNKEEPER_SEED_OAUTH
    * Value: Go to the [RunKeeper Developer Portal](http://runkeeper.com/partner) and establish an account. Then, obtain a valid OAuth token from RunKeeper through your favorite OAuth provider.

# meanr commands
Note that these commands need to be executed at the root of the meanr solution

* **meanr build**: If you've recently added new GitHub projects to the directory.json, this will pull them down into the directory structure. This is performed only intermittently as new projects get added to the meanr solution
* **meanr update**: This will pull the latest from your "dev" branches and execute npm installs for all API's and workers, and an npm install and bower install for the Web UI's. This is performed most frequently on a day-to-day basis. 
* **meanr run**: Intended for UI/UX or other resources who simply want to see the application in action. It will execute all the app.js files in the roots of each API and worker folder and execute **gulp** in each of the webclient and client folders.

# Using RunKeeper OAuth
Assuming you have obtained a valid RunKeeper OAuth token above, modify **/workers/tnj-runkeeper-worker/main/runners/get.js**  

In the **index** and **fitness_activities** functions, simply uncomment the lines below the TODO to integrate with RunKeeper. Restart tnj-main-worker to seed your local MongoDB's users collection with your OAuth token.

# Design Rationale
The tnj-runners repo is simply a directory.json file that acts as a reference to other GitHub repos that form a meanr "solution". Think of it as the equivalent of a .Net solution file for a microservices architecture.

In the steps above, we installed the prerequisites for the meanr managed solution, and the **meanr build** command performs a checkout on all of the Git repos comprising the meanr solution and lays them out in this folder structure:

* /APIs: Web API's
* /clients: *Future Feature* Non-web clients
* /webclients: Web clients
* /workers: Workers

# Debugging the Application
The **meanr run** command was designed mainly for UI/UX resources to spin up the architecture with minimal pain. For backend developers, we recommend using WebStorm and setting up configurations for each Node application -- the API, the workers, and the webclient. You would then debug each application as you would a normal Node application in WebStorm.

# WebStorm Git Goodies (as tested in WebStorm 9 & 10)

* After performing a **meanr build** and a **meanr update**, close out of WebStorm and reopen the package
* WebStorm will notify you of "Unregistered VCS roots detected".  Click "Add roots"

![Unregistered vcs roots on WebStorm](http://i.imgur.com/oqd7rbR.png)

* You will now notice each repo (API, workers, Web UI) are now on the lower right hand corner of WebStorm for Git integration

![VCS roots added to WebStorm](http://i.imgur.com/4LgpjHi.png)

