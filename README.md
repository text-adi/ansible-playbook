# Ansible

## Зміст

* [Системні вимоги до проєкту](#системні-вимоги-до-проєкту)
* [Завантаження проєкту](#завантаження-проєкту)
* [Встановлення залежностей](#встановлення-залежностей)
* [Встановлення IP сервера](#встановлення-ip-сервера)
  * [Адміністрування Linux](#адміністрування-linux)
  * [Адміністрування Windows](#адміністрування-windows)
  * [Виконання playbook на кількох серверах](#виконання-playbook-на-кількох-серверах)
* [Запуск playbook](#запуск-playbook)

* [Встановлення ansible на Windows](#встановлення-ansible-на-windows)
---

## Системні вимоги до проєкту

1. Рекомендується Python 3.10. [Завантажити...](https://www.python.org/downloads/release/python-31011/)
2. Ansible 2.15.3 ([Встановлення на Windows](#встановлення-ansible-на-windows))
3. `sshpass` - для входу на сервер по паролю

## Завантаження проєкту

Для завантаження проєкту із github, виконуємо команду в терміналі:
```shell
git clone https://github.com/text-adi/ansible-playbook.git
```

## Встановлення залежностей

Для використання playbook потрібно встановити відповідні модулі ansible. Для цього, потрібно виконати команду в терміналі:
```shell
ansible-galaxy install -r requirements.yml
```

## Встановлення IP сервера

По замовчуванні, сервер, для якого буде виконуватися playbook, не вказаний.
Щоб це змінити, потрібно в файлі `invertory/hosts.yml` вказати IP сервера, для якого буде запущений playbook.

Для цього, після `[servers]`, потрібно, дописати рядок IP сервера, 
та параметри, із якими відбувається підключення до сервера.


### Адміністрування Linux

У випадку для Linux, маємо наступний рядок:

```
[servers]
<ip-address> ansible_user=<user> ansible_port=<port> ansible_password=<password> ansible_shell_type=<shell_type>
```

В нашому випадку, в базовому рядку, із параметрами, потрібно лише замінити відповідні значення, такі як:
* `<ip-address>` - IP адреса сервера, який адмініструється.
* `<user>` - користувач, під яким виконуються команди на сервері.
* `<port>` - порт SSH. Зазвичай, використовується 22 порт.
* `<password>` - пароль користувача, до якого відбувається підключення.
* `<shell_type>` - тип оболонки. У випадку із Linux потрібно використовувати `shell`.


### Адміністрування Windows

У випадку для Windows, потрібно переконатися, що у системі із Windows встановлений OpenSSH. [Встановлення OpenSSH для Windows.](#https://docs.ansible.com/ansible/latest/os_guide/windows_setup.html#windows-ssh-setup)

```
[servers]
<ip-address> ansible_user=<user> ansible_port=<port> ansible_password=<password> ansible_shell_type=<shell_type>
```

В нашому випадку, в базовому рядку, із параметрами, потрібно лише замінити відповідні значення, такі як:
* `<ip-address>` - IP адреса сервера, який адмініструється.
* `<user>` - користувач, під яким виконуються команди на сервері.
* `<port>` - порт SSH.
* `<password>` - пароль користувача, до якого відбувається підключення.
* `<shell_type>` - тип оболонки. У випадку із Windows потрібно використовувати `powershell`.

### Виконання playbook на кількох серверах

Якщо потрібно виконати playbook на кількох серверах, у файлі `invertory/hosts.yml`, 
описати дані підключення для кожного сервера.

Приклад:
```
[servers]
<ip-address-1> ansible_user=<user-1> ansible_port=<port-1> ansible_password=<password-1> ansible_shell_type=<shell_type-1>
<ip-address-2> ansible_user=<user-2> ansible_port=<port-2> ansible_password=<password-2> ansible_shell_type=<shell_type-2>
...
```


## Запуск playbook

Для запуску відповідного playbook в корні проєкту, виконуємо команду в терміналі:

```shell
ansible-playbook playbooks/<name-playbook>.yml
```

Після чого, ansible запитає пароль до сервера, до якого відбувається підключення.


---

## Встановлення ansible на Windows

Оскільки офіційної підтримки ansible немає для Windows, для встановлення будемо використовувати [CygWin](https://www.cygwin.com/install.html).

Для встановлення Ansible в CigWin, потрібно встановити наступні компоненти:

* `python39`
* `python39-pip`
* `python39-cryptography`
* `git` - для завантаження проєкту із github.
* `vim` - або інший редактор, для редагування файлів в терміналі.

