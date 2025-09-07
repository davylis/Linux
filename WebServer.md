
# Tehtävä h3

- Tein harjoituksen lauantaina kotona. Omalla koneellani on Linux, mutta harjoitusta varten käytin virtuaalikoneiden luomiseen Oraclea VirtualBoxia(joka oli valmiiksi ladattuna).

```console
OS Name:          Zorin OS 17.3
OS Version:       17
Kernel Version:   6.8.0-65-generic
System Type:      x86_64
```

## Apache HTTP Server 2.4 Artikkelin tiivistelmä
- IP-pohjainen Virtual Host Support: jokaiselle sivulle oma IP-osoite.
- Name-pohjainen Virtual Host Support: kaikki sivut voivat jakaa saman IP:n, erotus tapahtuu Host-otsakkeen avulla.
- Kannattaa Säästää IP-osoitteita, ellei erikseen tarvita IP-pohjaista.
- Miten Apache valitsee oikean VirtualHostin: Ensin ratkaistaan IP+portti -> sitten verrataan ServerName ja ServerAlias -> Jos ei löydy täsmäävää, käytetään ensimmäistä määriteltyä VirtualHostia oletuksena.
- Käyttö:Jokainen host määritellään <VirtualHost *:80>-lohkoon -> Vähintään tarvitaan ServerName ja DocumentRoot

## Karvinen: Name Based Virtual Hosts on Apache Artikkelin tiivistelmä
- Asennus: Apache asennetaan: ```sudo apt-get -y install apache2```
- Uuden VirtualHostin luonti: Luodaan uusi asetustiedosto ```/etc/apache2/sites-available/nimi.conf```
- Testaus: ```curl -H 'Host: ...' localhost```
- Samalla koneella voi olla rajattomasti sivuja, vaikka olisi vain yksi IP-osoite.
- Todellisuudessa domain pitää ostaa toimittajalta, mutta testaukseen riittää hosts-tiedoston muokkaus.

## Apachen asennus ja localhostin testaus
- Asensin Apachen tunnilla Johannan ohjeiden mukaisesti. eli komennolla:
```sudo apt-get install apache2```

- Tämän jälkeen tarkistin statuksen komennolla:
```sudo systemctl status apache2```
Status oli aktiivinen (running) ja siksi jatkoin eteenpäin
<img width="949" height="478" alt="Screenshot from 2025-09-07 21-29-24" src="https://github.com/user-attachments/assets/447c01a2-1c57-4825-8351-196be93ab42d" />


- Tarkistin että Apache2 käynnistyy automaattisesti, kun kone käynnistyy
<img width="912" height="111" alt="Screenshot from 2025-09-07 21-31-26" src="https://github.com/user-attachments/assets/626d5697-dd21-4a08-be90-d41ecd33977e" />

- Testasin localhostia curlilla komennolla ```curl http://localhost```, se ei aluksi toiminut, mutta jälkeenpäin muistin että olin config filessa joskus vaihtanut oletusportin (80) toiseen porttiin omia testauksia varten joka on nykyään (2222) ja korjasin komennon ```curl http://localhost:2222```
<img width="939" height="317" alt="Screenshot from 2025-09-07 21-34-21" src="https://github.com/user-attachments/assets/4b180f96-efda-4cca-a209-7d37ecd618da" />

## Lokien analyysi 

- Tämän jälkeen päätin vaihtaa oletusportiksi taas 80, jotta localhostin haku toimisi oikein ja jotta lokien katsominen onnistuisi
<img width="933" height="992" alt="Screenshot from 2025-09-07 21-49-50" src="https://github.com/user-attachments/assets/47ba5248-0007-4656-8f5a-d59e88f59a6d" />

- Sain lokit auki komennolla ```sudo vim /var/log/apache2/access.log```
<img width="939" height="84" alt="Screenshot from 2025-09-07 21-49-09" src="https://github.com/user-attachments/assets/76c433be-abf0-40f8-8edc-e2a7ab101d16" />

- ```127.0.0.1```: IP-osoite
- ```-``` : identiteetti, joka on tyhjä
- ```-``` : käyttäjänimi, joka on tyhjä
- ```[07/Sep/2025:21:48:35 +0300]``` : aikaleima, jolloin palvelin vastaanotti pyynnön
- ```"GET / HTTP/1.1"``` : Pyyntö HTTP-metodi (GET), resurssi (/), ja protokollaversio (HTTP/1.1)
- ```200``` : statuskoodi, OK: pyyntö onnistui
- ```10926``` : vastauksen koko tavuina (10,9kB)
-  ```-``` : sivu, jolta pyyntö tuli
- ```"curl/7.81.0"``` : asiakasohjelman tunniste. Tässä curl.

## Uusi name-based Virtual Host


  
## Lähteet
- https://httpd.apache.org/docs/2.4/logs.html#common
- https://datatracker.ietf.org/doc/html/rfc7231
- Linuxin asentaminen: https://terokarvinen.com/2021/install-debian-on-virtualbox/
