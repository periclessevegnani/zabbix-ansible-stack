Autor: Pericles Sevegnani
Contato: periclessevegnani@gmail.com

O objetivo dessa instalacao eh baixar, instalar e configurar o Zabbix + PostgreSQL no Linux Ubuntu.

Edite os arquivos abaixo para personalizar sua instalacao:

- zabbix-stack/roles/postgres/defaults/main.yml:
  Escolha a versao do banco desejada na variavel "pg_version".
  Informe uma senha forte para o usuario "zabbix" na variavel "zbx_db_password".
  Este playbook foi desenvolvido para Ubuntu 24.04, por isso a variavel "zbx_repo_codename" esta setada para "noble", ajuste para o seu caso.

- zabbix-stack/roles/zabbix/defaults/main.yml:
  Escolha a versao do Zabbix desejada na variavel "zbx_version", aqui foi utilizada a versao 6.4.

Passo-a-passo:

- Baixe o Git e os arquivos do GitHub:
apt install -y git
cd
git clone https://github.com/periclessevegnani/zabbix-ansible-stack.git
cd zabbix-ansible-stack

- Baixe e instale o Ansible:
apt update
apt install -y software-properties-common
add-apt-repository --yes --update ppa:ansible/ansible
apt install -y ansible
ansible --version

- Para rodar o playbook:
ansible-galaxy collection install community.postgresql
ansible-playbook -i inventory.ini deploy.yml -v

- Acessar o front-end do Zabbix:
http://IP_DO_SERVIDOR/zabbix
Ja deve abrir na pagina de login, caso nao abra, algo deu errado na sua instalacao, revise os logs.

Duvidas e/ou sugestoes, entre em contato por e-mail.
