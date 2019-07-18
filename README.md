# Prometheus & Grafana for Kubernetes Monitoring 
Prometheus &amp; Grafana for Kubernetes Monitoring 

#### Step # 1 seprate Namespace needed ####
mansoor@LARC-MANSOOR ~ $ vim namespace.yaml

    $ {
    $   "kind": "Namespace",
    $   "apiVersion": "v1",
    $     "metadata": {
    $       "name": "monitoring",
    $       "labels": {
    $         "name": "monitoring"
    $       }
    $     }
    $   }


#### Official GoAccess Debian & Ubuntu repository ####

    $ echo "deb http://deb.goaccess.io $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list
    $ wget -O - http://deb.goaccess.io/gnugpg.key | sudo apt-key add -
    $ sudo apt-get update
    $ sudo apt-get install goaccess

