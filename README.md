Чтобы запустить Ad-Hoc команду с указанием сервера 178.178.73.149, используйте следующую команду:

```bash
ansible all -i 178.178.73.149, -m ping -u <username> -k
```

Или для выполнения вашего плейбука:

```bash
ansible-playbook -i 178.178.73.149, create_users.yaml -u <username> -k
```

Где:
- `-i 178.178.73.149,` - указывает инвентарь (запятая в конце важна для ad-hoc инвентаря)
- `-u <username>` - имя пользователя для подключения к серверу
- `-k` - запросить пароль пользователя
- `-m ping` - модуль для проверки подключения

Если у вас есть SSH ключ для подключения, используйте:

```bash
ansible-playbook -i 178.178.73.149, create_users.yaml -u <username> --private-key ~/.ssh/your_key
```

Также вы можете создать файл инвентаря `inventory.ini`:

```ini
[all]
178.178.73.149

[all:vars]
ansible_user=<username>
ansible_ssh_private_key_file=~/.ssh/your_key
```

И затем запустить:
```bash
ansible-playbook -i inventory.ini create_users.yaml
```

```bash
ansible-playbook -i /etc/ansible/hosts create_users.yaml --limit zaim -k
```

Или если хотите использовать прямое указание IP:

```bash
ansible-playbook -i 178.178.73.149, create_users.yaml -u root -k
```
```bash
ansible-playbook -i zaim, create_users.yaml -u root -k
```

