# Tehtävä h5

### Julkinen nimi osoittamaan koneeseeni
<img width="963" height="362" alt="Screenshot 2025-09-22 at 21 41 53" src="https://github.com/user-attachments/assets/93a7065a-01ac-4d46-acd5-a9a46b0470b9" />

- Lisäsin uuden tietuen, joka osoittaa palvelimeni IP-osoitteeseen. Lisäsin ```@``` osoittamaan että se on päädomain. Lisäsin aluksi Proxy statuksen ```proxied```, jotta se välittyisi cloudflaren kautta, mutta sain virheeksi 521, eli domainin osoitus ei onnistu. Kokeilin vaihtaa ```DNS only```, ja odotin muutaman minuutin, mutta sekään ei toiminut. Sitten tajusin etten ollut laittanut alkuun http:// :DDD
<img width="1264" height="439" alt="Screenshot 2025-09-22 at 21 41 34" src="https://github.com/user-attachments/assets/7c32e9d4-c502-4024-9e10-960e7d9eb43a" />
  
### Alidomainit
- Loin kaksi uutta alidomainia

<img width="965" height="415" alt="Screenshot 2025-09-22 at 21 47 58" src="https://github.com/user-attachments/assets/2b45e59a-f268-4179-a0a3-ea92fd5fe6d0" />

### Tutkitaan
#### Oma Domain
- ```host davylis.com``` komennolla tarkastelen damainin IP-osoitteita ja mahdollisia muita tietoja
<img width="1242" height="93" alt=" " src="https://github.com/user-attachments/assets/e4d73c23-750b-4559-b415-c06896692b8d" />

- ```dig davylis.com``` komento antaa kattavan tiedon domainin DNS-tietuista
<img width="926" height="150" alt="Screenshot 2025-09-22 at 21 55 44" src="https://github.com/user-attachments/assets/62f9bda1-1979-41b0-864d-9a889e8e355f" />

- Näyttää vain A-tietuet, ei AAAA ilman erillistä kyselyä.
<img width="684" height="113" alt="Screenshot 2025-09-22 at 22 00 11" src="https://github.com/user-attachments/assets/53310505-f7ec-4687-9a62-681930310729" />

#### HarrasteDomain
- Tässä näkyy jo A-tietuet ja MX-tietue
<img width="1207" height="108" alt="Screenshot 2025-09-22 at 22 03 03" src="https://github.com/user-attachments/assets/1ac6bcde-6360-432a-999e-8b0fc95febf6" />
- Näkyy A-tietuet ja voidaan erillisestä hake myös s-postin tietuet komennolla ```dig terokarvinen.com MX```

<img width="1070" height="608" alt="Screenshot 2025-09-22 at 22 04 56" src="https://github.com/user-attachments/assets/808744d1-6b91-475a-af56-a3a42d33dc6b" />

<img width="1134" height="619" alt="Screenshot 2025-09-22 at 22 05 41" src="https://github.com/user-attachments/assets/71997611-236a-43a5-81ff-fdaec615e937" />

#### Suuri palvelu
- Näyttää useita A-tietueita ja MX
<img width="1223" height="177" alt="Screenshot 2025-09-22 at 22 07 22" src="https://github.com/user-attachments/assets/26a8cee4-eec8-447e-b7f6-15fb40371fe2" />

- Palauttaa A-tietueet ja nimipalvelimen ja lisätiedot
- TTL:t, serverin vastaukset ja syvällisempi analyysi.

<img width="1117" height="949" alt="Screenshot 2025-09-22 at 22 08 55" src="https://github.com/user-attachments/assets/1cfd166d-4fa1-4436-ade4-db0027464a86" />

## Lähteet
- https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited](https://www.geeksforgeeks.org/techtips/how-to-use-cloudflare/
- https://terokarvinen.com/2009/command-line-basics-4/](https://docs.hetzner.com/cloud/servers/getting-started/connecting-to-the-server/
- https://commandmasters.com/commands/host-common/
- https://linuxize.com/post/how-to-use-dig-command-to-query-dns-in-linux/
