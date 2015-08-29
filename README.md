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

# Using RunKeeper OAuth
Assuming you have obtained a valid RunKeeper OAuth token above, modify **/workers/tnj-runkeeper-worker/main/runners/get.js**  

In the **index** and **fitness_activities** functions, simply uncomment the lines below the TODO to integrate with RunKeeper.

# Design Rationale
The tnj-runners repo is simply a directory.json file that acts as a reference to other GitHub repos that form a meanr "solution". Think of it as the equivalent of a .Net solution file for a microservices architecture.

In the steps above, we installed the prerequisites for the meanr managed solution, and the **meanr build** command performs a checkout on all of the Git repos comprising the meanr solution and lays them out in this folder structure:

* /APIs: Web API's
* /clients: *Future Feature* Non-web clients
* /webclients: Web clients
* /workers: Workers

# Running the Application
If you simply want to see the app in action, execute **meanr run** at the topmost level of the meanr solution.

# Debugging the Application
The **meanr run** command was designed mainly for UI/UX resources to spin up the architecture with minimal pain. For backend developers, we recommend using WebStorm and setting up configurations for each Node application -- the API, the workers, and the webclient. You would then debug each application as you would a normal Node application in WebStorm.

# WebStorm Git Goodies (as tested in WebStorm 9 & 10)
1. Step 3 above and after WebStorm is done indexing the files, close out of WebStorm and reopen the package
2. WebStorm will notify you of "Unregistered VCS roots detected".  Click "Add roots"

![Unregistered vcs roots on WebStorm](http://i.imgur.com/oqd7rbR.png)

3. You will now notice each repo (API, workers, Web UI) are now on the lower right hand corner of WebStorm for Git integration

![VCS roots added to WebStorm](http://i.imgur.com/4LgpjHi.png)

