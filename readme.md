http://jenkins-eks.premdesigns.in/job/jquery-eks/
admin
Login@123

aws ecr get-login-password --region us-east-2 | sudo docker login --username AWS --password-stdin 060920346106.dkr.ecr.us-east-2.amazonaws.com

sudo docker build -t 060920346106.dkr.ecr.us-east-2.amazonaws.com/jquery-eks:$BUILD_NUMBER .
sudo docker push 060920346106.dkr.ecr.us-east-2.amazonaws.com/jquery-eks:$BUILD_NUMBER 



Ingress-Controller --> Loadbalancer

Namespace
Deployment
Service
Ingress --path / host