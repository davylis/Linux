# Tehtävä h1

## Artikkelin tiivistelmä
- Raportointi tarkoittaa, että kerrot täsmällisesti mitä teit, ja mitä sitten tapahtui.
- Raportin tulee olla täsmällinen, eli siinä on listattava kaikki komennot.
- Raportissa tulee kirjata ylös myös virheilmoitukset.
- Raportissa tulee merkitä lähteet.

## Linuxin asentaminen

- Tein harjoituksen lauantaina kotona. Omalla koneellani on Ubuntu, mutta harjoitusta varten käytin virtuaalikoneiden luomiseen Oraclea VirtualBoxia(joka oli valmiiksi ladattuna).

```console
OS Name:          Zorin OS 17.3
OS Version:       17
Kernel Version:   6.8.0-65-generic
System Type:      x86_64
```
- Ladataan materiaalissa käytettyä Debian 64-bittinen levykuva: https://cdimage.debian.org/debian-cd/13.0.0-live/amd64/iso-hybrid/debian-live-13.0.0-amd64-xfce.iso
  
- Loin uuden virtuaalikoneen NebulaCore:n ja asetin tarvittavat muistiasetukset ja kovalevyasetukset. Screenshotissa on 34-bittiä, mutta vaihdoin sen myöhemmin 64!

### Kone
- Name: NebulaCore
- ISO Image: debian-live-13.0.0-amd64-xfce.iso
- Type: Linux
- Subtype: Debian
- Version: Debian (64-bit)

### Laitteisto:
- Base Memory: 2048 MB
- Processors 1

### Kiintolevy:
- 25,00 GB 


<img width="1911" height="1071" alt="Screenshot from 2025-08-21 23-13-39" src="https://github.com/user-attachments/assets/ff7b74f8-b82c-43a2-944a-7700fad93666" />

- Käynnistin Debianin Livenä ja kaikki toimi moiteettomasti
  
<img width="1911" height="1071" alt="Screenshot from 2025-08-21 23-15-48" src="https://github.com/user-attachments/assets/30c845d6-741b-4c62-ad3f-af9e596567b9" />

- joten käynnistin Calamares installerin vasemmasta alakulmasta.
  
<img width="1911" height="1071" alt="Screenshot from 2025-08-21 23-29-25" src="https://github.com/user-attachments/assets/601eb126-55e0-4f87-999a-a8341a735213" />

- Valitsin kielet, näppäimistön, tyhjensin levyn, loin käyttäjätunnuksen ja salasanan.
  
### Sijainti:
- Region: Europe
- Zone: Helsinki

### Näppäimistö
- Finnish Default

### Osiot
- Erase disk
  
### Käyttäjät
- käyttäjätunnus
- salasana
  
<img width="1911" height="1071" alt="Screenshot from 2025-08-21 23-33-32" src="https://github.com/user-attachments/assets/24dbc5ab-752d-4581-b79f-7be3a9afa3ff" />

- Käynnistin virtuaalikoneen uudestaan ja nyt on koje käytössä.
- Lopuksi päiviin ohjelmistot ajan tasalle

```console
sudo apt update && sudo apt upgrade
```

<img width="1911" height="1071" alt="Screenshot from 2025-08-21 23-54-21" src="https://github.com/user-attachments/assets/547452b2-6761-4f56-ab02-f3e1a4c7c3c7" />

## Suosikkiohjelmani Linuxilla
- Vim, rakastan tehdä kaikki muistiinpanot sinne
- btop && htop, prosessin seuranta
- curl, web-pyynnöt terminaalin kautta
- nmap, porttiskanneri
- cmatrix tietenkin!!

  <img width="2002" height="1108" alt="Screenshot from 2025-08-25 01-57-19" src="https://github.com/user-attachments/assets/3c02f5ab-bb70-4f8f-9a1e-15843c6c811e" />

## Lähteet
- Tehtävänanto: https://terokarvinen.com/linux-palvelimet/#h1-oma-linux
- Raportin kirjoittaminen: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
- Linuxin asentaminen: https://terokarvinen.com/2021/install-debian-on-virtualbox/
