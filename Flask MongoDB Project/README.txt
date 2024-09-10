 Prerequisite 
 ------------

      Docker - for image building and pushing.
      Minikube - a local kubernetes cluster for testing and deployment.


 Deployment Architecture
 -----------------------

    Secret file:
      secrets.yaml - for storing the mongodb credentials.

    Persistent Volumes:
      pv.yaml - for configuring persistent storage. 
      pvc.yaml - for configuring durable storage.

    MongoDB :     
      mongodb-stateful.yaml - for managing mongodb pods with pv and pvc.
      mongodb-services.yaml - provides direct access to MongoDB pods.

    Flask Application   
      app-deployment.yaml - for deploying flask application.
      app-service.yaml - for exposing the application through ClusterIP.


  Minikube
  ---------

    minikube start - to start the local kubernetes cluster.


  Resources Creation
  -------------------

    #create all the resourcres using "Kubectl apply -f <name>"
    kubectl apply -f secrets.yaml
    kubectl apply -f pv.yaml
    kubectl apply -f pvc.yaml
    kubectl apply -f mongodb-stateful.yaml
    kubectl apply -f mongodb-services.yaml
    kubectl apply -f app-deployment.yaml
    kubectl apply -f app-service.yaml
    kubectl apply -f hpa.yaml