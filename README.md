checkbox deployment

- created playbook keyDroplet.yml file to create droplets and updating inventory files.
- jenkins.yml will be run for jenkins set up on the instances mentioned in jenkins-inventory file.
- jenkins.yml will install jenkins, create a build job and run the build job for checkbox. 
- This will run cbDeploy.yml on instances mentioned on checkbox-inventory file and will clone the checkbox repo and install all the dependencies on the deployment instances. And finally it wall start server.js to start the checkbox up and running.
- Git hooks will be set on github for the jenkins server. Every time, the git push is done, it will hit the jenkins webhook url which will trigger the build of same job again. 
- This time the same cbDeploy.yml will be run but it will check if the checkbox is already deployed before and it will not download dependencies and do installtions of requirements. It will just clone the latest code from the git repo and restart the services like nginx and forever and finally restart server.js to deploy the checkbox's latest code on deployment instances.