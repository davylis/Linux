# Tehtävä h6

- Tein harjoituksen kotona. Käytin tehtävän tekoon Mac:ia.

## Artikkelin tiivistelmä
### Let's Encrypt 2024
- Let's Encrypt on ilmainen, automatisoitu varmenteenmyöntäjä
- Se käyttää ACME-protokollaa (Automatic Certificate Management Environment) varmistaakseen, että pyytäjä hallitsee verkkotunnusta.
- Sertifikaatin hankinta perustuu kolmeen vaiheeseen: Asiakasohjelma pyytää varmenteen, tarkistetaan domainin hallinnan (esim. HTTP- tai DNS-todistus) ja jos tarkistus onnistuu, myönnetään TLS-sertifikaatti.
- Sertifikaatit ovat lyhytikäisiä, joten uusiminen täytyy automatisoida.
-Tärkeät hakemistot: / juurihakemisto(root), /home/ käyttäjien kotihakemistot, /etc/ järjestelmän asetukset, /var/log/ lokit.
-Ylläpito ja ohjelmien asennus: ```sudo``` tarvitaan järjestelmätason muutoksiin. ```apt-get``` paketinhallintaan (päivitykset, haku, asennus, poisto).

### Lange 2024

- Lego-työkalulla voi hakea Let's Encrypt -sertifikaatin, vaikka Apache tai muu palvelin olisi jo käynnissä.
- Käytetään --http.webroot -parametria, joka osoittaa palvelimen juurihakemistoon.
- Lego luo vahvistustiedoston sinne ja Let's Encrypt voi hakea sen HTTP-yhteydellä ja todentaa domainin hallinnan.
- Sertifikaatti tallennetaan hakemistoon, jonka Lego määrittää (--path).

### Apache Software Foundation 2025
- Apache tarvitsee perusasetukset, jotta HTTPS toimii: SSLEngine ottaa TLS:n käyttöön, SSLCertificateFile viittaa palvelimen julkiseen sertifikaattiin, SSLCertificateKeyFile viittaa yksityiseen avaimeen.
- Asetukset sijoitetaan <VirtualHost *:443> -lohkoon.

## Let's asennus ja TLS-sertifikaatti
- Lähdetään asentamaan ohjelmaa komennolla ```sudo apt install lego``` 
<img width="1231" height="1167" alt="Screenshot 2025-09-24 at 18 35 07" src="https://github.com/user-attachments/assets/4a547ca8-591b-48e7-9fec-6c71835fca4a" />

- Luodaan TLS sertifikaatti, mutta hupsista, portti 80 on jo käytössä. Otetaan defaultti sitti pois paaltä ja apache alas niin lego pystyy käyttämään sitä.
<img width="1246" height="558" alt="Screenshot 2025-09-24 at 19 06 48" src="https://github.com/user-attachments/assets/e95c139d-9998-4e49-b888-6d655c3b7252" />

-  Sertifikaatti luotuna
<img width="1243" height="527" alt="Screenshot 2025-09-24 at 19 09 36" src="https://github.com/user-attachments/assets/124173cb-6df7-4254-8072-8f13461bb352" />

- Ne näkyy nyt legon polussa.
<img width="1219" height="172" alt="Screenshot 2025-09-24 at 19 11 05" src="https://github.com/user-attachments/assets/acfeb9ea-5844-4eb0-9a8f-27e33728f910" />

- Siirretään ne apachen polkuun, niin se pääsee käyttämään niitä vapaasti.
<img width="1247" height="117" alt="Screenshot 2025-09-24 at 19 13 01" src="https://github.com/user-attachments/assets/9bf6f22f-5b4c-475a-88f2-91c290d7e125" />

- Tehdään tiedostot niin että ne ovat turvallisesti luettavissa vain rootille ja Apachelle. Muut käyttäjät eivät pääse käsiksi yksityiseen avaimiin.
<img width="1245" height="84" alt="Screenshot 2025-09-24 at 19 14 39" src="https://github.com/user-attachments/assets/07ce9381-6983-4e52-a970-5d71d8927519" />

- Lisätään tarvittavat konfiguraatiot config fileen
<img width="1022" height="422" alt="Screenshot 2025-09-24 at 19 16 27" src="https://github.com/user-attachments/assets/d234b24f-8ff5-4281-ae4f-14c693a50f39" />

- Config testi meni läpi! Jes!
<img width="1239" height="144" alt="Screenshot 2025-09-24 at 19 15 13" src="https://github.com/user-attachments/assets/4dd0ecd3-c7c6-4bbe-bc12-8d40e117da79" />

- Käynnistetään apache uudelleen
<img width="1245" height="604" alt="Screenshot 2025-09-24 at 19 20 49" src="https://github.com/user-attachments/assets/c42b5158-2777-49ff-8fda-d7ac88595e0c" />

- davylis.com on nyt suojattu, mutta mietin pitkään, miksei www.davylis.com toimi. Syyksi osoittautui koneeni DNS Cache ja piti vain kokeilla puhelimen kautta :)
<img width="1030" height="245" alt="Screenshot 2025-09-24 at 23 14 09" src="https://github.com/user-attachments/assets/4369b083-c093-4f32-a281-4db2f3f59276" />
<img width="836" height="450" alt="Screenshot 2025-09-24 at 23 15 01" src="https://github.com/user-attachments/assets/1ff48054-33a4-4432-9177-d7778f4481b9" />

- Lisäsin myös ```Redirect permanent / https://davylis.com/``` config fileen, jotta https tulisi automaattisesti, ettei tarvitsisi kirjoittaa sitä hakuun.
<img width="844" height="309" alt="Screenshot 2025-09-24 at 23 16 52" src="https://github.com/user-attachments/assets/6038bafd-b385-4a26-87db-583f62a01cdf" />

## TLS Testaus
- davylis.com
<img width="1085" height="1114" alt="Screenshot 2025-09-24 at 23 17 58" src="https://github.com/user-attachments/assets/6cf99abc-d5ed-4b0c-b176-d6eafeeb910e" />

## Haavoittuvuustesti

---

## Lähteet
- Let's Encrypt. 2024. https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited](https://letsencrypt.org/how-it-works/
- Lange. 2024. https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server
- Apache Software Foundation. 2025. https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample
- https://github.com/terokarvinen/palettero

