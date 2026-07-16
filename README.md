# nodeselector 
* first we add labels to node using below command 
kubectl label nodes <node-name> <key>=<value>
ex: kubectl label nodes ip-192-168-15-26.ec2.internal disk=ssd 
    kubectl label nodes ip-192-168-17-180.ec2.internal disk=ssd  
    
<!-- 
apiVersion: v1
kind: Pod
metadata:
  name: node-selector
  labels:
    env: test
spec:
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: Always #upadted images pulled 
  nodeSelector: #select particular node name or ip
    # disktype: ssd
    disk: ssd -->

 the labels does not match the pod is pedning reamin 

 # taints and toolerance :

 * kubectl taint nodes <node-name> <key>=<value>:<effect>
 ex: kubectl taint nodes ip-192-168-15-26.ec2.internal env=prod:NoSchedule
     kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoSchedule 
      kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoExecute
      kubectl taint nodes ip-192-168-17-180.ec2.internal key1=value1:NoSchedule

     <key>->key1 ,<vaule>->vaule1 
     env->key 
     value->prod 
next tainte the node using labels 
 kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoSchedule 
 ->the pod is pedning beacuse we taint that node but we select the node selector 
 Noschedule->not scheduling new pods 
 Noexcute->evicted pods 



