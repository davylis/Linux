
# Tehtävä h4

- Tein harjoituksen omalla kotikoneella ilman virtuaalikonetta. Tämä kone on MAC:illa:


## Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla
- Palvelin vuokrataan pilvipalveluntarjoajalta (esim. UpCloud, DigitalOcean)
- Valitaan käyttöjärjestelmä (esim. Linux ja esim. Ubuntu)
- Kirjaudutaan palvelimelle SSH:lla ja otetaan ensimmäiset asetukset käyttöön

### Palvelin suojaan palomuurilla
- Palomuuri rajoittaa, mihin portteihin palvelimella voi tehtä yhteyksiä
- Asetetaan säännöt esim. sallimaan ssh (22) ja http (80)
- Tyypillinen työkalu on ufw, jolla hallinta on yksinkertaista

### Kotisivut palvelimelle
- Asennetaan web-palvelin (esim. Apache)
- Palvelin näyttää aluksi testisivun, joka vaihdetaan omilla sivuilla
- Sivujen näkyminen testataan eri laitteilla, myös palvelimen ulkopuolelta

### Palvelimen ohjelmien päivitys
- Ohjelmien säännöllinen päivitys on tärkeää tietoturvan kannalta
- Päivitykset tehdään komennoilla ```sudo apt-get update && sudo apt-get upgrade```
- Palvelin voidaan tarvittaessa käynnistää uudelleen, jotta päivitykset tulevat voimaan

## Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
- Ensimmäiseksi palvelin vuokrataan ja siihen kirjaudutaan ssh:lla
- Luodaan uusi käyttäjä ja annetaan tälle sudo-oikeudet, jotta root-tunnusta ei tarvita
- Root-käyttäjä suljetaan tietoturvan parantamiseksi
- Palomuuri (ufw) otetaan käyttöön, sallitaan tarvittavat portit
- Päivitetään ohjelmat heti alussa (apt-get update ja upgrade)
- Asennetaan web-palvelin ja testataan, että sivu näkyy julkisesti
- Artikkeli painottaa hyvää tietoturvakäytäntöä (salasanat, SSH-avaimet)

## Palvelimen vuokraus(prosessi)
- Ajattelin että teen tämän tehtävän vähän eri tavalla(pikku riski, kun ei ole tehtävänannon mukaan, mutta kokeillaan!) + Github Education ei toimi
- Eli sanotaan näin että vuokrasin mun aviomiehen meidän kotipalvelimesta virtuaalipalvelimen
- Meidän palvelin on hallinnassa Proxmoxin kautta, jossa hallitaan portteja, virtuaalipalvelimia ja muita servicejä.
- Luodaan uusi virtuaalikone(virtuaalipalvelin)

  <img width="1598" height="899" alt="Screenshot 2025-09-17 at 16 56 07" src="https://github.com/user-attachments/assets/68f559c4-d955-4350-8519-836e41af7125" />
  
- Koneen asetukset
<img width="2196" height="857" alt="Screenshot 2025-09-17 at 16 59 18(1)" src="https://github.com/user-attachments/assets/68b69319-27a8-425b-b756-5cc6bafe052d" />

- Minun root kirjautuminen jäi tästä välistä(huomasin vasta jälkikäteen, mutta harjoituksen vuoksi teen samat asetukset ja uuden sudo käyttäjän)
<img width="1137" height="1156" alt="Screenshot 2025-09-17 at 20 08 06" src="https://github.com/user-attachments/assets/b59e9f3f-31c1-4ba2-b1a3-1f75cf114def" />

- Otetaan käyttöön palomuuri ja sallitaan portti 22
<img width="1191" height="90" alt="Screenshot 2025-09-17 at 20 07 20" src="https://github.com/user-attachments/assets/615fabee-a1df-4b99-86d1-fe0a97fdd13b" />

<img width="1256" height="122" alt="Screenshot 2025-09-17 at 20 06 38" src="https://github.com/user-attachments/assets/50dcac2f-607f-4cb1-be06-7b7163f23dab" />

- Uuden sudo käyttäjän luonti ja annetaan sille tarvittavat oikeudet
<img width="1145" height="785" alt="Screenshot 2025-09-17 at 18 19 28" src="https://github.com/user-attachments/assets/ee40d1c9-8e34-487c-b50d-8368cddf9c2d" />

- Testataan uusi sudo käyttäjä ja kirjautuminen
<img width="1194" height="376" alt="Screenshot 2025-09-17 at 21 59 38" src="https://github.com/user-attachments/assets/8578841b-6bd9-45ef-86a4-697a9e48072c" />

- Suljetaan root käyttäjä
<img width="926" height="65" alt="Screenshot 2025-09-17 at 18 29 52" src="https://github.com/user-attachments/assets/ddfaec79-8aad-4e15-ad3d-f1aca53ba806" />

- Otetaan pois käytöstä ssh kirjautuminen rootilta
<img width="983" height="253" alt="Screenshot 2025-09-17 at 18 29 11" src="https://github.com/user-attachments/assets/f8b2bd3a-c6f4-4837-9315-d838b894c6f6" />

- Tehdään kaikki ohjelmapäivitykset
<img width="1229" height="329" alt="Screenshot 2025-09-17 at 18 30 41" src="https://github.com/user-attachments/assets/fd1e7da0-9566-45c6-b957-c0c96d0e381c" />

- Aloitetaan käyttö, lataamalla julkinen palvelin Apache. Tehdään myös palomuuri ja sallitaan portti 80(terminaalissa ei näy, mutta lisään kuvan kun palaan kotiin:D)
<img width="1179" height="240" alt="Screenshot 2025-09-17 at 18 37 08" src="https://github.com/user-attachments/assets/ecdaaa8b-4205-40c2-a8e3-134c1a03fd1d" />

- Testataan meidän nettisivu! Kännykällä toimii myös!
<img width="1208" height="120" alt="Screenshot 2025-09-17 at 18 48 39" src="https://github.com/user-attachments/assets/9fb26ae8-52f1-4478-a01f-edc256276a64" />


## Lähteet
- First Steps on a New Virtual Private Server. Tero Karvinen. Luettavissa: https://httpd.apache.org/docs/2.4](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
- Teoriasta käytäntöön pilvipalvelimen avulla. Susanna Lehto. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/
- Proxmox VE Documentation. Luettavissa: https://pve.proxmox.com/pve-docs/
- ChatGPT: käyttö termien hiontaan ja tehtävän tarkistukseen.



