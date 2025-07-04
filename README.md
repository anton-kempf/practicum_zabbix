# Задание к практикуму по работе с Zabbix  
## Колыванов Антон  
### Цели задания  

1. Научиться планировать мониторинг инфраструктуры.
2. Настроить базовые проверки с помощью системы мониторинга Zabbix.
3. Закрепить знания по архитектуре системы мониторинга Zabbix.
4. Попрактиковаться в подключении хостов по SNMP.

### Чек-лист готовности к выполнению заданий практикума 

1. Ранее по программе изучены материалы занятий «L2-сеть», «L3-сеть», «L4-сеть», Firewall.
2. С помощью Vagrant созданы три виртуальные машины с Ubuntu, названы следующим образом: Zabbix, client1, client2. Настроены сетевые интерфейсы виртуальных машин так, чтобы у всех ВМ была связь друг с другом и с интернетом.
3. С помощью Ansible установлены Zabbix-сервер, Zabbix-агенты.

### Требование к результату

1. Выложите в репозиторий Vagrantfile и плейбуки Ansible.
 
---

## Задание 1. Настройка мониторинга интернет-хоста

### Описание задания

Настройте мониторинг интернет-хоста 8.8.8.8 при помощи встроенного шаблона Template ICMP Ping. Убедитесь, что триггеры работают при потере связи с 8.8.8.8.

### Этапы выполнения задания

1. Создайте host 8.8.8.8 для группы Internet-services.
2. Подключите шаблон Template ICMP Ping к хосту 8.8.8.8.
3. Дождитесь получения данных.
4. Заблокируйте маршрут до 8.8.8.8 (ip route add blackhole 8.8.8.8).
5. Убедитесь, что триггер потери связи с 8.8.8.8 сработал.

### Требование к результату

1. Убедитесь, что триггер потери связи с 8.8.8.8 сработал.
2. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.  


[скриншот](img/1.png)

 
## Задание 2. Настройка мониторинга ВМ client1 и client2

### Описание задания

Настройте мониторинг ВМ client1 и client2 при помощи встроенного шаблона Template OS Linux by Zabbix agent. Убедитесь, что агенты присылают данные.


### Этапы выполнения задания

1. Установите Zabbix-agent на ВМ client1 и client2.
2. Отредактируйте конфигурационный файл zabbix_agentd.conf на каждом клиенте, добавив параметр Server=IP, где IP — IP-адрес ВМ Zabbix.
3. Перезагрузите службу zabbix-agent: systemctl restart zabbix-agent.
4. Создайте host client1 и client2 для группы Linux-servers.
5. Подключите шаблон Template OS Linux by Zabbix agent к хостам client1 и client2.
6. Убедитесь, что данные от client1 и client2 появились в системе мониторинга.

### Требование к результату

1. Убедитесь, что данные от client1 и client2 доступны в разделе Latest data.
2. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.  

[скриншот](img/2.png)

---

## Задание 3. Настройка мониторинга облачного роутера

### Описание задания

Настройте мониторинг облачного роутера netology_csr при помощи встроенного шаблона Cisco IOS versions 12.0._3_T-12.2_3.5 by SNMP. Убедитесь, что агенты присылают данные.

### Этапы выполнения задания

1. Создайте host netology_csr для группы Cloud-routers (IP - 45.134.127.23, метод опроса — SNMP, community — netology_snmp).
2. Подключите шаблон Cisco IOS versions 12.0._3_T-12.2_3.5 by SNMP.
3. Убедитесь, что даннные от netology_csr появились в системе мониторинга.

### Требования к результату

1. Убедитесь, что данные от netology_csr доступны в разделе Latest data.
2. Сделайте скриншот полученного результата. Поделитесь им в чате занятия или продемонстрируйте свой экран преподавателю непосредственно на практикуме.  

[скриншот](img/3.png)
