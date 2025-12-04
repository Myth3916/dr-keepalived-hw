# Домашнее задание к занятию 1 «Disaster recovery и Keepalived»  
**Шаров Олег**

---

Задание 1  
Настроено отслеживание интерфейса GigabitEthernet0/0 для HSRP-группы 1 на обоих маршрутизаторах. Приоритет MASTER (Router1) — 105, BACKUP (Router2) — 100. Включён режим preempt. После разрыва кабеля между Router1 и Switch0 на интерфейсе Gi0/0 роль Active переключается на Router2, и связь между PC0 (192.168.0.250) и Server0 (192.168.1.50) сохраняется без прерываний.

1. Открыта схема в Cisco Packet Tracer.  
2. На Router1 и Router2 добавлена конфигурация HSRP-группы 1 на интерфейсе Gi0/0.  
3. Настроено отслеживание состояния интерфейса с помощью команды standby 1 track GigabitEthernet0/0 decrement 20.  
4. Выполнен тест: разрыв кабеля между Router1 и Switch0 на порту Gi0/0.  
5. Подтверждена непрерывность ping между PC0 и Server0.

6. Сохранена схема как homework1.pkt.  
7. Сделаны скриншоты: подключение Router1 к Switch0, CLI-настройка, схема после разрыва кабеля.

Поле для вставки кода...  
```bash
interface GigabitEthernet0/0
 standby 1 ip 192.168.0.1
 standby 1 priority 105
 standby 1 preempt
```
![img](img/hsrp-cli-configuration.png)
![img](img/router1-switch0-gi00.png)
![img](img/test-after-cable-disconnect.png)



