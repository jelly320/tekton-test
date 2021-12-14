每个task应当都是可以被复用的

tekton-test描述：
```
- resource
    |- serviceaccount.yaml
    |- 
- tasks
    |-
    |-
- pipeline
    |- build-pipeline.yaml  //pipeline
- run
    |- run.yaml   //pipelinerun
- trigger
    |- 


执行和创建
1. 创建secret docker-registry
```
# kubectl create secret docker-registry dockerhub --docker-server=harbor.996a.com:8443 --docker-username=vela --docker-password=3xxxxL --dry-run=client -o json | jq -r '.data.".dockerconfigjson"' | base64 -d > /tmp/config.json && kubectl create secret generic docker-config --from-file=/tmp/config.json
```

3. apply
```
# kubectl apply -f resource/git-secret.yaml 
# kubectl apply -f resource/serviceaccount.yaml
...
所有task
所有pipeline
```

4. apply run
```
# kubectl apply -f run/run.yaml
```

第二类
第三类
```







mark
```

```


tekton安装
```
# kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

# wget https://github.com/tektoncd/dashboard/releases/latest/download/tekton-dashboard-release.yaml  
参考tekton-dashboard-release.yaml中Service部分的修改，按需即可。

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



我本地pv建来测试的比较小，如果因为上个pr失败导致未释放，可以操作一下如下：
```
# kubectl patch pv pv001 -p '{"spec":{"claimRef": null}}' 
```