# Prometheus & Grafana for Kubernetes Monitoring 
Prometheus &amp; Grafana for Kubernetes Monitoring 

#### Step # 1 seprate Namespace needed ####

     mansoor@LARC-MANSOOR ~ $ kubectl apply -f namespace.yaml 
     namespace/monitoring created

#### Check namespace which created for prometheus ####
     mansoor@LARC-MANSOOR ~ $ kubectl get namespaces|grep monitoring
     monitoring    Active   2m10s
     
#### Steps # 2 Create Cluster RBAC Rule. ####
     mansoor@LARC-MANSOOR ~ $ kubectl apply -f clusterRole.yml

#### Step # 3 Create ConfigMap for Prometehus 
     mansoor@LARC-MANSOOR ~ $ kubectl apply -f prometheus-config-map.yml

#### Step # 4 Create deployment of Prometheus #### 
     mansoor@LARC-MANSOOR ~ $ kubectl apply -f prometheus-deployment.yml
    
#### Check Prometheus deployment 
     mansoor@LARC-MANSOOR ~/Documents/prometheus $ kubectl get pods -n monitoring |grep prometheus
     prometheus-deployment-766fcbb548-p68sz   1/1     Running   0          135m

#### Step # 5 Create Grafana deployment ####
     mansoor@LARC-MANSOOR ~ $ kubectl apply -f grafana-deployment.yml
     deployment.extensions/grafana created
     
#### Check Grafana deployment #### 
     mansoor@LARC-MANSOOR ~ $ kubectl get deployment -n monitoring |grep grafana
     grafana                 1         1         1            1           128m

#### Check Grafana PODs
     mansoor@LARC-MANSOOR ~ $ kubectl get pods -n monitoring |grep grafana 
     grafana-58c869ccc5-kmr8h                 1/1     Running   0          129m
     
#### Step # 6 Create Grafana Service #### 
     mansoor@LARC-MANSOOR ~ $ kubectl apply -f grafana-service.yml
     service/grafana-service created

#### Check Grafana Service #### 
     mansoor@LARC-MANSOOR ~ $ kubectl get svc -n monitoring |grep grafana
     grafana-service      NodePort   10.64.8.172   <none>        3000:30544/TCP   130m
 
 #### Step # 7 Access Grafana Dashboard
 In order to acces Grafana Dashboard need to port forward 
     
     mansoor@LARC-MANSOOR ~ $ kubectl port-forward $(kubectl get pods -n monitoring |awk '{print $1}' |grep grafana) 3000:3000 -n monitoring




