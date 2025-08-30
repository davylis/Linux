# Tehtävä h2

- Tein harjoituksen lauantaina kotona. Käytin tehtävän tekoon Linuxia.

## Artikkelin tiivistelmä
- Komentorivin perusasiat: ```pwd``` näyttää nykyisen hakemiston, ```ls``` listaa tiedostot, ```cd``` vaihtaa hakemistoa. Komennon tulosteen voi selata ```less```-komennolla
- Tiedostojen käsittely: ```nano``` editorina(itse käytän vim), ```mkdir``` luo hakemiston, ```mv``` siirtää/nimeää uudelleen, ```cp``` kopioi, ```rm``` poistaa (ei roskakoria).
- Etäkäyttö: ```ssh``` avaa yhteyden etäkoneeseen, ```scp``` kopioi tiedostoja koneiden välillä.
- Apua: ```man``` ja ```--help``` näyttävät ohjeet. Tab-täydennys ja nuolinäppäimet nopeuttavat käyttöä.
-Tärkeät hakemistot: / juurihakemisto(root), /home/ käyttäjien kotihakemistot, /etc/ järjestelmän asetukset, /var/log/ lokit.
-Ylläpito ja ohjelmien asennus: ```sudo``` tarvitaan järjestelmätason muutoksiin. ```apt-get``` paketinhallintaan (päivitykset, haku, asennus, poisto).

## Micro editorin asennus
<img width="1485" height="932" alt="Screenshot from 2025-08-30 14-23-58" src="https://github.com/user-attachments/assets/f4a60e20-ad9e-4135-aa3f-3b7276eda91c" />

## Kolme uutta komentoriviohjelmaa
- Ohjelmien asentaminen
 ```
  sudo apt install -y tmux ranger ncdu
 ```
1. tmux : jaa terminaali useaan paneeliin
<img width="1485" height="932" alt="Screenshot from 2025-08-30 14-34-05" src="https://github.com/user-attachments/assets/8a7691c8-422d-48a1-a746-118d8a00637f" />
2. ranger : tiedostojen selaaminen ja hallinta paljon mukavampaa kuin pelkillä ls, cd ja mv komennoilla.
<img width="1485" height="932" alt="Screenshot from 2025-08-30 14-36-52" src="https://github.com/user-attachments/assets/8557e2cb-6014-40c0-94e0-9950004dacdf" />
3. ncdu : tekstipohjainen työkalu levytilan analysointiin
<img width="1485" height="932" alt="Screenshot from 2025-08-30 14-40-04" src="https://github.com/user-attachments/assets/ef3ce346-3085-4b30-a57a-c595e9428f39" />

### FHS
<img width="1920" height="1048" alt="Screenshot from 2025-08-30 16-57-03" src="https://github.com/user-attachments/assets/c7929c6a-ed71-4330-8762-674a25baa5b5" />
<img width="1920" height="1048" alt="Screenshot from 2025-08-30 16-57-40" src="https://github.com/user-attachments/assets/f9fea7f2-9f46-4d1c-9f2d-d684149106ce" />
- juurihakemistot
- kotihakemisto
- käyttäjän tiedostot
-  ```/etc/``` järjestelmän asetukset
- ```/media/``` mediahakemistosta löytyy tallennusvälineet
- ```/var/log/```hakemistosta löytyy lokitiedostot

  
### Grep-kommennot ja Pipe
<img width="1518" height="932" alt="Screenshot from 2025-08-30 15-17-54" src="https://github.com/user-attachments/assets/5ede76b1-7db7-4145-9fe8-af6813c6814a" />
- 


### Rauta

<img width="1920" height="1048" alt="Screenshot from 2025-08-30 15-22-03" src="https://github.com/user-attachments/assets/495389ba-9060-42e9-93f8-f154ffc304e6" />

- Järjestelmä ja bus:
```
system         20FAS1NF00 (LENOVO_MT_20FA_BU_Think_FM_T)
bus            20FAS1NF00
```
- Muisti: L1,L2,L3 prosessorin välimuistit, RAM, ja tyypit DDR4
```
memory         64KiB L1 cache
memory         512KiB L2 cache
memory         3MiB L3 cache
memory         24GiB System Memory
memory         8GiB SODIMM DDR4
memory         16GiB SODIMM DDR4
```
- Prosessori: 2-ytiminen/4-sähkeinen prosessori
```
processor      Intel(R) Core(TM) i5-6300U CPU @ 2.40GHz
```
- Näytönohjain: Integroitu Intel HD Graphics 520 ja graafinen näyttö, 2D/3D kiihdytys
```
/dev/fb0   display        Skylake GT2 [HD Graphics 520]
```
- Tallennustila: yksi SSD-levy 256 GiB, FAT Windows bootloader, Linuxin pääjärjestelmä
```
/dev/sda   disk           256GB Micron_1100_MTFD
/dev/sda1  volume         511MiB Windows FAT volume
/dev/sda2  volume         2047MiB swap partition
/dev/sda3  volume         2047MiB boot partition
/dev/sda4  volume         233GiB root partition
```
- Verkkokortit ja USB: Wifi, Ethernet, Bluetooth ja kamera
```
wlp4s0     network        Wireless 8260
enp0s31f6  network        Ethernet Connection I219-LM
/0/100/14/0/7  Bluetooth wireless interface
/0/100/14/0/8  Integrated Camera
```
- Ääni ja syöttölaitteet
```
/0/100/1f.3        card0      multimedia     Sunrise Point-LP HD Audio
input0-8           input       näppäimistö, touchpad, TrackPoint, napit, lid switch
```


## Lokien analysointi
<img width="1518" height="932" alt="Screenshot from 2025-08-30 16-21-35" src="https://github.com/user-attachments/assets/1e55d319-765d-48ee-9771-40a8bad14bda" />

- viestit tulee Linux-ytimeltä
- ``` audit: type=1400 ``` auditointiloki, AppArmor-viesti
- DENIED eli estänyt operaation
- yritettiin avata tiedostoa
- rajoitus koskien Firefox selainta
- prosessin tunnus ja nimi
- Kirjoitusoikeus pyydetty mutta estetty
- ```fsuid=1000 ouid=1000``` käyttäjä, joka yritti operointia
- lokissa näkyy sama viesti monta kertaa eri prosesseille → Firefox tai jokin sen laajennus yrittää kirjoittaa oom_score_adj useaan kertaan
- AppArmor suojaa järjestelmää vahingollisilta toiminnoilta

## Plugin micro-editorille
<img width="1518" height="932" alt="Screenshot from 2025-08-30 16-40-07" src="https://github.com/user-attachments/assets/e3dffb6f-af1a-4b30-a30e-707dd105a21a" />

## Lähteet
- https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
- https://terokarvinen.com/2009/command-line-basics-4/
- https://terokarvinen.com/2008/commands-for-admin-4/
- https://gitlab.com/apparmor/apparmor/-/wikis/Home?utm_source=chatgpt.com
- https://github.com/terokarvinen/palettero
