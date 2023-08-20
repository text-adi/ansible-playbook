# Ansible

## Зміст

* [Системні вимоги до проєкту](#системні-вимоги-до-проєкту)
* [Завантаження проєкту](#завантаження-проєкту)
* [Встановлення залежностей](#встановлення-залежностей)
* [Запуск playbook](#запуск-playbook)

---

## Системні вимоги до проєкту

1. Рекомендується Python 3.10. [Завантажити...](https://www.python.org/downloads/release/python-31011/)
2. Ansible 2.15.3
3. `sshpass` - для входу на сервер по паролю

## Завантаження проєкту

Для завантаження проєкту із github, виконуємо команду в терміналі:
```shell
git clone ...
```

## Встановлення залежностей

Для використання playbook потрібно встановити відповідні модулі ansible. Для цього, потрібно виконати команду в терміналі:
```shell
ansible-galaxy install -r requirements.yml
```

## Встановлення IP сервера

По замовчуванні, сервер, для якого буде виконуватися playbook, не вказаний.
Щоб це змінити, потрібно в файлі `invertory/hosts.yml` вказати IP сервера, для якого буде запущений скрипт.

Для цього, допишіть IP сервера, після `[servers]`, для якого очікується виконання playbook, наступним чином:

```
[servers]
127.0.0.1
```

## Запуск playbook

Для запуску відповідного playbook в корні проєкту, виконуємо команду в терміналі:

```shell
ansible-playbook  playbooks/<name-playbook>.yml
```

