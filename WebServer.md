
# Tehtävä h3

- Tein harjoituksen omalla kotikoneella ilman virtuaalikonetta. Omalla koneellani on Linux:

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

## Uusi name-based Virtual Host ja validi HTML-sivu
- Loin kansion uudelle sivulle tarvittaessa, jos sitä ei ole vielä olemassa komennolla ```mkdir -p ~/public_html/hat```
- Tämän jälkeen loin uuden html sivun komennolla ```vim ~/public_html/hat/index.html```
<img width="611" height="338" alt="Screenshot from 2025-09-08 10-54-56" src="https://github.com/user-attachments/assets/2220afcb-bb18-43c8-a49d-2890383b6d34" />

- Sitten luodaan uusi Virtual Host tiedosto config-filella komennolla ```sudo vim /etc/apache2/sites-available/hat.conf```
- Tämä tiedosto kertoo Apachessa, että kaikki pyynnöt hat.davydov.com-osoitteeseen ohjataan tähän hakemistoon.
- Tiedostoon lisätään:
-Portin tiedot: ```80```
-Domain nimi: ```hat.davydov.com```
-Hakemisto, josta sisältö palvellaan: ```/home/davylis/public_html/hat```
-sallii .htaccess-määritykset, tarvittaessa:  ```AllowOverride All```
-sallii kaikille pääsyn hakemistoon: ```Require all granted```

- Poistetaan oletussivu ja lisätään uusi sivu
- Ennen tätä tarkistan mikä oletussivu minulla on juuri nyt käytössä komennolla ```ls -l /etc/apache2/sites-enabled/```
<img width="956" height="104" alt="Screenshot from 2025-09-08 11-18-14" src="https://github.com/user-attachments/assets/2b628791-0bf0-4420-a9bf-1f95839ebab0" />

- Tämän jälkeen poistan vanhan oletussivun käytöstä, otan uuden sivun käyttöön ja reboottaan apachen komennoilla:
```
sudo a2dissite 000-default.conf
sudo a2ensite hat.conf
sudo systemctl restart apache2
```

- Lisätään hosts tiedostoon simulaatio, kun ei ole vielä omaa domainia käytössä
```
sudo vim /etc/hosts
```
- ja tiedostossa vaihdetaan localhost meidän uuteen sivuun eli ```hat.davydov.com```
- Testataan sivu curlilla ja selaimessa:
![Uploading Screenshot from 2025-09-08 14-18-39.png…]()

## curl-hakemistot
- curl on komentorivityökalu, jolla voidaan tehdä HTTP-pyyntöjä. Se hakee verkkopalvelimelta tiedostoja ja tietoja kuten edellisessä esimerkissä näkyy.
- ```curl -I http://hat.davydov.com``` hakee vain HTTP- otsikot(HEAD-pyyntö)
<img width="848" height="243" alt="Screenshot from 2025-09-08 11-42-44" src="https://github.com/user-attachments/assets/0cf04f9a-9a33-467e-8783-ccfe58adfb55" />

- Pyyntö onnistui: ```200```
- Pyynnön kellonaika
- Palvelinohjelmisto
- Palvelin lähettää html


## Molemmat sivut samalle IP-osoitteelle
- Minulla on molemmat hakemistot ja sivut luotuna
 <img width="941" height="149" alt="Screenshot from 2025-09-08 13-56-32" src="https://github.com/user-attachments/assets/8c317777-7fff-43ed-b8fa-9fdca60f59dd" />

- Config files myös ovat valmiita
<img width="940" height="170" alt="Screenshot from 2025-09-08 13-58-03" src="https://github.com/user-attachments/assets/dd04f12b-c0de-43de-a81f-551be6a3e526" />

- Otan molemmat sivut käyttöön komennoilla:
```
sudo a2ensite hat.conf
sudo a2ensite sitel.com.conf
sudo systemctl restart apache2
```

- Lisään molemmat sivut samalle IP-osoitteelle simulaatioon
```
sudo vim /etc/hosts
```
<img width="937" height="77" alt="Screenshot from 2025-09-08 14-01-12" src="https://github.com/user-attachments/assets/7a4f30cc-8e88-48fe-8132-20fb20a82bb4" />

- sama Apache-palvelin palvelee kahta eri verkkotunnusta:
```
hat.davydov.com
site1.com
```

- Molemmat näyttävät eri sivuja, vaikka käytetään samaa IP-osoitetta.
<img width="920" height="312" alt="Screenshot from 2025-09-08 14-04-59" src="https://github.com/user-attachments/assets/dfa117ac-fa40-4041-a9cb-a228c6c3878f" />

  
## Lähteet
- https://httpd.apache.org/docs/2.4/logs.html#common
- https://datatracker.ietf.org/doc/html/rfc7231
- Linuxin asentaminen: https://terokarvinen.com/2021/install-debian-on-virtualbox/
- https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
- https://httpd.apache.org/docs/2.4/vhosts/name-based.html
- https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-03092025.md
