Autor: Pericles Sevegnani<br>
Contato: periclessevegnani@gmail.com<br>

O objetivo dessa instalacao eh baixar, instalar e configurar o Zabbix (com Apache) + PostgreSQL no Linux Ubuntu.<br>
Edite os arquivos abaixo para personalizar sua instalacao:<br>
- zabbix-stack/roles/postgres/defaults/main.yml:<br>
  Escolha a versao do banco desejada na variavel "pg_version".<br>
  Informe uma senha forte para o usuario "zabbix" na variavel "zbx_db_password".<br>
  Este playbook foi desenvolvido para Ubuntu 24.04, por isso a variavel "zbx_repo_codename" esta setada para "noble", ajuste para o seu caso.<br>
- zabbix-stack/roles/zabbix/defaults/main.yml:<br>
  Escolha a versao do Zabbix desejada na variavel "zbx_version", aqui foi utilizada a versao 6.4.<br>

Passo-a-passo:<br>

- Baixe e instale o Ansible:<br>
```bash
apt update
apt install -y software-properties-common
add-apt-repository --yes --update ppa:ansible/ansible
apt install -y ansible
ansible --version
```
- Baixe o Git e os arquivos do GitHub:<br>
```bash
apt update
apt install -y git
cd
git clone https://github.com/periclessevegnani/zabbix-ansible-stack.git
cd zabbix-ansible-stack
```
- Para rodar o playbook:<br>
```bash
ansible-galaxy collection install community.postgresql
ansible-playbook -i inventory.ini deploy.yml -v
```
- Acessar o front-end do Zabbix:<br>
```bash
http://IP_DO_SERVIDOR/zabbix
```

Ja deve abrir na pagina de login, caso nao abra, algo deu errado na sua instalacao, revise os logs.<br>
Duvidas e/ou sugestoes, entre em contato por e-mail.<br>

