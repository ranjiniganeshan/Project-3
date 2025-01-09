```
aws eks update-kubeconfig --region us-east-2 --name education-eks-ifedZHyO
```

The ec2 nodes require cloudwatch admin access.

add cloudwatch admin acccess to IAM role

Step 1: 
create namespace
kubectl apply -f https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/main/k8s-deployment-manifest-templates/deployment-mode/daemonset/container-insights-monitoring/cloudwatch-namespace.yaml

Step 2:

Set up a service account in the amazon-cloudwatch namespace.

kubectl apply -f https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/main/k8s-deployment-manifest-templates/deployment-mode/daemonset/container-insights-monitoring/cwagent/cwagent-serviceaccount.yaml



Step 3

Download and edit the ConfigMap YAML file to specify your cluster name.
 kubectl apply -f cwagentconfig.yaml

Step 4: 

kubectl apply -f https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/main/k8s-deployment-manifest-templates/deployment-mode/daemonset/container-insights-monitoring/cwagent/cwagent-daemonset.yaml


step 5: kubectl get pods -n amazon-cloudwatch
