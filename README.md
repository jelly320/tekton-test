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
kubectl create secret generic regcred --from-file=.dockerconfigjson=/data/kaniko/.docker/config.json
```


tekton安装
```
# kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

# wget https://github.com/tektoncd/dashboard/releases/latest/download/tekton-dashboard-release.yaml  修改NodePort

# rpm -Uvh https://github.com/tektoncd/cli/releases/download/v0.21.0/tektoncd-cli-0.21.0_Linux-64bit.rpm
```