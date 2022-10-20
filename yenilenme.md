# Bu daha öncədən qurulu olan Nulink nodunu yeniləmək üçündür. 
## Qurulum 
* Stake və worker hesabınız varsa

1. İşləyən nodu stoplayın.
```bash
docker kill ursula
```

```bash
export NULINK_KEYSTORE_PASSWORD=mövcutşifrəniz

export NULINK_OPERATOR_ETH_PASSWORD=mövcutşifrəniz
```

2. NuLink image faylını çəkin. 
```bash
docker pull nulink/nulink:latest
```
3. Nodu yenidən başladın. 
```bash
docker run --restart on-failure -d \
--name ursula \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
-e NULINK_OPERATOR_ETH_PASSWORD \
nulink/nulink nulink ursula run --no-block-until-ready
```
