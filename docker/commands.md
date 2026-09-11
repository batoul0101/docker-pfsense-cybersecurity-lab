# Docker Commands

## Docker Environment Verification

```bash
docker version

docker info

docker ps

docker network ls
```

---

## Shared Network Creation

```bash
docker network create cyberlab
```

التحقق:

```bash
docker network inspect cyberlab
```

---

## Attacker Container

```bash
docker run -dit \
--name scripting-lab \
--network cyberlab \
python:3.12-slim
```

الدخول للكونتينر:

```bash
docker exec -it scripting-lab sh
```

التحقق من الـ IP:

```bash
hostname -I
```

أو:

```bash
ip addr
```

---

## Target Container

```bash
docker run -dit \
--name target-lab \
--network cyberlab \
ubuntu:24.04
```

الدخول:

```bash
docker exec -it target-lab bash
```

تحديث النظام:

```bash
apt update
```

تنصيب SSH:

```bash
apt install -y openssh-server
```

تشغيل SSH:

```bash
service ssh start
```

التحقق:

```bash
ss -tulpn
```

---

## Network Inspection

عرض الشبكات:

```bash
docker network ls
```

فحص شبكة:

```bash
docker network inspect cyberlab
```

IP الـ Attacker:

```bash
docker inspect -f "{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}" scripting-lab
```

IP الـ Target:

```bash
docker inspect -f "{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}" target-lab
```

---

## Network Segmentation

إنشاء شبكة المهاجم:

```bash
docker network create \
--subnet=10.10.10.0/24 \
attacker-net
```

إنشاء شبكة الهدف:

```bash
docker network create \
--subnet=10.10.20.0/24 \
target-net
```

فصل الكونتينرات:

```bash
docker network disconnect cyberlab scripting-lab

docker network disconnect cyberlab target-lab
```

ربط المهاجم:

```bash
docker network connect \
--ip 10.10.10.10 \
attacker-net \
scripting-lab
```

ربط الهدف:

```bash
docker network connect \
--ip 10.10.20.10 \
target-net \
target-lab
```

التحقق:

```bash
docker inspect scripting-lab

docker inspect target-lab
```

---

## Connectivity Tests

من Attacker:

```bash
docker exec -it scripting-lab sh
```

Ping على Gateway:

```bash
ping 10.10.10.1
```

اختبار الوصول لـ Target:

```bash
ping 10.10.20.10
```

اختبار SSH:

```bash
nc -zv 10.10.20.10 22
```

اختبار HTTP:

```bash
nc -zv 10.10.20.10 80
```

اختبار Route:

```bash
ip route
```

---

## Resource Limits

إيقاف الكونتينر:

```bash
docker stop target-lab

docker rm target-lab
```

إعادة الإنشاء مع القيود:

```bash
docker run -dit \
--name target-lab \
--network target-net \
--ip 10.10.20.10 \
--memory=256m \
--cpus=0.5 \
ubuntu:24.04
```

التحقق:

```bash
docker inspect target-lab
```

البحث عن Memory:

```bash
docker inspect target-lab | grep Memory
```

البحث عن CPU:

```bash
docker inspect target-lab | grep NanoCpus
```

---

## Monitoring

مراقبة الكونتينرات:

```bash
docker ps
```

استهلاك الموارد:

```bash
docker stats
```

سجلات الكونتينر:

```bash
docker logs target-lab

docker logs scripting-lab
```

معلومات الشبكة:

```bash
docker network inspect attacker-net

docker network inspect target-net
```

معلومات الراوت:

```bash
docker exec scripting-lab ip route

docker exec target-lab ip route
```
