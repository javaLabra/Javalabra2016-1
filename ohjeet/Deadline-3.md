# Deadline 3

### Ohjelma selkeästi edennyt

* Ohjelmoinnin tulee edistyä viikottain

### Noudata Clean code -periaatteita

* Jos koodia on syntynyt useita luokkia, kannattaa jakaa koodi loogisiin paketteihin [laatuvaatimusten](Koodin-laatuvaatimukset.md) mukaisesti

### JUnit-yksikkötestit

* Uusia luokkia ja metodeja testattu
* Jokaisen luokan testit on määritelty omassa testiluokassaan
  * Jos jaoit koodin paketteihin, huomioi myös testipakettien nimentä
* Yhtä luokkaa kohti saa olla myös useita testiluokkia
* Poista viime viikon pit-raportti ja generoi uusi sen tilalle.
  * [ohjeet](Maven-ja-PIT.md#raportit)
  * Logiikan rivikattavuus olisi hyvä olla jo >70%.

### Generoi PIT-raportti uudestaan
* Generoi uudestaan PIT-raportti
* Lisää uusi generoitu raportti dokumentaatioon

### Luokkakaavio
* Tarkenna ohjelman luokkakaaviota tai piirrä uusi kuvaamaan nykyistä rakennetta
* Merkitse kytkentärajoitteet
* Lähtökohdaksi voi ottaa ohjelmakoodinsa

### CheckStyle 
* Generoi uusi CheckStyle-raportti
* Korjaa kaikki esiintyvät CheckStyle-virheet (tästä eteenpäin oletetaan, ettei raportissa olisi enää virheitä)
* Käyttöliittymä-luokkien kuten Swing-komponenttien testaus checkstylellä ei ole tarpeen, seuraa [näitä ohjeita](Checkstyle.md#deadline-3-luokkien-jättäminen-checkstylen-ulkopuolelle) jättääksesi UI-luokat checkstylen ulkopuolelle

### README.md
* Linkataan tällä viikolla myös pit- ja CheckStyle-raportit README.md:stä. Tähän käytetään [htmlpreviewiä](https://htmlpreview.github.io/)
* Htmlpreviewiä käyttäen, linkkaa README.md:hen pit-raporttisi index.html ja CheckStyle-raporttisi checkstyle.html. 
* Linkki pit-raporttiisi olisi siis esimerkiksi tälläinen: https://htmlpreview.github.io/?https://github.com/kayttaja/javalabra/blob/master/documentation/pit-reports/index.html
* Muista päivittää linkki viikottain ja linkata aina uusin versio raporteistasi
