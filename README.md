

<h2>
  Cloud Formation
</h2>

eksctl create cluster -f cluster.yaml



<h2>
  Deploy Image Initially
</h2>

***Deploys the image***: kubectl apply -f deploy.yaml

***Creates the load balancer:*** kubectl apply -f loadBalancer.yaml



<h2>
  Rolling Deployment
</h2>

***Changing the version number each time and setting the new image will allow it to update the deployment.***

kubectl set image deployments/simple-node-app-deployment simple-node-app=850598408435.dkr.ecr.us-west-2.amazonaws.com/simple-node-app:v2



