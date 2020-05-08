# ec2_aws_ansible

Playbook Ansible para criação de máquinas EC2 na AWS.

# O que eu preciso para executar o meu playbook?

* Uma conta na AWS.
* Ansible instalado.

Após ter sua conta na AWS criada, será necessário criar usuário, grupo e a key-pair para nosso projeto e em seguida realizar o download da "key-pair" que foi criada.

Agora iremos importar a chave criada para que seja possível a comunicação com a AWS.

OBS: O arquivo de key-pay, precisará estar dentro da pasta raiz do projeto "ec2_aws_ansible"
```
chmod 0400 sua_chave.pem
ssh-add sua_chave.pem
```


Assim que baixar o projeto:

```
git clone https://github.com/leoberbert/ec2_aws_ansible.git
```
Será necessário aterar o arquivo:

```
ec2_aws_ansible/roles/create/vars/main.yml
```
Realizando as respectivas alteração de acordo com sua necessidade:

```
---
# vars file for create

instance_type: t2.micro <= <<CHANGE_YOUR_INSTANCE>>
security_group: dev <= <<CHANGE_YOUR_SECURITY_GROUP>>
aws_access_key: <<CHANGE_YOUR_ACCESS>>
aws_secret_key: <<CHANGE_YOUR_ACCESS>>
image: ami-0323c3dd2da7fb37d <= <<CHANGE_YOUR_IMAGE>>
keypair: sua_chave <= <<CHANGE_YOUR_KEYPAR>>
region: us-east-1 <= <<CHANGE_YOUR_REGION>>
count: 1 <= <<CHANGE_YOUR_NUMBER_MACHINES>>

```

Agora basta executar o comando abaixo e acompanhar a criação da sua instância na AWS.

```
ansible-playbook -i hosts main.yml
```

OBS: Certifique-se de estar dentro da pasta do projeto "ec2_aws_ansible" para executar o comando acima.
