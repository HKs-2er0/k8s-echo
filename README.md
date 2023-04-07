# k8s-echo

## 適用手順

レポジトリ Top にすべてのファイルを置いてしまったため、適用に下記コマンドは使えない。

```zsh
kubectl apply -f .
```

なので、下記手順で適用を行う。

```zsh
kubectl apply -f namespace.yaml
kubectl apply -f configmap.yaml -n dev-nginx
kubectl apply -f dev-nginx-deployment.yaml -n dev-nginx
kubectl apply -f dev-nginx-service.yaml -n dev-nginx
kubectl apply -f dev-server-deployment.yaml -n dev-server
kubectl apply -f dev-server-service.yaml -n dev-server
```

最後に Cluster 外部から `dev-nginx` の Service に対して Port-Forward するための設定を追加する。

```zsh
kubectl port-forward service/nginx-service 8080:8081 -n dev-nginx
```


## Linters

### YAML

これらのファイルはすべて、`yamllint` による Validation を行っているため、下記コマンドでインストールすることを推奨します。

```zsh
brew install yamllint
```

実行方法は次のコマンドの通りである。

```zsh
yamllint -c .yamllint.yaml *.yaml
```
