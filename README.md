circleci badge :
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/DRMagdySalem/kube_project/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/DRMagdySalem/kube_project/tree/main)

in this Project ; our target was to operationalize machine learning microservice using docker and kubernetes .
let's get a walk through the project and the steps we passed : 

1) we started by ceating an environment and setting up this environment with all needed dependencies that we could need though our path .
used command: 
-command: | python3 -m venv venv  : create virtual environment 
-source ~/.devops/bin/activate : activate the virtual environment
-make install : install the needed dependencies listed in the "requirements.txt" file 
2) then we used linting facilities of pylint and hadolint to rate our code and check for errors .
used command : Make Lint 
3) after completing the "run_docker.sh" and "app.py"  files we ran the docker script through :./run_docker.sh to build the docker image and run the built image 
files: 
run_docker.sh : contains the commands for building and running the needed docker image 
app.py : carry the logig needed for predictions API operation which is the project target .
4) after running the image we used the ./make_prediction.sh script to test the logic and the functionality of the app and the built image .
we saved also an output for the prediction process in : output_txt_files/docker_out.txt 

5) after successfull build we moved to the step of publishing the image to docker hub through ./upload_docker.sh after adding the tag , 
the authentication is done through my terminal not to expose the user and passowrd but you can find the image on : 
https://hub.docker.com/repository/docker/magdysalemm/kube_proj

6) after that we moved to creating a kubernetes cluster using " minikube start " command after installing minikube and kubectl  .
7) then we used the run_kubernetes.sh script to Run the Docker Hub container with kubernetes and Forward the container port to a host .
8) and we tested again the prediction through the make_prediction script and saved the output to : output_txt_files/kubernetes_out.txt
9) we also created the .circleci directory carrying the config.yml file to test the build though circleci and passed as in the following badge :

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/DRMagdySalem/kube_project/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/DRMagdySalem/kube_project/tree/main)
