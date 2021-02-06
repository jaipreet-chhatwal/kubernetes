# kubernetes

## terms used in K8


## important commands



kubectl get nodes,namespaces,services,deployments,replicaset,pods,secrets,configMaps -o wide

kubectl create deployment

kubectl apply -f configFileName 

kubectl describe pods

kubectl logs podname

kubectl exec -it podnme command

## Why Namespaces

1. `can be used to group similar applications`
2. `Conflicts : Many teams , same application`
3. `Resource Sharing : Staging and Development aka different environments `
4. `Access and Resource Limits on Namespaces `

### important note 
1. `you cant access most resources from another Namespaces`
    example of resources which cannot be shared are but not limited to configMap, secrets
    Resources which can be shared are services. example for excessing a service deployed in 
    another namespace ex application in namespace 1 want to access database service in 
    another namespace then the application in namespace 1 should refer like
    serviceName.namespace
    
2. `There are certain components which cant be created in namespace i.e. which are global
     cluster,cant isolate them example volumes,nodek`
     
     kubectl api-resources --namespaced=false (resources which are not namespaces
     aka global )
     kubectl api-resources --namespaced=true (resources which can stay in boundaries of 
     namespaces or can be confined in namespaces)
 
      `when components are created in a cluster without a namespace ,components are
      created in `default` namespace`
    
