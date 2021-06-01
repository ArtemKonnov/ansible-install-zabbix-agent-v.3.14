# Installer zabbix agent v.3.14

Ansible playbook для установки  zabbix-agent v.3.14 на удалённые машины (Ubuntu, Debian, Centos)

Текщий файл hosts зашифрован Vault. Для запуска задачи необходимо пересоздать файл hosts:

` rm ./hosts ` 

` EDITOR=nano ansible-vault init hosts  `
 
`<ввод master-pass> ` запомнить

**Формат заполнения файла hosts:**

```
[nodes]
node_name_1 ansible_host=<ip адрес> ansible_ssh_user=<логин> ansible_become_pass=<sudo пароль от ВМ> ansible_ssh_pass=<пароль от ВМ>
node_name_2 ansible_host=<ip адрес> ansible_ssh_user=<логин>  ansible_become_pass=<sudo пароль от ВМ>  ansible_ssh_pass=<пароль от ВМ>
node_name_3 ansible_host=<ip адрес> ansible_ssh_user=<логин>  ansible_become_pass=<sudo пароль от ВМ>  ansible_ssh_pass=<пароль от ВМ>
```

**Команда для редактирования файла hosts:**
` EDITOR=nano ansible-vault edit hosts `

**Команда запуска задачи:**
`ansible-playbook zabbix-agent.yml --ask-vault-pass -v`

Перед запуском проверить директорию vars