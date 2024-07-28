<!-- @format -->

## Steps

- Containerization
  1. Understand the project flow like hoe the project works, on which port project is running etc
  2. Build multi stage docker file (that is goos practices)
- Kubernetes manifest
  1.  create deployment.yml script to ddeploy the project
  2.  create services.yml script
  3.  crate ingress.ymll services
  4.  deploy project on aws eks using below command
      - Prerequisites
        - kubectl (CLI for working woth kubernetes cluster)
        - awscli (CLI use to work with aws. You need to config your awscli using access key for this check docs)
        - ekscli (CLI use to work with eks)

      <h4> This is use to create EKS cluster <h4>
      ```eksctl create cluster --name demo-cluster --region <enter your region like ap-south-1>   ```
      <h4> This is use to delete EKS cluster <h4>
      ``` eksctl delete cluster --name demo-cluster --region <enter your region which u used above> ```
   5. 
