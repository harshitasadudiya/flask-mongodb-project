 Prerequisite 
 ------------

      Docker(for image building and pushing)
      Minikube(a local kubernetes cluster for testing and deployment)
      Kubectl(Kubernetes command-line tool)


 Deployment Architecture
 -----------------------

    Secret:
      secrets.yaml - Stores MongoDB credentials.

    Persistent Volumes:
      pv.yaml - Configures persistent storage. 
      pvc.yaml - Claims durable storage.

    MongoDB:     
      mongodb-stateful.yaml - Manages MongoDB pods with PV and PVC.
      mongodb-services.yaml - Provides direct access to MongoDB pods.

    Flask Application:   
      app-deployment.yaml - Deploys Flask application.
      app-service.yaml - Exposes the application through ClusterIP.

     Autoscaling:
      hpa.yaml - Configures Horizontal Pod Autoscaler for the Flask app


 Deployment Steps
 -----------------
    Start Minikube:
      minikube start
    Build and Push Docker Images:
      docker build -t harshitasadudiya/flask-monngodb-app .
      docker push harshitasadudiya/flask-mongodb-app:latest
    Create Kubernetes Resources:
      #create all the resourcres using "Kubectl apply -f <name>"
      kubectl apply -f secrets.yaml
      kubectl apply -f pv.yaml
      kubectl apply -f pvc.yaml
      kubectl apply -f mongodb-stateful.yaml
      kubectl apply -f mongodb-services.yaml
      kubectl apply -f app-deployment.yaml
      kubectl apply -f app-service.yaml
      kubectl apply -f hpa.yaml

 Verify Deplyment:
------------------
    Kubectl get pods
    kubectl get services
    kubectl get pv,pvc
    kubectl get hpa
