# Brief

The project enumerates the steps to undertake to deploy an ecommerce application on Google Cloud Platform using Kubernetes service.
The code is persisted on MongoDB.
The ecommerce application has front end and backend codes implying there are two pods deployed on kubernetes i.e frontend and backend.

The choice of GCP selected is asia east 2 which did not have cluster disk persistency limits when using the free tier.


# Requirements
Make sure that you have the following installed:
- [node](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04) 
- npm 
- [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)
- Docker Installation
- A Google Cloud Account with sufficient credits to run Kubernetes.

# Running Locally Setup Steps
## Navigate to the Client Folder 
 `cd client`

## Run the folllowing command to install the dependencies 
 `npm install`

## Run the folllowing to start the app
 `npm start`

## Open a new terminal and run the same commands in the backend folder
 `cd ../backend`

 `npm install`

 `npm start`

 ## Test the portal by navigating to home page and adding a product
 
 # Running on Docker
- Navigate to your github account and fork https://github.com/kennedynjoroge/K8s_Ochestration_GCP/
- Clone the code to pull the repository to your local directory
- Navigate to the application directory K8s_Ochestration_GCP
- Under backend directory, specify the MongoDB database configurations on the server.js file.
- Run docker compose to install the image and create a container : sudo docker compose up --build
- Note: The backend port as is 3001 and frontend port is 3000. You can change these if there are any conflicts.
- Push images to docker hub : sudo docker compose push
- Test the portal by navigating to home page and adding a product
 
# Deployment on GCP
- Create a GCP account if it doesn't exist.
- Log into the cloud project and enable billing
- Create a kubernetes cluster by setting region and creating the container cluster.
gcloud config set compute/zone asia-east2-a (created in Asia as it doesn’t	have the 600GB persistent SSD disk limit

gcloud container clusters create yolo-cluster \
  --machine-type e2-small \
  --num-nodes 3 \
  --scopes "https://www.googleapis.com/auth/projecthosting,storage-rw"
 
 - Deploy the app using the kubectl commands specify the image name as pushed on Docker Hub
