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
