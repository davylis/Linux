
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

## Vanha Labra(Huomasin tämän liian myöhään! Odota arvioija jooko teen tänään (tiistai) aikana!!!)
Työstön alla



## Lähteet
- Shell Scripting. Tero Karvinen. Luettavissa: [https://httpd.apache.org/docs/2.4](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2007/12/04/shell-scripting-4/)
- Linux shell scripting basics. Johanna Heinonen. Luettavissa: [https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-01102025.md)
- Build own command in Linux. Geeksforgeeks. Luettavissa: https://www.geeksforgeeks.org/linux-unix/how-to-build-your-own-commands-in-linux/
- ChatGPT: käyttö termien hiontaan ja tehtävän tarkistukseen.



