# Software Quality Project Deliverable 3: Deploying using Google Kubernetes Engine
Group 18:
- [Tahmid Chowdhury](https://github.com/tahmid-chowdhury) - 100822671

Due: March 1st, 2024

## YAML Files
binarycalculator-deploy.yaml:
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: binarycalculator-deployment
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: binarycalc
    template:
      metadata:
        labels:
          app: binarycalc
      spec:
        containers:
          - image: northamerica-northeast2-docker.pkg.dev/feisty-tempest-415720/sofe3980u/binarycalculator
            name: binarycalculator
            ports:
              - containerPort: 8080
                name: binarycalc
  ```
binarycalculator-service.yaml:
  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: binarycalculator-service
  spec:
    type: LoadBalancer
    ports:
      - port: 8080
    selector:
      app: binarycalc
  ```
