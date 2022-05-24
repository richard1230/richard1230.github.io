---
title: Deploy Project With buildpacks to Heroku and Github
date: 29-09-2021
categories:
- Buildpacks
tags:
- front end
---

### Deploy to Heroku

1. Go to the [Heroku](https://dashboard.heroku.com) website, if you don't have a account, register one first.

2. Open Command Line, enter ```heroku login```, hit any button, when you see ```heroku: Press any key to open up the browser to login or q to exit:```, it will jump to the webpage where it ask us to ```Log in``` Heroku.

3. You may have to manually enter your username and password for Heroku in your command line if browser in your command line browser window does not open.

4. Create a Heroku Project Command:
    - ```heroku create spending-log --buildpack mars/create-react-app```.
    - This ***[create-react-app-buildpack](https://github.com/mars/create-react-app-buildpack)*** is also great because it will also use the production build of our react-app for the deployment.

5. Here is the buildpacks command:
  ```
  COMMANDS
    buildpacks:add       add new app buildpack, inserting into list of buildpacks if necessary
    buildpacks:clear     clear all buildpacks set on the app
    buildpacks:info      fetch info about a buildpack
    buildpacks:remove    remove a buildpack set on the app
    buildpacks:search    search for buildpacks
    buildpacks:set
    buildpacks:versions  list versions of a buildpack
  ```
6. ```git add .```
7. ```git commit -m "fix all the problem"```
8. ```git push heroku master```


### Deploy to Github
1. Run ```yarn build``` to build the project, you will get a build folder, this is for displaying the content in a independent website.
2. Check current project the ```.gitignore```  file, to make sure we exclude the ```build``` folder
3. Run ```yarn global add serve```
4. Run ```serve -s build``` You will learn more about deployment from this webpage: [Deployment](https://create-react-app.dev/docs/deployment/)
5. Create a new repository in github to store the production of this project.
6. Go to ***build*** folder
7. Run ```git init```
8. Run ```git add .```
9. Run ```git commit -m "deploy spending log project to github"```
10. Run ```git remote add origin git@github.com:Yueran-Yu/spending-log-app.git ```
11. Run ```git push --set-upstream origin master```
12. Go to ```package.json```, add ```"homepage" : "."``` package.json at the top.



### The custom deploy script: **deploy.sh**
1. create a file ***deploy.sh*** under the folder ***scripts***
2. Add the [bash shebang](https://linuxize.com/post/bash-shebang/) ***#!/usr/bin/env bash***

```
#!/usr/bin/env bash
yarn build &&
cd build &&
git init &&
git add . &&
git commit -m 'deploy' &&
git remote add origin git@github.com/ &&
git push -u origin master -f &&
cd -
```
3. These are the executable script example in the ```deploy.sh``` file.
4. Final step: add ```"deploy: "sh scripts/deploy.sh``` to the ```package.json```  file.
5. Run ```yarn deploy```, it will automatically deploy the script as you provided.


