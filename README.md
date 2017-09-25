# Kafka in Kubernetes
Running Kafka brokers, consumers, and producers in Kubernetes for prototyping and exploration.  This setup spins up a single broker Confluent Kafka broker using the Confluent packaged docker containers. 

This configuration uses local `emptyDir` volumes, which survive for the life of a pod.  When a pod is destroyed or recreated all data will be lost and will need to be re-created or reloaded.
 
## Objective
As a person interested in Confluent Kafka and kubernetes
I want to spin up and tear down kafka environments in kubernetes
So that I can test out features and functionality.

## Assumptions
* Built and tested on minikube, which includes the k8s DNS service
* `kafka` namespace exists in the k8s cluster 
 
## Services
* kafka-01: kafka broker service (name needs to match the hostname assigned in the kafka-01 deployment descriptor)
* zookeeper-01: zookeeper host for the broker
* control-center:  Confluent Kafka Enterprise control center

## Deployments
* kafka-01: single kafka broker instance.  Deployment descriptor `hard codes` the container instance hostname to `kafka-01`
* zookeeper-01:  single zookeeper instance
* control-center: control center instance

## TODO
* Control Center only partially works.  The broker and topic stats are not yet reporting through to the control center

## Disclaimer
This setup is intended for personal non-production use.
