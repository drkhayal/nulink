# NuLink Horus Testnet Node (Mükafatlı-Binance yatırımlı)
Testnet 2 hissəli olacaq.
* Hissə 1 : (15 sentyabr— 20 noyabr)
* Hissə 2 : (20 oktyabr — 20 noyabr)
Testnetin ilk hissəsini edənlər 3000 NLK + ikincini edənlər 6000 NLK və token ön satışı üçün whitelistə yer qazanacaqlar.

Keçək nodu qurmağa

```bash
sudo su
```
```bash
sudo ufw allow 9151
```
```bash
sudo apt-get update && apt-get upgrade -y
```
```bash
sudo apt-get -y install libssl-dev && apt-get -y install cmake build-essential git wget jq make gcc
```


Aşağıdakı kodu yazandan sonra sizdən şifrə istəyəcək, şifrəni yazın,Bizə “key”lər verəcək, həm şifrəni həm də keyləri mütləq bir yerə qeyd edin yaddaşda saxlayın.

```bash
wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.10.24-972007a5.tar.gz

tar -xvzf geth-linux-amd64-1.10.24-972007a5.tar.gz

cd geth-linux-amd64-1.10.24-972007a5/

./geth account new --keystore ./keystore
```
```bash
cd /root
```
```bash
sudo apt install docker.io -y
```
```bash
sudo systemctl enable --now docker
```
```bash
docker pull nulink/nulink:latest
```
```bash
cd /root
mkdir nulink
```
Bayaq yaddaşda saxladığımız, “Path of the secret key file” yerində çıxan yazını ( “/root** ilə başlayır) kopya edib aşağıdakı kodda əvəz edirik.


```bash
cp KEYİBURAYAZIN /root/nulink
```
```bash
chmod -R 777 /root/nulink
```
Bura ən azı 8 xanalı şifrə yazın, ikisini də eyni etmək lazımdır.

```bash
export NULINK_KEYSTORE_PASSWORD=ŞİFRƏNİZ

export NULINK_OPERATOR_ETH_PASSWORD=ŞİFRƏNİZ
```
Bu kodda yenə key fayldan əvəzetmə edəcəyik.
Kodda yazılan “UTC daxil və sonrasını əvəzləyin” yerini dəyişin. Public adress də keydə olan adresdir.
Aşağıdakı kodu girəndən sonra “y” yazın . Mnemonicləri yadda saxlayın.
```bash
docker run -it --rm \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
nulink/nulink nulink ursula init \
--signer keystore:///code/UTC daxil və sonrasını əvəzləyin \
--eth-provider https://data-seed-prebsc-2-s2.binance.org:8545  \
--network horus \
--payment-provider https://data-seed-prebsc-2-s2.binance.org:8545 \
--payment-network bsc_testnet \
--operator-address PUBLICadresiniz \
--max-gas-price 100
```
Nodu başladın.
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
Screendə logları açıb, kodları sıra ilə girin. Loglarını işləməyini gözləyib 1–2 dəqiqə sonra ctrl+a+d basıb əsas ekrana geri qayıdın.
```bash
apt install screen
screen -S log
docker logs -f ursula
```
* Aşağıdakı sayta girib metamaskınızı bağlayın. BSC TEST ağı avtomatik əlavə olunacaq. BSC Test token və Nulink token alın.
 Nulink Staking
BSC test faucet : https://testnet.binance.org/faucet-smart
* Nulinkləri staking bölməsindən stake edirik. Daha sonra Bond worker basırıq.

Worker bölümü nodu quranda verdiyi ilk public adresimiz.

Node Url : aşağıda bir nümunə yazdım. 123.45.678 yerinə serverinizin ip adresini yazacaqsınız. Sonda olan 9151 yerində qalacaq.

https://123.45.678:9151
* Nodunuz bu işləmlərdən sonra online görünəcək. Bir neçə dəqiqə çəkə bilər.
* Saytda nod online olub, sonradan offline olarsa narahat olmayın. Saytla bağlı bir məsələdir.

— — — — — — — — — — — — — — — — — — —— — — — — — — — — — — — — — — — — — —

** Form: Feedback yazmaq lazımdır. Əgər heç bir problem olmayıbsa elə də qeyd edin. Metamask adresinizi yazın .
https://docs.google.com/forms/d/e/1FAIpQLSdFhnZWG6p6XLY3xqNSMRJbFFN3_M0nRXG4E23X0RPVB6b4yA/viewform
** Proyektin Twitter , discorduna qatılın;
DC : https://discord.gg/3pn3cC9ww6

Twitter : https://twitter.com/NuLink_

