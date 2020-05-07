1. It decouples configuration from PODs and components. So it is easier to manage and change.
2. It stores the data as KEY-VALUE pair.
3. If you're passing any configuration in files then the name of the file is going to be the key and content of that file is going to be the value. You can also pass key value pairs straight from the command line or as a environment variable. 
4. So the help of config maps in K8s you can manage configuration of containers but there aren't any sensitive data as part of this configuration. Then use secrets.
5. You must create configmap before referencing it in a POD spec.
6. Syntax
    -- kubectl create configmap <map-name> <data-source>
    Data-source can be directory/file or literal value.

For directory/file use  "--from-file"
For literal use  "--from-literal"  

create a config folder with some configuration inside it.
Create configmap by following command from directory config
kubectl create configmap game-config --from-file=02_configMap/01_configMap/config/

Create configmap by following command from file from a directory
kubectl create configmap game-config-file --from-file=02_configMap/01_configMap/config/ui.properties

#get details
kubectl get configmap
kubectl describe configmaps game-config
#In yaml format
kubectl get configmap game-config -o yaml
#delete the configuration
kubectl delete configmap game-config


Accesing configMaps in PODs:

1. Create a POD manifestfile
2. Create a configmap and reference it to pod spec volume section
3. Key is nothing but a file name used when creating the volume
4. Path is target location where data is present inside the POD.

volumeMounts : 
mountPath where the volume mounted on and the “name” of the volume which is “”config””  name in spec.volumes.

ConfigMap using literal value :
kubectl create configmap <name> - - from-literal=specical.key=value
Eg
 — kubectl create configmap gyan-lit-conf --from-literal=special.key=k8s

kubectl get configmap gyan-lit-conf -o yaml

apiVersion: v1
data:
  special.key: k8s
kind: ConfigMap
metadata:
  creationTimestamp: "2020-05-05T15:33:14Z"
  name: gyan-lit-conf
  namespace: default
  resourceVersion: "945108"
  selfLink: /api/v1/namespaces/default/configmaps/gyan-lit-conf
  uid: bc113b00-8ee5-11ea-84fc-42010af00032

*******************************************************************************************************
When we reference the config map inside the POD, we use the key (here special.key)
2 ways to reference configmap inside the POD, by volume mount or by env variable.
*******************************************************************************************************
