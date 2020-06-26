<h1>
  DevOps Capstone 
</h1>


<h3>
  Deploying a simple node application.
</h3>

In this project  I applied the skills and knowledge which were developed throughout the Cloud DevOps Nanodegree program. These include:

- Working in AWS
- Using Jenkins to implement Continuous Integration and Continuous Deployment
-  Building pipelines 
- Working with Ansible and CloudFormation to deploy clusters 
- Building Kubernetes clusters 
- Building Docker containers in pipelines

---



<h4>
  Cloud Formation
</h4>

eksctl create cluster -f cluster.yaml



---



<h4>
  Deploy Image Initially
</h4>

***Deploys the image***: 

- kubectl apply -f deploy.yaml

***Creates the load balancer:*** 

- kubectl apply -f loadBalancer.yaml



---



<h4>
  Rolling Deployment
</h4>

***Changing the version number each time and setting the new image will allow it to update the deployment image.** 

- kubectl set image deployments/simple-node-app-deployment simple-node-app=850598408435.dkr.ecr.us-west-2.amazonaws.com/simple-node-app:v2



---



