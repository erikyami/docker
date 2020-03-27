# Instalando AWX com docker-compose

Instalação da ferramenta AWX


## Clone do Repositorio
```
git clone https://github.com/ansible/awx.git
```

## Instalação de Pacotes

Alterar o aquivo de configuração ./awx/installer/inventory e mudar a linha:

De:
```
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/env python"
```

Para:
```
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/env python3"
```


```
cd awx/installer

ansible-playbook -i inventory install.yml

```

Acesso:

http://192.168.57.80

user: admin
senha: password
