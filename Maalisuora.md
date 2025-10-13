
# Tehtävä h7

- Tein harjoituksen omalla kotikoneella ilman virtuaalikonetta. Tämä kone on MAC:illa:

## Hei maailma kolemlla kielellä 

### python
- Luodaan tiedosto ```hello.py``` ja kirjoitetaan koodipätkä
<img width="473" height="198" alt="Screenshot 2025-10-07 at 10 50 26" src="https://github.com/user-attachments/assets/48dda431-c25f-48a6-94b1-0c9a67d4300b" />


### bash
- Luodaan tiedosto ```hello.py``` ja kirjoitetaan koodipätkä
<img width="528" height="260" alt="Screenshot 2025-10-07 at 10 50 45" src="https://github.com/user-attachments/assets/a099955c-bedf-4d82-94cd-59b18c76d5ef" />
  
### c
- Luodaan tiedosto ```hello.py``` ja kirjoitetaan koodipätkä
  <img width="667" height="458" alt="Screenshot 2025-10-07 at 10 51 05" src="https://github.com/user-attachments/assets/465bd22f-f912-479d-9a8b-d413396c8272" />

- Ja sen jälkeen ajetaan ohjelmat:
<img width="1236" height="604" alt="Screenshot 2025-10-07 at 10 50 10" src="https://github.com/user-attachments/assets/c8535652-a6d9-4f24-bda2-cfc86579f20c" />


## Oma Linuxkomento

- Luodaan komento ```levytarkistus```
- Ajattelin että tälläinen komento olisi tarpeen, koska itselläni meinaa muisti loppua koko ajan:D
- Komento näyttää levyn käytön ja suurimman kansion käyttäjän kotihakemistossa.
- Skriptin sisältö:
<img width="1073" height="570" alt="Screenshot 2025-10-07 at 11 27 40" src="https://github.com/user-attachments/assets/e4be212c-97ce-4ff3-866a-22ce56937776" />

- Annetaan tiedostolle suoritusoikeus (eli tehdään siitä ohjelma/komento) ```chmod +x levytarkistus```
- Suoritetaan skripti ```./levytarkistus```
<img width="1217" height="578" alt="Screenshot 2025-10-07 at 11 28 55" src="https://github.com/user-attachments/assets/da9b9dc9-e021-46ac-87f6-29c5165dfe67" />

- Kopioidaan skripti kaikkien käyttäjien näkyvään komentohakemistoon ```sudo cp levytarkistus /usr/local/bin/levytarkistus```
- Muutetaan tiedoston omistajaksi root-käyttäjä ja root-ryhmä ```sudo chown root:root /usr/local/bin/levytarkistus```
- Asetetaan tiedoston oikeudet, että kaikki voivat ajaa, mutta vain root voi muokata ```sudo chmod 755 /usr/local/bin/levytarkistus```
<img width="1240" height="319" alt="Screenshot 2025-10-07 at 11 29 12" src="https://github.com/user-attachments/assets/379a698f-d23d-4937-9793-bc292217f8dd" />

- Katsotaan tiedoston tiedot(omistajat ja oikeudet) ```ls -l /usr/local/bin/levytarkistus```
- Nähdään että omistajan root oikeudet ovat luku, kirjoitus, suoritus, ryhmän root oikeudet ovat luku ja suoritus ja muilla käyttäjillä luku ja suoritus ```-rwxr-xr-x 1 root root 305 Oct  7 11:21 /usr/local/bin/levytarkistus```
<img width="1233" height="86" alt="Screenshot 2025-10-07 at 11 29 28" src="https://github.com/user-attachments/assets/e7f4453c-1daf-4187-a5c0-a52d05450582" />

## Vanha Labra : Final Lab for Linux Palvelimet 2024 Spring(SOS! HUOMASIN TÄMÄN LIIAN MYÖHÄÄN :(( TEHTÄVÄ KESKEN VIELÄ)
- Luodaan raportti
<img width="1151" height="120" alt="Screenshot 2025-10-08 at 18 02 30" src="https://github.com/user-attachments/assets/29b4a214-8d9b-4a5d-ab7c-8dd51159ef0f" />

### b) Tiivistelmä koko työstä lopuksi
      
### c) Ei kolmea sekoseiskaa
- Asetettaan omistajaksi itseni kaiken varaksi komennolla ```sudo chown -R davylis:davylis report```
<img width="1126" height="66" alt="Screenshot 2025-10-08 at 18 03 22" src="https://github.com/user-attachments/assets/0093a1c6-3ee0-4fa1-9574-5a78766deb5d" />

- Suojataan raportti Linux-oikeuksilla niin, että vain oma käyttäjäni pystyy katselemaan raporttia.
- - Lisätään ```700``` ja ```600``` oikeudet
<img width="1165" height="182" alt="Screenshot 2025-10-08 at 18 03 54" src="https://github.com/user-attachments/assets/4b2f5ed3-ba1a-4c0f-a9e1-aa367abd3b0b" />

- Testaus: toionen käyttäjä ei näe raporttia
<img width="1165" height="89" alt="Screenshot 2025-10-08 at 18 05 05" src="https://github.com/user-attachments/assets/3f9b5bab-f27d-4b44-ae28-336198012bc9" />

