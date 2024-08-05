# Домашнее задание к занятию "Система мониторинга Zabbix" - Сухопалов Дмитрий


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

```
Установка репозиториев:
# wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_7.0-2+debian12_all.deb
# dpkg -i zabbix-release_7.0-2+debian12_all.deb
# apt update 

Установка постгреса:
# apt install postgresql -y

Установка пакетов zabbix:
# apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

Настройка БД:
# sudo -u postgres createuser --pwprompt zabbix
# sudo -u postgres createdb -O zabbix zabbix 
# zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix 

Редактирование конфига:
# nano /etc/zabbix/zabbix_server.conf
DBPassword=123456789

Службы:
# systemctl restart zabbix-server zabbix-agent apache2
# systemctl enable zabbix-server zabbix-agent apache2 
```

![Страница входа](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/1.1.jpg)
![Главная страница](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/1.2.jpg)


---

### Задание 2


```
Установка агента:
# wget https://repo.zabbix.com/zabbix/7.0/debian/pool/main/z/zabbix-release/zabbix-release_7.0-2+debian12_all.deb
# dpkg -i zabbix-release_7.0-2+debian12_all.deb
# apt update 
# apt install zabbix-agent

Редактирование конфига:
# find / -name "zabbix_agentd.conf"
# nano /etc/zabbix/zabbix_agentd.conf
Server=192.168.5.200

Запуск служб:
# systemctl restart zabbix-agent.service

Проверка лога:
# find / -name "zabbix_agentd.log"
# tail -f /var/log/zabbix/zabbix_agentd.log
```

![Узлы](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/2.1.jpg)
![Лог агента](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/2.2.jpg)
![Данные 1](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/2.3.jpg)
![Данные 2](https://github.com/PL4NTEXZ/hw_sdn/blob/main/img/smon-02/2.4.jpg)


---
