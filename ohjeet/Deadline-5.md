# Deadline 5

### Ohjelma selkeästi edennyt
* Ohjelmoinnin tulee edistyä viikottain

### Noudata Clean code -periaatteita
* Yritä noudattaa koodin [laatuvaatimuksia](Koodin-laatuvaatimukset.md) jo mahdollisimman hyvin

### JUnit-yksikkötestit
* Tee uusi pit-raportti ja poista vanha.
* Toimintalogiikan testauksen oltava erittäin kattavaa (>90% rivikattavuus ja >60% mutanteista tapettu)
  * Prosenttiluvut ovat suosituksia, eivät absoluuttisia. Tarkoitus on testata kaikki mikä tuntuu mielekkäältä
  * Tähtää siihen, että kaikki mikä on järkevää testata on testattu

### JavaDoc
* Päivitä luokkien kuvauksia, jos tarpeen
* Kuvaa mahdollisimman paljon julkisia metodeja
  * @Override -metodit voi jättää kuvaamatta
  * Get- ja Set- metodit voi jättää kuvaamatta, jos ne eivät tee mitään erikoista
* Testeille ei kirjoiteta javadocia

### Checkstyle
* Lisätään checkstyleen JavaDoc-moduuli [näiden ohjeiden](JavaDoc.md#deadline-5-javadoc-checkstyle) mukaisesti
* Generoi uudestaan Checkstyle-raportti ja korjaa nyt myös kaikki syntyvät JavaDoc virheet


### Piirrä sekvenssikaavioita

* Muista: .png tai .jpg
* Luonnostele 2-3 tärkeintä sekvenssikaaviota käyttötapauksista
* Tärkeimmät käyttötapaukset löydät aihemäärittelystäsi
* Ota kuvataksesi riittävän pieniä käyttötapauksia
* Älä yritä samassa kaaviossa esittää liian montaa asiaa, esimerkiksi ehdollisuutta
* Epäonnistunut ja onnistunut kirjautuminen voisivat olla omat kaavionsa, tai yhden kaavion kaksi osaa
  * Sekvenssikaavio alkaa tunnusten syöttämisellä, kirjautuminen hylätään, virheilmoitus, tunnukset syötetään uudestaan, kirjautuminen onnistuu
* **Lisää sekvenssikaaviot kuvina [seuraavien ohjeiden](https://daringfireball.net/projects/markdown/syntax#img) mukaisesti dokumentaatiosi aiheenKuvausJaRakenne.md tiedostoon.**

### Generoi PIT-raportti uudestaan
* Generoi uudestaan PIT-raportti
* Lisää uusi generoitu raportti dokumentaatioon

### Muu dokumentaatio
* Aihemäärittely ja luokkakaaviot ajantasalla **viimeistään nyt**!
