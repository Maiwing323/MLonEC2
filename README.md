## Machine Learning On EC2

The dataset to train my model is MNIST handwritten digits database. Train the CNN model to recognize the number in each picture. 

##### Task 1. Build a CNN model runs on a single machine using PyTorch

Step 1: Write the python code, import libraries

Step 2: Move CNNModel.py from local to EC2 by command: ```scp -i```

Step 3:  Connect to EC2 by command: ```ssh -i ~/Downloads/"replace-to-your-pem-key" ubuntu@ec2XXXXXX.compute-1.amazonaws.com```

Step 4: Verify the file by command: ```ls```

You can get:CNNModel.py  None  README

Step 5: Create virtual environment “pytorch” and active it

Step 5a: Install python3 by command: ```sudo apt-get install python3-venv```
Step 5b: Creates a new virtual environment named "pytorch" for Python 3 by command: ```python3 -m venv pytorch```
Step 5c: Active it by command: ```source pytorch/bin/activate```
Step 6: Install torchvision module by command: ```pip install torchvision```
Step 7: Install matplotlib module by command: ```pip install matplotlib```
Step 8: Run the python code by command: ```python3 CNNModel.py```

##### Task 2: Launched in a distributed way with data parallelism. 
Step 1: Stop the instance then go to instance settings and change
instance type to c5.xlarge which is 4vCPU 8G Memory. Then runs the
instance.
Step 2:Connect to EC2 in terminal by command: ```ssh -i```
~/Downloads/"replace-to-your-pem-key" ubuntu@ec2-replace-to-your-own-one.compute-1.amazonaws.com
Step 3: Verify file in this instance by command: ```ls```
Step 4: Install docker by command: ```sudo apt install docker.io```
Step 5: log in to Amazon ECR
step a: Configure your EC2 instance with your AWS credentials
step b. Log in to Amazon ECR by command: $(aws ecr get-login --region
us-east-1 --no-include-email --registry-ids XXXXX-XXXXXXX)
Step 6: install minikube and create 3 nodes, but need to install minikube , curl,
Need to follow the below steps:
```minikube start --nodes 3```
```sudo apt-get update```
Step 6a: ```sudo apt-get install curl```
Step 6b: Download and install minikube:```curl -LO```
Step 6c: install minikube binary: ```sudo install minikube-linux-amd64/usr/local/bin/minikube```
Step 6d: Verify the minikube version by command: minikube version ```minikube version```
Step 6e: Start docker by command: sudo service docker restart ```minikube start --nodes 3```
Step 7: Verify the node by command: ```minikube profile list```
NOTE: not working by using command: ```kubectl get node```
Step 8: Verify file by command: ```ls```
Step 9: go to pytorch by command: ```source pytorch/bin/activate```
Step 10: Runs the code by command: ```python3 CNNModel.py```
Done!



      

