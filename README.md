# Kubernetes Tracker Notes

## PersistentVolumeClaim (Development)
    - db-service
        - db-service-pvc
    - mongo-service
        - mongo-service-pvc

## Deployments

    - main-service
        - main-service-depl
    - machine-learning-service
        - machine-learning-service-depl
    - auth-service
        - auth-service-depl
    - db-service (Development)
        - db-service-depl
    - mongo-service (Development)
        - mongo-service-depl

## Services

    - main-service
        - main-service-ci (Cluster IP)
    - machine-learning-service
        - machine-learning-service-ci (Cluster IP)
    - auth-service
        - auth-service-ci (Cluster IP)
    - db-service (Development)
        - db-service-np (NodePort)
        - db-service-ci (Cluster IP)
    - mongo-service (Development)
        - mongo-service-np (NodePort)
        - mongo-service-ci (Cluster IP)

## Ingress
    - ingress-srv

## How to Run

### production
```bash
# Setup main-service
kubectl apply -f production/deployments/main-service-depl.yml
kubectl apply -f production/services/main-service-ci.yml

# Setup machine-learning-service
kubectl apply -f production/deployments/machine-learning-service-depl.yml
kubectl apply -f production/services/machine-learning-service-ci.yml

# Setup auth-service
kubectl apply -f production/deployments/auth-service-depl.yml
kubectl apply -f production/services/auth-service-ci.yml

# Setup ingress-nginx controller
kubectl apply -f production/ingress/ingress-srv.yml
```

### Development
```bash
# Setup PostgreSQL database
kubectl apply -f development/persistent-volume-claim/db-service-pvc.yml
kubectl apply -f development/deployments/db-service-depl.yml
kubectl apply -f development/services/db-service-ci.yml
kubectl apply -f development/services/db-service-np.yml

# Setup MongoDB database
kubectl apply -f development/persistent-volume-claim/mongo-service-pvc.yml
kubectl apply -f development/deployments/mongo-service-depl.yml
kubectl apply -f development/services/mongo-service-ci.yml
kubectl apply -f development/services/mongo-service-np.yml

# Setup main-service
kubectl apply -f development/deployments/main-service-depl.yml
kubectl apply -f development/services/main-service-ci.yml

# Setup machine-learning-service
kubectl apply -f development/deployments/machine-learning-service-depl.yml
kubectl apply -f development/services/machine-learning-service-ci.yml

# Setup auth-service
kubectl apply -f development/deployments/auth-service-depl.yml
kubectl apply -f development/services/auth-service-ci.yml

# Setup ingress-nginx controller
kubectl apply -f development/ingress/ingress-srv.yml
```