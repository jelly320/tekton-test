```
- tasks
    |-
    |-
- pipeline
- run
- trigger
```




mark
```

```


tekton安装
```
# kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

# wget https://github.com/tektoncd/dashboard/releases/latest/download/tekton-dashboard-release.yaml  修改NodePort

# rpm -Uvh https://github.com/tektoncd/cli/releases/download/v0.21.0/tektoncd-cli-0.21.0_Linux-64bit.rpm
```

https://github.com/tektoncd/pipeline/blob/main/docs/tutorial.md


当我在pipelinerun中使用volumeClaimTemplate时，会出现如下报错：
```
Events:
  Type     Reason            Age                 From               Message
  ----     ------            ----                ----               -------
  Warning  FailedScheduling  53s (x3 over 119s)  default-scheduler  0/3 nodes are available: 3 pod has unbound immediate PersistentVolumeClaims.
```
在任何集群都是。


大致的变量传递的逻辑
pipelineResource
```
  pipelinerun的resource，必须是已经创建过的同名pipelineResource，要么就直接写一个resourceSpec现创一个
  
  pipeline也同理。 
  不过pipeline中的resource主要是为了传到task里面去。
  传入task时，resources.input.name可以随意取，他想表达的意思只是这个resource是已定义的git-repo

  task中的就必须name就必须是resources.input.name了。
```
params

tekton和deploy不在一个集群？



```
echo user:passwd |base64
cat /data/kaniko/.docker/config.json
  {
      {
          "auths": {
                  "harbor.****.com:8*3": {
                          "auth": "bHV5dWppYW5**************************0A0NTY0Cg=="
                  }       
          }       
      }
  }
kubectl create secret generic regcred --from-file=.dockerconfigjson=/data/kaniko/.docker/config.json
```