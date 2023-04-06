# k8s-echo

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
