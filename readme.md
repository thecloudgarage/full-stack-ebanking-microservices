# online banking example

* Install nodejs on ubuntu 18.04
* The below will install 8.x version of nodejs (as the node modules used in the code require the same)
```
sudo su
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash
. ~/.nvm/nvm.sh
nvm install 8.9
node -e "console.log('Running Node.js ' + process.version)"
```
* Install docker on ubuntu 18.04
```
sudo su
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt-get install -y docker-ce
sudo usermod -aG docker ubuntu
```
* Clone this git repo and cd into frontend/ebanking and run npm install
* At this stage, we have node 8.x running, however installation of angular-cli needs node 10.x or above
* Once done run the below command it will upgrade node js to the latest version...
```
nvm install node --reinstall-packages-from=node
npm update
npm install -g @angular/cli --unsafe-perm=true
ng --version
```
* Now the node is upgraded to latest (as of writing 13.x) and the angular/cli is also installed

## Dockerization
* The docker images are already present on my dockerhub thecloudgarage and are respectively referenced in the k8s yaml templates
* However, in case we want to build these docker images again, then each of the service directory contains a dockerfile
* The maven docker plugin and along with maven wrapper enables us to create the jar and also the docker image for it
* To build the docker image run
```
./mvnw build 


Example project showcasing:

* SpringBoot microservices with reactive streams
* Kafka for messaging between microservices
* OAuth2 security
* Angular 5 front end
* All deployed in local kubernetes cluster (minikube)
* Finally Instructions on how to deploy on AWS

To use local docker daemon within minikube, `eval $(minikube docker-env)`

To run kafka locally and test producer and consumer on console:

* Run `bin/zookeeper-server-start.sh config/zookeeper.properties`
      `bin/kafka-server-start.sh config/server.properties`
      `bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning`
      `bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic baeldung --from-beginning`


The application comprises of following microservices:


1. CardsService
2. CashService
3. MortgageService
4. CustomerService

# Cash Service

To build docker image of cashservice
`docker build -t achalise/cash-service:0.0.1 .`

for gateway service using the dockerfile-maven-plugin, 
`./mvnw dockerfile:build`

Create a spring boot starter project with start.spring.io selecting reactive web and reactive MongoDB options.



Order to run:

1. zookeeper-services.yaml (`kubectl create -f kafka/zookeeper-services.yaml`)
2. zookeeper-cluster.yaml
3. kafka-service.yaml
4. kafka-cluster.yaml
5. mongo-cash.yaml
6. cash-service.yaml
7. gateway-service.yaml


uninstall all:
--------------
kubectl delete -f gateway/k8s/gateway-service.yaml

kubectl delete -f cash-service/k8s/cash-service.yaml
kubectl delete -f cash-service/k8s/mongo-cash.yaml

kubectl delete -f card-service/k8s/card-service.yaml 
kubectl delete -f card-service/k8s/mongo-card.yaml

kubectl delete -f kafka/kafka-cluster.yaml
kubectl delete -f kafka/kafka-service.yaml

kubectl delete -f kafka/zookeeper-cluster.yaml
kubectl delete -f kafka/zookeeper-services.yaml

install all:
------------
eval $(minikube docker-env)
kubectl create -f kafka/namespace-kafka.yaml
kubectl config set-context kafka --namespace=kafka-cluster --user=cluster-admin
kubectl config use-context kafka

kubectl create -f kafka/zookeeper-services.yaml
kubectl create -f kafka/zookeeper-cluster.yaml

kubectl create -f kafka/kafka-service.yaml 
kubectl create -f kafka/kafka-cluster.yaml

kubectl create -f cash-service/k8s/mongo-cash.yaml
kubectl create -f cash-service/k8s/cash-service.yaml 

kubectl create -f card-service/k8s/mongo-card.yaml
kubectl create -f card-service/k8s/card-service.yaml

kubectl create -f gateway/k8s/gateway-service.yaml

***** during minikube upgrade if there are issues, try
   - removing .minikube, .kube
   - upgrading virtual box - if not current
   - upgrading docker - if not current





## For the front end

- Install Angular cli globally
  npm install -g @angular/cli
- When there are multiple modules in the project, and using ng generate, specify module like this:
   ng generate component payment/from-account --module=app.module



