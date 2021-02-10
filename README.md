# kubernetes

## terms used in K8


## important commands



kubectl get nodes,namespaces,services,deployments,replicaset,pods,secrets,configMaps -o wide

kubectl create deployment

kubectl apply -f configFileName  --namespace=namespaceName

kubectl describe pods

kubectl logs podname

kubectl exec -it podnme command

## Why Namespaces

Consider this like a portlets within Portal container where every portet has its own
portlet-id . Every portlet has its own boundry but at the same time ,a portlet is allowed to interact with global objects. Also other portlets can access this portet with its portlet id. (but this statement is very generic and read the below to get more and more details)

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
      
      
  ## K8 Ingress
  
  ### to do 
  
  ## Helm
   `Package manager for k8 like npm, brew,apt. It packages YAML files and distributes
  and distributes them in public and private repositories`
  
 ### Helm charts
 
 `Bundle of YAML files`
 `Create your own Helm Charts with Helm`
 `Push them to Heml Repository`
 
 Common components like DB, redis,elk etc are commonly available so can be reused and
 this thr are publiv and private registeries for helm charts. 
 It is also a templating engine in which references can be defined in YAML files instead of
 actual values like
 >  name : {{ .Values.container.name }} where this Values object is referenced from a 
 values.yaml file. `Values object is either defined via YAML file or with --set flag in 
 command line`
 
 ### Helm chart Structure : Templating Feture
 
 myChart/
    Chart.yaml
    values.yaml
    charts/
    templates/
    ...
 `heml install <chartname>`
 `helm install --values=my-values.yaml <chartname>` 
 Important Note : Default values are picked up from values.yaml file but if you create a
 new yaml file lets say my-values.yaml and overide a value in this file, so overidden value 
 will be picked from my-values.yaml file and remaining values will be picked from Default 
 values.yaml file
 
 ### Release Management
 
 heml v.2 
 Uses a helm client(cli) and server(Tiller deployed in k8 cluster) to execute release
 management. Here Tiller stores the last state of configuration  and we can use commands like
 
 helm  install <chartname>
 helm  upgrade <chartname>
 helm  rollback <chartname>
    
 Problem with this architecture 
 
 - Tiller has too much power inside k8 cluster
 - Security issue
 
 So in heml 3 , it was removed
 
 
 ## K8 volumes
 
 
 
 
 
 
 
 
 
  
  
  
      
    
