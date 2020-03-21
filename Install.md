# Estudos Docker

## Instalando o Docker
```
curl -fsSl https://get.docker.com | bash
```

O comando acima vai configurar os repositórios e instalar o docker corretamente no sistema operacional


## Configurando usuário no grupo docker
```
sudo usermod -aG docker vagrant
```

## Habilitando e iniciando o docker
```
[vagrant@docker ~]$ sudo systemctl enable docker
Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.
[vagrant@docker ~]$ sudo systemctl start docker
[vagrant@docker ~]$ 
```
