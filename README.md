# Домашнее задание к занятию "8.4 Работа с Roles"
## Подготовка к выполнению
1. Создайте два пустых публичных репозитория в любом своём проекте: vector-role и lighthouse-role.
2. Добавьте публичную часть своего ключа к своему профилю в github.

## Основная часть
Наша основная цель - разбить наш playbook на отдельные roles. Задача: сделать roles для clickhouse, vector и lighthouse и написать playbook для использования этих ролей. Ожидаемый результат: существуют три ваших репозитория: два с roles и один с playbook.

1. Создать в старой версии playbook файл requirements.yml и заполнить его следующим содержимым:

```
---
  - src: git@github.com:AlexeySetevoi/ansible-clickhouse.git
    scm: git
    version: "1.11.0"
    name: clickhouse 
```

2. При помощи ansible-galaxy скачать себе эту роль.

```
[root@localhost share]# ansible-galaxy role install -r requirements.yml
Starting galaxy role install process
The authenticity of host 'github.com (140.82.121.3)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
- extracting clickhouse to /root/.ansible/roles/clickhouse
- clickhouse (1.11.0) was installed successfully
```

3. Создать новый каталог с ролью при помощи ansible-galaxy role init vector-role.

```
[root@localhost share]# ansible-galaxy role init vector-role
- Role vector-role was created successfully
```

4. На основе tasks из старого playbook заполните новую role. Разнесите переменные между vars и default.

5. Перенести нужные шаблоны конфигов в templates.

6. Описать в README.md обе роли и их параметры.

7. Повторите шаги 3-6 для lighthouse. Помните, что одна роль должна настраивать один продукт.

Не очень было понятно, зачем так много кликхаусов, сделал из своего ещё одну роль, как сказано в самом начале
https://github.com/SergeyKosmovsky/vector-role  
https://github.com/SergeyKosmovsky/lighthouse-role  
https://github.com/SergeyKosmovsky/clickhouse-role  

8. Выложите все roles в репозитории. Проставьте тэги, используя семантическую нумерацию Добавьте roles в requirements.yml в playbook.

```
Starting galaxy role install process
- clickhouse (1.11.0) is already installed, skipping.
- extracting vector-role to /root/.ansible/roles/vector-role
- vector-role (1.0.0) was installed successfully
- extracting lighthouse-role to /root/.ansible/roles/lighthouse-role
- lighthouse-role (1.0.0.1) was installed successfully
- extracting clickhouse-role to /root/.ansible/roles/clickhouse-role
- clickhouse-role (1.0.0) was installed successfully
```

9. Переработайте playbook на использование roles. Не забудьте про зависимости lighthouse и возможности совмещения roles с tasks.

10. Выложите playbook в репозиторий.

11. В ответ приведите ссылки на оба репозитория с roles и одну ссылку на репозиторий с playbook.

https://github.com/SergeyKosmovsky/vector-role  
https://github.com/SergeyKosmovsky/lighthouse-role  
https://github.com/SergeyKosmovsky/playbook-8.3  
