# DevOps_Task_5 (Prometheus + Grafana + Kubernetes + YML)

## Project purpose:
Integrate Prometheus and Grafana and perform in following way:

1. Deploy them as pods on top of Kubernetes by creating resources Deployment, ReplicaSet, Pods or Services
2. And make their data to be remain persistent 
3. And both of them should be exposed to outside world

## Let's see step by step how to achieve this:

#### Step - 1 - I have used various YML files to create all resources on top of kubernetes.
For prometheus- 1) deployment - prometheus-deploy.yml 2) service - prometheus-service.yml  4) configMap - prom-config-map.yml.
For grafana-    1) deployment - grafana-deploy.yml 2) service - grafana-service.yml 3) 
(please refer them for detail understanding)

#### Step - 2 - I have used automatic PVC - persistent volume claim to make their data to be remain persistent.
1) For prometheus - prometheus-pvc-claim.yml 2)  For grafana- grafana-pvc-claim.yml

(Here we can also use manual persistent volume instead of automatic). 
(Note- I have used configMap for inserting some data or configuration file for prometheus at the time of launching of pods. The file is known as prometheus.yml)

#### Step - 3 - I have used kustomization concept to run all resources in one go by using ```kustomization.yml``` file and below commnad. This file includes all yml files.
```
kubectl apply -k .
```
(Note - here "." means we are running this command from prsent directory where kustomization.yml file lies) (please refer this snap of output after running this command - [command output](https://github.com/krushnakant241/deveops_proj_5/blob/master/Task-5%20Snapshots/kubectl%20kustomization%20run%20command.JPG)).

#### Step - 4 - Now, I have aleady exposed port of Node for prometheus(30001) and grafana(30002) in service files so we can see output using below URLs.
For prometheus - http://192.168.99.100:30001  and for grafana - http://192.168.99.100:30002 (initial username- admin and password- admin).
Please refer the below snapshots for both URLs.
1) [Prometheus targets](https://github.com/krushnakant241/deveops_proj_5/blob/master/Task-5%20Snapshots/prometheus%20targets.JPG)
2) [PromQL output](https://github.com/krushnakant241/deveops_proj_5/blob/master/Task-5%20Snapshots/PromQL%20output.JPG)
3) [Grafana login](https://github.com/krushnakant241/deveops_proj_5/blob/master/Task-5%20Snapshots/Grafana%20login.JPG)
4) [Grafana output](https://github.com/krushnakant241/deveops_proj_5/blob/master/Task-5%20Snapshots/Grafana%20output.JPG)
