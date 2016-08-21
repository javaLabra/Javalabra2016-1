# Koodin laatuvaatimukset

Kurssin tavoitteena on, että tuotoksesi voisi ottaa kuka tahansa kaverisi tai muu opiskelija ylläpidettäväksi ja laajennettavaksi. Tavoitteena on Clean code - selkeää, ylläpidettävää ja toimivaksi testattua koodia. Tämä sivu esittelee erityisesti *lopullisen* palautuksen laatuvaatimukset, mutta lueteltuja vaatimuksia tulisi noudattaa mahdollisimman pian alussa.

### Clean Code

Alla luetellaan Clean Code -periaatteita noudattavan koodin laatuvaatimukset. Ohjelmoinnin harjoitustyön tulisi noudattaa periaatteita mahdollisimman hyvin.

**1. Nimeä luokat, metodit, attribuutit, parametrit ja  muuttujat selkeästi ja johdonmukaisesti**
* Käytä mahdollisimman kuvaavia nimiä kaikkialla 
 * Luokkien nimet aina isolla alkukirjaimella
* Metodit, attribuutit, parametrit ja muuttujat aina _camelCase_
* Muuttujat, joilla on iso käyttöalue, tulee olla erittäin selkeästi (vaikka pitkästi) nimettyjä. 
* Lyhyen metodin sisäisille muuttujille riittää yleensä lyhyt nimi. 
* Jos metodia käytetään vähän, tulee nimen olla mahdollisimman kuvaava. 
* Jos metodia käytetään useassa kohdassa koodia, voi sen nimi olla lyhyt ja ytimekäs.
* Älä käytä ääkkösiä

**Huomaa:** tee uudelleennimeäminen NetBeansin Refactor/rename-ominaisuuden avulla, ks kohta [refaktorointi](https://www.cs.helsinki.fi/node/61563)

**2. Ei pitkiä metodeja**
* Sovelluslogiikan metodin pituuden tulee ilman erittäin hyvää syytä olla korkeintaan 10 riviä, mieluiten 5.
* Pitkät metodit tulee jakaa useampiin metodeihin. 
* Yksi metodi - yksi pieni tehtävä. (Single Responsibility)
 * Helpottaa myös testaamista
* Jos metodin voi jakaa useampaan metodiin, niin silloinhan se jo tekee useamman metodin hommat.
* [Checkstyle-ohje](Checkstyle.md)

**3. Ei copy-pastea**
* Toistuvan koodin saa lähes aina hävitettyä
* Tapauksesta riippuen luo metodi tai yliluokka, joka sisältää toistuvan koodin

**4. Luokkien Single Responsibility**
* Luokkien tulisi hoitaa vain yhtä asiaa
* Esimerkiksi tiedoston lukemista tai -kirjoittamista EI tulisi löytyä useasta luokasta
 * Tee oma luokka tiedostojen käsittelylle
* Eriytä käyttöliittymä ja sovelluslogiikka
 * Kaikki tulostaminen tulisi tapahtua käyttöliittymässä
 * Sovelluslogiikkaan liittyviä laskuja ja tapahtumia ei tehdä käyttöliittymässä
 * Edellinen mahdollistaa helpon siirtymän tekstikäyttöliittymästä graafiseen

**5. Pakkaukset**
* << Default package >> EI saa olla käytössä
* Luokat tulee jakaa pakkauksiin
* * Pakkausten nimet aina pienellä (_lowercase_)
* Kaikkien pakkausten tulee olla yhden juuripakkauksen alla, esim. fi.omanimi
 * Logiikkapakkaus olisi näin tehtynä siis fi.omanimi.logiikka, käyttöliittymä fi.omanimi.gui
* Yhdessä pakkauksessa yksi kokonaisuus
 * Esim. yhdessä pakkauksessa käyttäjätileihin liittyvät luokat
 * Toisessa muu logiikka
 * Kolmannessa käyttöliittymän luokat
 * jne.
* Myös testipakkausten nimentä tulee olla oikea, ks. 6. Testaus

**6. Testaus**
* Generoidut testit ovat *kiellettyjä*
 * Tarkoitus on oppia testaamaan itse oma ohjelmakoodinsa
 * Generoidut testit harvoin testaavat mitään hyödyllistä
 * Generoitujen testien tai testipohjien käyttö: 0 pistettä
* Automatisoitu yksikkötestaus (=JUnit -testit) on *pakollista*
 * Testauksen puutteessa kurssisuoritus hylätään
* Palauta mieleesi Ohjelmistotekniikan Menetelmien testaustehtävät:
 * Testaa mahdollisimman montaa luokkaa
 * Testaa mahdollisimman montaa metodia
 * Testaa rajatapauksia
 * Testaa virheellisiä syötteitä
 * Gettereitä ja settereitä ei tarvitse testata, jos ne eivät tee mitään monimutkaista
 * Käyttöliittymää ei testata automaattisesti (Aihetta opetetaan kurssilla Ohjelmistotuotanto)
* Pakkaukset ja nimentä testeille
 * Esim. luokkaa Kayttaja testaa testiluokka KayttajaTest
 * Jos luokka Kayttaja on pakkauksessa "fi.teuvo.ilmo.kayttajat", KayttajaTest tulisi olla testipakkauksesa nimelta "fi.teuvo.ilmo.kayttajat".
 * Yhtä luokkaa kohti saa luoda useita testiluokkia
* Testikattavuudessa tärkein väline on oma järki, mutta halutessa voit käyttää hyväksi generoitua pit-raporttia

### Yleiset laatuvaatimukset

Lisäksi lopulliseen arvosteluun palautetun ohjelman tulee toimia oikein. Arvostelussa ensimmäiset muutaman minuutin ohjaajat kokeilevat ohjelmaasi käyttöohjeiden mukaan - ja todennäköisesti yrittävät tehdä jotain todella typerää apinan raivolla. Varaudu siis seuraavasti:

* Ohjelma ei saa missään tilanteessa kaatua
* Ohjelma ei saa printata Exceptioneita (Stack tracea) komentoriville, vaikka virhe ei kaataisi ohjelmaa
* Tarkista, ettei ohjelmasi käsittele taulukon ulkopuolelle meneviä arvoja, tai jo poistettuja arvoja
* Varaudu siihen, että käyttäjä yrittää antaa vääriä syötearvoja
 * Esim. ohjelmasi haluaa numeron, tyhmä käyttäjä syöttää "lolcat"
* Pelien sääntöjen tulisi toimia oikein
 * Esim. muistipelissä ei saa kääntää jo käännettyä palaa
 * Ristinollassa ei saa asettaa merkkiä ruutuun, jossa on jo merkki
* Jos ohjelmassasi tapahtuu vakava virhe, ohjelmasi voi esimerkiksi
 * näyttää käyttäjäystävällisen virheilmoituksen
 * ja sulkea ohjelman

Jos ohjelmaan jää jokin hämärä bugi tai outoa käyttäytymistä, yritä päästä siitä eroon. Etsi ongelman lähdettä esimerkiksi Netbeansin debuggerilla tai lisää koodiin välitulostuksia. Kysy vaikka ohjaajilta apua bugien liiskaamisessa. Jos mikään ei auta, älä lannistu! Oikeisiinkin ohjelmiin jää yleensä aina jonkinlaisia pieniä tai suurempia bugeja. Dokumentoi tiedostamasi bugit käyttöohjeeseen tai testausdokumenttiin, jos et saa niitä korjattua.
