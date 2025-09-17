
# Tehtävä h4

- Tein harjoituksen omalla kotikoneella ilman virtuaalikonetta. Omalla koneellani on Linux:

```console
OS Name:          Zorin OS 17.3
OS Version:       17
Kernel Version:   6.8.0-65-generic
System Type:      x86_64
```


## Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla
- Palvelin vuokrataan pilvipalveluntarjoajalta (esim. UpCloud, DigitalOcean).
- Valitaan käyttöjärjestelmä (yleensä Linux, esim. Ubuntu).
- Kirjaudutaan palvelimelle SSH:lla ja otetaan ensimmäiset asetukset käyttöön.

### Palvelin suojaan palomuurilla
- Palomuuri rajoittaa, mihin portteihin palvelimelle voi ottaa yhteyksiä.
- Asetetaan säännöt esim. sallimaan SSH (22) ja HTTP (80).
- Tyypillinen työkalu on ufw, jolla hallinta on yksinkertaista.

### Kotisivut palvelimelle
- Asennetaan web-palvelin (esim. Apache tai Nginx).
- Palvelin näyttää aluksi testisivun, joka vaihdetaan omilla sivuilla.
- Sivujen näkyminen testataan eri laitteilla, myös palvelimen ulkopuolelta.

### Palvelimen ohjelmien päivitys
- Ohjelmien säännöllinen päivitys on tärkeää tietoturvan kannalta.
- Päivitykset tehdään komennoilla sudo apt-get update ja sudo apt-get dist-upgrade.
- Palvelin voidaan tarvittaessa käynnistää uudelleen, jotta päivitykset tulevat voimaan.

## Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
- Ensimmäiseksi palvelin vuokrataan ja siihen kirjaudutaan SSH:lla.
- Luodaan uusi käyttäjä ja annetaan tälle sudo-oikeudet, jotta root-tunnusta ei tarvita.
- Root-käyttäjä suljetaan tietoturvan parantamiseksi.
- Palomuuri (ufw) otetaan käyttöön, sallitaan tarvittavat portit.
- Päivitetään ohjelmat heti alussa (apt-get update ja upgrade).
- Asennetaan web-palvelin ja testataan, että sivu näkyy julkisesti.
- Artikkeli painottaa hyvää tietoturvakäytäntöä (salasanat, SSH-avaimet).


## Palvelimen vuokraus
- Ajattelin että teen tämän tehtävän vähän eri tavalla(pikku riski, kun ei ole tehtävänannon mukaan, mutta kokeillaan!) + Github Education ei toimi
- Eli sanotaan näin että vuokrasin mun aviomiehen meidän kotipalvelimesta virtuaalipalvelin.
- Meidän palvelin on hallinnassa Proxmoxin kautta, jossa hallitaan portteja, virtuaali palvelimia ja muita servicejä.
- Luodaan uusi virtuaalikone(virtuaalipalvelin)
  <img width="1598" height="899" alt="Screenshot 2025-09-17 at 16 56 07" src="https://github.com/user-attachments/assets/68f559c4-d955-4350-8519-836e41af7125" />
  
- Koneen asetukset
<img width="2196" height="857" alt="Screenshot 2025-09-17 at 16 59 18(1)" src="https://github.com/user-attachments/assets/68b69319-27a8-425b-b756-5cc6bafe052d" />

- Kirjaudutaan sisään ensimmäisen kerran
<img width="1137" height="1156" alt="Screenshot 2025-09-17 at 20 08 06" src="https://github.com/user-attachments/assets/b59e9f3f-31c1-4ba2-b1a3-1f75cf114def" />

-Firewall reikä
<img width="1191" height="90" alt="Screenshot 2025-09-17 at 20 07 20" src="https://github.com/user-attachments/assets/615fabee-a1df-4b99-86d1-fe0a97fdd13b" />

<img width="1256" height="122" alt="Screenshot 2025-09-17 at 20 06 38" src="https://github.com/user-attachments/assets/50dcac2f-607f-4cb1-be06-7b7163f23dab" />

- Sudo käyttäjän luonti
<img width="1145" height="785" alt="Screenshot 2025-09-17 at 18 19 28" src="https://github.com/user-attachments/assets/ee40d1c9-8e34-487c-b50d-8368cddf9c2d" />

VIRHE

- Suljetaan root käyttäjä
<img width="926" height="65" alt="Screenshot 2025-09-17 at 18 29 52" src="https://github.com/user-attachments/assets/ddfaec79-8aad-4e15-ad3d-f1aca53ba806" />

<img width="983" height="253" alt="Screenshot 2025-09-17 at 18 29 11" src="https://github.com/user-attachments/assets/f8b2bd3a-c6f4-4837-9315-d838b894c6f6" />

- Ohjelmien päivitys
<img width="1229" height="329" alt="Screenshot 2025-09-17 at 18 30 41" src="https://github.com/user-attachments/assets/fd1e7da0-9566-45c6-b957-c0c96d0e381c" />

- Aloitetaan käyttö!
<img width="1179" height="240" alt="Screenshot 2025-09-17 at 18 37 08" src="https://github.com/user-attachments/assets/ecdaaa8b-4205-40c2-a8e3-134c1a03fd1d" />




<img width="1208" height="120" alt="Screenshot 2025-09-17 at 18 48 39" src="https://github.com/user-attachments/assets/9fb26ae8-52f1-4478-a01f-edc256276a64" />








## Lähteet
- Apache Documentation. Luettavissa: https://httpd.apache.org/docs/2.4
- Tero Karvinen. Name Based Virtual Hosts on Apache. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
- https://httpd.apache.org/docs/2.4/vhosts/name-based.html
- Johanna Heinonen. 2025. Apache2. Luettavissa: https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-03092025.md
- ChatGPT: käyttö termien hiontaan ja tehtävän tarkistukseen.

