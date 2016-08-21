# Deadline 1

### Luo itsellesi Github-repositorio, jonka nimi vastaa projektiasi.
* Esimerkiksi jos harjoitustyösi aihe on Monopoli ylimääräisellä blingillä niin repositoriosi voit nimetä vaikkapa Swagopoliksi.
* Älä siis valitse nimeksi geneerisiä 'Javalabra' tai 'OhHa'.
* [Git-ohje](Git-ohje.md)

### Luo uusi Netbeans-projekti repositoriokansioosi
* Luo projekti ja konfiguroi Maven ja PIT [näiden ohjeiden](Maven-ja-PIT.md) mukaisesti.
* Samalla kansioon pitäisi ilmestyä .gitignore -tiedosto

### Kirjoita aihemäärittely

**HUOM!** Kaikki kurssin dokumentaatio kirjoitetaan käyttämällä [Markdownia](https://help.github.com/articles/markdown-basics/). Tyylittele palautuksesi asianmukaisesti ja lisää jatkossa kaikki tekemäsi kuvat myös md-tiedostoihin edellämainittujen ohjeiden mukaisesti. Mikäli markdownia ei ole käytetty asianmukaisesti voi se johtaa palautuksessa nolliin pisteisiin dokumentaation osalta. 

Lyhyt kuvaus toteutettavasta ohjelmasta. Kuvauksen ei tarvitse olla kovin pitkä eikä kattava. Kuvaus tarkentuu myöhemmin, aluksi dokumentoidaan vain ideat, joiden pohjalta työtä lähdetään tekemään. Kuvaus sisältää muutaman tekstikappaleen pituisen yleiskuvauksen.

Tee aihemäärittelystä md-tiedosto. Nämä tiedostot ovat siis GitHubin tukemia Markdown-tiedostoja, joihin on mahdollisuus lisätä omia muotoiluja. Kannattaa tutustua  [Markdownin perusteisiin](https://help.github.com/articles/markdown-basics) ja [GitHub Flavored Markdowniin](https://help.github.com/articles/github-flavored-markdown). Tyylitietoisimmat voivat etsiä lisää kikkoja [tästä kattavasta oppaasta](http://guides.github.com/overviews/mastering-markdown/). Kaikki kurssilla kirjoitettava dokumentaatio tulee olemaan md-tiedostoissa. Md-tiedostoja voi editoida myös suoraan GitHubissa.

Aihemäärittelylle hyvä muoto on seuraava:

**Aihe:** ilmoittautumisjärjestelmä
Toteutetaan järjestelmä, jonka avulla ylläpidetään tietojenkäsittelylaitoksen kurssitietoja sekä tietoja kursseille ilmoittautuneista opiskelijoista... [lisää tekstiä 1-2 tekstikappaleen verran]

**Käyttäjät:** Opiskelija ja Opetushallinto

**Kaikkien käyttäjien toiminnot:**
* järjestelmään kirjautuminen
  * onnistuu jos salasana ja käyttäjätunnus oikein
* kaikkien kurssien listaus
* ...

**Opiskelijan toiminnot:**
* ilmoittautuminen
  * onnistuu jos kurssi ei ole täynnä ja opiskelija ei ole jo kurssilla
* omien ilmoittautumisten listaus
* ...

**Opetushallinnon toiminnot:**
* uusien kurssien lisäys
* tietyn kurssin ilmoittautujien listaaminen
* ...

### Aloita tuntikirjanpito

* Muoto: md-tiedosto
* Pidä kirjaa harjoitustyöhön käyttämästäsi työmäärästä
* Käyttämäsi työmäärä ei vaikuta arvosanaan, joten ole rehellinen
* Merkitse aina vähintään päivämäärä, käyttämäsi aika ja ajankäytön kohde
* Kirjoita tuntikirjanpito tässä muodossa:
```
### Tuntikirjanpito
Päivä | Tunnit | Kuvaus
--------------- | ----- | ------
01.01.2016 | 1.5h | Aiheen suunnittelua ja repon luonti
... | ... | ...
```
Ylläoleva markdown näkyy GitHubissa vastaavasti:
#### Tuntikirjanpito ####
Päivä | Tunnit | Kuvaus
--------------- | ----- | ------
01.01.2016 | 1.5h | Aiheen suunnittelua ja repon luonti
... | ... | ...

### Noudata kansiorakennetta

Kansiorakenne näyttää sen, miltä projektikansion pitäisi näyttää kurssin lopulla. Esimerkiksi Javadoc-kansiota tai käyttöohjeita ei tarvitse kuin kurssin lopussa. Noudata selkeää kansiorakennetta kuitenkin heti alussa. 

Kansiorakenne:
* Harjoitustyösi juurikansio (Repositoriokansio)
  * Ohjelma.jar (Vaaditaan vasta palautuksessa)
  * ohjelmasinimitähän/ (Netbeansin projektihakemisto)
  * javadoc/ (Generoitu dokumentaatio, vaaditaan vasta loppupalautuksessa)
  * dokumentaatio/
    * pit-raportti/
    * checkstyle-raportti/
    * aiheenKuvausJaRakenne.md
    * testausdokumentti.md
    * käyttöohjeet.md
    * tuntikirjanpito.md
    * luokka- ja sekvenssikaaviot.png tai .jpg

### Palauta Githubiin ja rekisteröi itsesi kurssin labtooliin

Puske (push) kaikki edellä tehdyt muutokset ja lisäykset Githubiin Git-ohjeiden mukaisesti.
Rekisteröi itsesi kurssin labtooliin osoitteessa: http://tktl-labtool.herokuapp.com/register. **Valitse listasta periodiasi vastaava kurssi (esim. Javalabra2015-1 vastaa ykkösperiodin kurssia vuonna 2015).** Periodit 5/alkukesä ja 6/loppukesä viittavat kesän opintojaksoihin. Rekisteröitymiseen tarvitset nimesi, sähköpostiosoitteesi, opiskelijanumerosi, harjoitustyöaiheesi ja Github-repositoriosi http-osoitteen.

**Palautuksia ei lähetetä sähköpostilla. Jos törmäät ongelmiin, niin älä jää murhehtimaan yksinäsi, vaan lähetä sähköpostia ohjaajille. Palautukseksi katsotaan viimeisin ennen deadlinea tehty Github pushaus. Ohjaajat siis seuraavat edistymistä suoraan Github-repositoriosi kautta ja antavat palautetta työstäsi pajassa sekä labtoolin välityksellä** http://tktl-labtool.herokuapp.com/mypage