### d) 'howdy'
- Tehdään kaikkien käyttäjien käyttöön komento 'howdy'
- Lisätään julkiset oikeudet
<img width="1098" height="38" alt="Screenshot 2025-10-08 at 18 05 27" src="https://github.com/user-attachments/assets/5a1ea8ea-c22f-4878-83eb-82620b2e02ac" />

- Testataan. Toinen käyttäjä pystyy käyttämään!
<img width="1268" height="473" alt="Screenshot 2025-10-08 at 17 58 39" src="https://github.com/user-attachments/assets/1b4fa871-0c79-43d0-a7ba-a151715ac9be" />

### e) Etusivu uusiksi
- Asennetaan apache komennolla ```sudo apt install apache2 -y```
- Tehdään uusi kotisivu "AI kaikone"
<img width="1181" height="123" alt="Screenshot 2025-10-13 at 14 04 54" src="https://github.com/user-attachments/assets/bd222d56-150d-4a8d-94a9-a8bb6eb79e73" />

<img width="1075" height="62" alt="Screenshot 2025-10-13 at 14 04 21" src="https://github.com/user-attachments/assets/1a77780b-aeef-46d3-ab71-e45289ed57d0" />

- Sallitaan muokkaus tavalliselle käyttäjälle komennolla ```sudo chown -R $davylis:$davylis /var/www/html```
- Testataan meidän IP-osoitteella
<img width="1179" height="86" alt="Screenshot 2025-10-13 at 14 08 27" src="https://github.com/user-attachments/assets/5f33bb9a-50d3-4b18-9075-017e04087551" />

### g) Salattua hallintaa
- Asennetaan ssh-palvelin
<img width="1119" height="126" alt="Screenshot 2025-10-13 at 14 13 47" src="https://github.com/user-attachments/assets/165772d5-36ea-4d42-977e-9cd2161b8443" />

- Luo uusi käyttäjä
<img width="1162" height="226" alt="Screenshot 2025-10-13 at 14 43 07" src="https://github.com/user-attachments/assets/33a3a484-8960-4756-956a-efa4813aa13c" />

- Luo ssh-avaimet
<img width="1143" height="92" alt="Screenshot 2025-10-13 at 14 44 19" src="https://github.com/user-attachments/assets/585ecef5-ecd5-46b1-8b7a-a1df6b061fc8" />

- Kopioidaan avain uudelle käyttäjälle
<img width="1022" height="118" alt="Screenshot 2025-10-13 at 14 42 02" src="https://github.com/user-attachments/assets/ee46a788-70a5-4990-b627-08c9ea405100" />

- Testataan
<img width="1183" height="884" alt="Screenshot 2025-10-13 at 14 41 33" src="https://github.com/user-attachments/assets/8e20d701-5965-4ba6-9625-0d603d8d4cca" />

### h) Django

- Asennetaan Python-virtuaaliympäristöpaketti
<img width="1182" height="177" alt="Screenshot 2025-10-13 at 14 50 25" src="https://github.com/user-attachments/assets/ef2d9fb6-6e65-4a15-91ff-849e6515bb87" />

- Luodaan virtuaaliympäristö komennolla ```python3 -m venv venv```
- Aktivoidaan komennolla ```source venv/bin/activate```
- Asennetaan Django ```pip install django```
- Luodaan uusi Django projekti ja siirrytään sinne
- Käynnistetään palvelin
<img width="1207" height="441" alt="Screenshot 2025-10-13 at 14 54 52" src="https://github.com/user-attachments/assets/dfdb75dc-2ce7-437a-9b71-81f39bbf00bf" />

- Testataan localhost
<img width="1247" height="901" alt="Screenshot 2025-10-13 at 14 47 56" src="https://github.com/user-attachments/assets/495f1956-32a4-4c1f-a5f5-003a1bb9a4ad" />

- Luodaan tietomalli, lisätään adminiin ja tehdään tietokanta ja admin käyttäjä
<img width="1222" height="38" alt="Screenshot 2025-10-13 at 15 19 17" src="https://github.com/user-attachments/assets/a7540c5c-34c0-4741-8c73-2d7c64b8d3cc" />
<img width="1123" height="33" alt="Screenshot 2025-10-13 at 15 19 02" src="https://github.com/user-attachments/assets/d4ae4982-ec93-4ac2-ae20-67381d3250d4" />
<img width="1143" height="664" alt="Screenshot 2025-10-13 at 15 19 58" src="https://github.com/user-attachments/assets/2e954e20-3902-4c46-b353-1470eafb9860" />


- Käynnistetään
<img width="1224" height="407" alt="Screenshot 2025-10-13 at 15 18 33" src="https://github.com/user-attachments/assets/25d10048-041e-46d7-b586-d2a89135ebcf" />
<img width="1214" height="1006" alt="Screenshot 2025-10-13 at 15 20 55" src="https://github.com/user-attachments/assets/00a4ca60-4cbf-4582-a1ed-c17cad3d6f83" />


### h) Tuotantopropelli
- Tehtävä jätetty väliin;(


## Lähteet
- Shell Scripting. Tero Karvinen. Luettavissa: [https://httpd.apache.org/docs/2.4](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2007/12/04/shell-scripting-4/)
- Linux shell scripting basics. Johanna Heinonen. Luettavissa: [https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-01102025.md)
- Build own command in Linux. Geeksforgeeks. Luettavissa: https://www.geeksforgeeks.org/linux-unix/how-to-build-your-own-commands-in-linux/
- ChatGPT: käyttö termien hiontaan ja tehtävän tarkistukseen.



