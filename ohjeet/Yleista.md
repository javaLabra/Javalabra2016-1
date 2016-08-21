# Yleistä

### Mikä on ohjelmoinnin harjoitustyö?

Harjoitustyössä toteutetaan itsenäisesti ohjelmisto omavalinteisesta [aiheesta](Esimerkkeja-aiheista.md). Tavoitteena on soveltaa ja syventää ohjelmistotekniikan menetelmät (ohjelmistojen mallintaminen) sekä ohjelmoinnin perus- ja jatkokursseilla opittuja taitoja ja harjoitella tiedon omatoimista etsimistä. Harjoitustyötä tehdään itsenäisesti ja tarjolla on pajaohjausta. 

Harjoitustyön on edettävä [viikottaisten virstanpylväiden mukaan](Tehtavat-ja-palautus.md). Työ on saatava valmiiksi kurssin aikana ja sitä on toteutettava tasaisesti, muuten kurssi katsotaan keskeytetyksi. Samaa ohjelmaa ei voi jatkaa myöhemmin toisessa yrityksessä, vaan työ on aloitettava uudella aiheella alusta. Kurssin uusimismahdollisuuksia on jouduttu rajoittamaan, joten varaathan riittävästi aikaa kurssin suorittamiseen! 

### Harjoitustyön kieli ja ohjelmointikieli

Harjoitustyön ohjelmointikieli on Java.

Ohjelmakoodin muuttujat, luokat ja metodit voi kirjoittaa suomeksi tai englanniksi, kunhan kieliä ei sekoita rumasti keskenään. Samoin Javadoc ja muu dokumentaatio kirjoitetaan suomeksi tai englanniksi. Suositeltava tapa on kirjoittaa koodi englanniksi ja dokumentaatio suomeksi.

### Ohjelman toteutus

Toteutus etenee "iteratiivisesti ja inkrementaalisesti". Tämä tarkoittaa, että heti alussa toteutetaan pieni osa ohjelman toiminnallisuudesta. Ohjelman ydin pidetään koko ajan toimivana, uutta toiminnallisuutta lisäten, kunnes tavoiteltu ohjelman laajuus on saavutettu. Ohjelman rakenteeseen kannattaa kysyä vinkkejä pajasta, sekä ottaa mallia ohjelmoinnin jatkokurssin harjoitustehtävistä. 

Iteratiiviseen tapaan tehdä ohjelma liittyy kiinteästi automatisoitu testaus. Aina uutta toiminnallisuutta lisättäessä ja vanhaa muokatessa täytyy varmistua, että kaikki vanhat ominaisuudet toimivat edelleen. Kaiken testaaminen käsin uudelleen ja uudelleen ei ole ajankäytöllisesti järkevää, ja siispä ohjelmakoodille onkin syytä laatia jatkuvasti yksikkötestejä ohjelmoinnin edetessä. Testit on syytä pitää kattavina ja ajan tasalla.

Voit tehdä harjoitustyöhösi aluksi tekstikäyttöliittymän ja vasta saatuasi ohjelman perustoiminnallisuuden toteutettua voit siirtyä graafisen käyttöliittymän toteutukseen. Graafinen käyttöliittymä on mahdollista jättää pois sopimuksen mukaan, mikäli aihevalinta ja toteutus tukevat tätä vaihtoehtoa. Graafiseen käyttöliittymän toteuttamiseen voit halutessasi käyttää NetBeansiin integroitua Swing GUI builderia. GUI-builderin generoimaa koodia on kuitenkin vaivalloista seurata, mikä vaikeuttaa ongelmien korjaamista ja oman ohjelman rakenteen hahmottamista, joten suositeltavaa on Swingin kohdalla rakentaa käyttöliittymä itse. Tämä varmistaa sen, että tiedät miten ohjelmasi on koodattu. [Lisätietoa GUI-builderista](http://netbeans.org/kb/docs/java/gui-functionality.html)

Harjoitustyön tavoitteena on tuottaa ohjelma, joka voitaisiin antaa toiselle opiskelijalle ylläpidettäväksi ja täydennettäväksi. Lopullisessa palautuksessa on oltava lähdekoodin lisäksi dokumentaatio sekä automaattiset testit.
