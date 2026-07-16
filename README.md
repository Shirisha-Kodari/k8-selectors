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
* ex: kubectl taint nodes ip-192-168-15-26.ec2.internal env=prod:NoSchedule
     kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoSchedule 
      kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoExecute
      kubectl taint nodes ip-192-168-17-180.ec2.internal key1=value1:NoSchedule

     <key>->key1 ,<vaule>->vaule1 
     env->key 
     value->prod 
 * next tainte the node using labels 
 * kubectl taint nodes ip-192-168-15-26.ec2.internal key1=vaule:NoSchedule 
 * ->the pod is pedning beacuse we taint that node but we select the node selector 
 * Noschedule->not scheduling new pods 
 * Noexcute->evicted pods 

 # toolerance:
 * toolerance excuse the tainted node 
 * we add labels whatever add to tainted node 
   taint labels add to toolerance  
* sometimes it not give guarantee so we use also node selecotr and toolerance out pod shloud scheduling tainted  node    

# uses:
 * some hardware for special projects 
 * networking requiremnets 
 * high priority applications 

 # node-affinity: 
 step-1 :
 nodeselector 
 add label to node key=hardware and value=gpu 
 kubectl label nodes ip-192-168-17-180.ec2.internal hardware=gpu
 
 * requiredschedulin:
  -> labels should matche this hard rule 
  -> if does not match the pod is pending 

* preferredsheduling :
 -> labels matche schdelues the pods 
 -> if not lebals match eventhough the pod shechdule another node 
 -> this is soft rule 
 -> the labels if matched then schedule the pod and if not matches scheduling another node 

 # node-anti-affinity :
 * if we give operate notin then scheduling expect selected node 
 use operator = NotIn 

 # pod-affinity: 
 * required schdeuling :

 we define podaffinity 
 thirugh labels 
 if pod-1 is running in one node 
 and pod-2 also want to run same node where pod-1 is running 
 topology key ->find the pod-1 labels and shcedule the pod-2 on the same node 









