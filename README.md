# Домашнее задание к занятию 1 «Disaster recovery и Keepalived»  
**Шаров Олег**

---

## Задание 1

> Дана схема для Cisco Packet Tracer.  
> На данной схеме уже настроено отслеживание интерфейсов маршрутизаторов Gi0/1 (для нулевой группы).  
> Необходимо аналогично настроить отслеживание состояния интерфейсов Gi0/0 (для первой группы).  
> Для проверки корректности настройки, разорвите один из кабелей между одним из маршрутизаторов и Switch0 и запустите ping между PC0 и Server0.  
> На проверку отправьте получившуюся схему в формате pkt и скриншот, где виден процесс настройки маршрутизатора.

### Решение

На обоих маршрутизаторах настроена HSRP-группа 1 на интерфейсе `GigabitEthernet0/0` с отслеживанием состояния линка. Приоритеты выставлены так, чтобы Router1 был MASTER (105), а Router2 — BACKUP (100). Включён режим `preempt` для немедленного возврата активной роли после восстановления связи.

**Конфигурация на Router1:**
```bash
interface GigabitEthernet0/0
 standby 1 ip 192.168.0.1
 standby 1 priority 105
 standby 1 preempt

Конфигурация на Router2:

```bash
interface GigabitEthernet0/0
 standby 1 ip 192.168.0.1
 standby 1 priority 100
 standby 1 preempt

После разрыва кабеля между Router1 и Switch0 на интерфейсе Gi0/0, роль Active переключается на Router2, и связь между PC0 (192.168.0.250) и Server0 (192.168.1.50) сохраняется без прерываний.

1. Подключение Router1 к Switch0 на интерфейсе Gi0/0  

![Router1 to Switch0 connection](router1-switch0-gi00.png)

**2. Схема после разрыва кабеля (тест отказоустойчивости)**  

![Cable disconnected — HSRP failover test](test-after-cable-disconnect.png)

**3. CLI: настройка HSRP с отслеживанием интерфейса**  

![HSRP CLI configuration](hsrp-cli-configuration.png)


