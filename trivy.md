## Geral

Trivy é um scanner de vulnerabilidades para containers. É fácil de utilizar, basta instalar o binário e você já estará pronto para scanear. Tudo que você precisa é especificar um target como uma imagem de container.


## Instalação

```
$ sudo vim /etc/yum.repos.d/trivy.repo
[trivy]
name=Trivy repository
baseurl=https://aquasecurity.github.io/trivy-repo/rpm/releases/$releasever/$basearch/
gpgcheck=0
enabled=1

$ sudo yum -y update

$ sudo yum -y install trivy
```

Utilização:

```
trivy image [YOUR_IMAGE_NAME]
```
Na primeira execução ele vai baixar as informações do banco de vulnerabilidades. 

### Filtrando Vulnerabilidades
Por Serveridade

Use --severity option.

```
$ trivy image --severity HIGH,CRITICAL ruby:2.4.0
```

