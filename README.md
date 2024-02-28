# Kafka Simple Server Deployment
## How to install on your local machine?
### Install Docker for Desktop and enable Kubernetes
If you want to install in your local machine, you can do it by using __Docker for Desktop__ and enable __Kubernetes__.
![Docker Settings/Kubernetes/Enable Kubernetes](/Readme/docker_desktop_kubernetes.png)

### Import deployment files to your kubernetes
Then just apply both deployment files to kubernetes.
![open terminal](/Readme/open_terminal.png)

#### Deploy zookeeper pod
`kubectl apply -f .\deploy-zookeeper.yml`

#### Deploy confluentic-cp-kafka pod
`kubectl apply -f .\deploy-cp-kafka.yml`

#### Check if pods were created and running
`kubectl get pods`

It should print something like the following:
```
NAME                                           READY   STATUS    RESTARTS   AGE
testing-kafka-server-deploy-57f47cdb86-qxxdj   1/1     Running   0          8s
zookeeper-deploy-69bf9964dd-9lpr9              1/1     Running   0          17s
```

#### Check if services were successfully created
`kubectl get services`

It should print something like the following:
```
NAME              TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
kakfa-server-lb   LoadBalancer   10.110.217.247   localhost     9092:32119/TCP   5h59m
kubernetes        ClusterIP      10.96.0.1        <none>        443/TCP          2d1h
zookeeper-svc     ClusterIP      10.99.58.0       <none>        2181/TCP         5h50m
```

At this point you should have a kafka server available on your local machine and accessible on **127.0.0.1:9092**

## Credits
This work was based on this article: [A Practical Guide to Apache Kafka with Node.js: Code Examples](https://medium.com/@ketanpradhan/a-practical-guide-to-apache-kafka-with-node-js-code-examples-329cc65be502)
