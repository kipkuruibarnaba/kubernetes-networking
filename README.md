# kubernetes-volumes
For adding volumes in kubetes, PersistentVolume and PersistentVolumeClaim

#Pre-requisites 

1. Install kubernetes with minikube and Install kubectl
2. minikube start 

# Minikubes commands
 kubectl version --client
 minikube delete
 minikube status
 minikube dashboard
 minikube dashboard --url

 3. Build and push images to docker hub.
    
    # build frontend
    docker build -t frontend-api .
    docker tag frontend-api barnmutahi/frontend-api && docker push barnmutahi/frontend-api

    # build task-api
    docker build -t task-api .
    docker tag task-api barnmutahi/task-api && docker push barnmutahi/task-api

    # build users-api
    docker build -t user-api .
    docker tag user-api barnmutahi/user-api && docker push barnmutahi/user-api

    # build auth-api
    docker build -t auth-api .
    docker tag auth-api barnmutahi/auth-api && docker push barnmutahi/auth-api


    <!-- # build frontend
    docker build -t kube-networking-frontend-app .
    docker tag kube-networking-frontend-app barnmutahi/kube-networking-frontend-app && docker push barnmutahi/kube-networking-frontend-app

    # build tasks-api
    docker build -t kube-networking-tasks-app .
    docker tag kube-networking-tasks-app barnmutahi/kube-networking-tasks-app && docker push barnmutahi/kube-networking-tasks-app

    # build users-api
    docker build -t kube-networking-users-app .
    docker tag kube-networking-users-app barnmutahi/kube-networking-users-app && docker push barnmutahi/kube-networking-users-app

    # build auth-api
    docker build -t kube-networking-auth-app .
    docker tag kube-networking-auth-app barnmutahi/kube-networking-auth-app && docker push barnmutahi/kube-networking-auth-app -->


 4. Apply the yaml files inside the kubernetes folder i.e
     
     -> kubectl apply -f=auth-deployment.yaml -f=auth-service.yaml -f=environment.yaml -f=frontend-deployment.yaml -f=frontend-service.yaml -f=host-pv.yaml -f=host-pvc.yaml -f=tasks-deployment.yaml -f=tasks-service.yaml -f=users-deployment.yaml -f=users-service.yaml

 5. Start the service that will be exposed outside the cluster.The one that interact with users outside
     ->  minikube service users-service tasks-service frontend-service

      This applies for minikube, If you are using Kubernetes provided by cloud will not need to start the service, ie EKS 
 6. Now you can acces your cluster     

     # Test Via postman 
    post-> http://127.0.0.1:1224/story
    get-> http://127.0.0.1:1224/story
    get-> http://127.0.0.1:1224/error

     {
   "text":"my text 10" 
      }
