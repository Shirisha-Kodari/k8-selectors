# nodeselector 
* first we add labels to node using below command 
kubectl label nodes <node-name> <key>=<value>
ex: kubectl label nodes ip-192-168-15-26.ec2.internal disk=ssd 

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

 