# Git-ohje

*Alkuperäinen ohje: Mika Huttunen ja Silja Polvi*

### Mikä Git?

Git on laajalti käytetty versionhallinnan työkalu, jota tarvitaan muunmuassa harjoitustöitä tehdessä. Versionhallinnan avulla esimerkiksi tiedostoihin tekemäsi muutokset ovat aina tallessa, ja voit palata edelliseen versioon, jos jokin menee pieleen.

## Yksityiskohtainen “kädestä pitäen” -ohje Gitin käyttöön

*Huomaa:* Lyhyemmät ohjeet löydät [OhTu-kurssin harjoituksista](https://wiki.helsinki.fi/display/ohtu2012/laskari1).

### Aloittaminen

**HUOM: käytä Netbeansin tarjoamaa Git-lisäosaa tai muita graafisia ohjelmia omalla vastuullasi.** Tähän asti kaikki kurssilla päivän koodaustyönsä menettäneiden ongelmat ovat johtuneet näistä. Käytä aina Linuxissa terminaalia tai Windowsissa Git Bashia, ja tee Commitit sekä Pushit käsin.

1. Jos et ole yliopiston koneella ja koneessasi ei ole valmiiksi Gitiä, voit ladata sen täältä: http://help.github.com/win-set-up-git/. Ohje on Windowsille, mutta sen alussa on linkit myös muita käyttöjärjestelmiä varten.
2. Mene osoitteeseen [http://www.github.com/plans](http://www.github.com/plans) **(Github-repositoriosi on julkinen. Sen näkee koko maailma. ÄLÄ pistä sinne esimerkiksi opiskelijanumeroasi.)**
3. Vapaaehtoinen - hae itsellesi opiskelijatunnusta githubiin, saat ilmaisen Micro-planin ja siten ilmaisia private-repositorioita [https://education.github.com/](https://education.github.com/) 
4. Paina oikealla ylhäällä olevaa nappia "Sign Up"
5. Täytä vaadittavat neljä kenttää ja klikkaa "Create an account"
6. Paina oikealla olevaa harmaata nappia "New repository"
7. Laita repositorion nimeksi esimerkiksi harjoitustyösi aihe tai oma nimiehdotuksesi ohjelmalle (ohjeessa Fraktaaligeneraattori)
  * Valitse pallura "Public"
  * Valitse ruutu "Initialize this repository with a README"
8. Klikkaa lopuksi "Create repository".

### SSH-avaimen luominen omalla koneella

Katso ohje [tästä](https://help.github.com/articles/generating-ssh-keys). Mikäli latasit Gitin yllä olevan linkin takaa Githubin sivuilta, käytä komentorivinä Git Bashia!

### SSH-avaimen luominen laitoksen koneella

**Huomaa:** Laitoksen sivuilla on tähänkin vähän lyhyemmät [ohjeet](http://www.cs.helsinki.fi/group/kuje/compfac/ssh_avain.html).
SSH-avaimen luominen ei ole pakollista, mutta helpottaa versionhallinnan käyttöä. Toisinaan joillakin henkilöillä Github on evännyt yhteydenotot ilman SSH-avaimen luomista.

1. Avaa komentorivi (Konsole tai Terminal)
2. Anna komento `ssh-keygen`
3. Ohjelma kysyy, mihin tiedostoon avain tallennetaan. Oletus on hyvä, joten hyväksy painamalla *enter*.
4. Ohjelma pyytää asettamaan salasanan avaimellesi. Anna salasana, jonka varmasti muistat. Salasana on pakollinen, muuten laitoksen ylläpito poistaa ssh-avaimesi.
5. Aseta ssh-hakemiston oikeudet antamalla ensin komento `chmod u=rwx,go= .ssh` ja antamalla seuraavaksi komento `chmod u=rwx,go= .ssh/*`
6. Lisää avaimen julkinen pari Githubiin: anna ensin komento `less .ssh/id_rsa.pub` tai `gedit .ssh/id_rsa.pub` niin pääset tarkastelemaan tiedostoa
7. Kopioi koko tiedoston sisältö (eli teksti)
8. Avaa nettiselaimella Github ja kirjaudu sisään (jos et jo ole kirjautuneena)
9. Paina oikeassa yläkulmassa olevaa jakoavaimen ja ruuvimeisselin kuvaa (“Account Settings”)
10. Klikkaa vasemmalta “SSH Keys” ja sitten oikealta nappia "Add SSH key"
11. Anna nimeksi (Title) vaikka "Laitoksen avain" ja liitä Key-kenttään kohdassa 10 kopioimasi teksti. Poista tekstin seasta mahdolliset rivinvaihdot ja välilyönnit, jotta avaimesi sekaan ei jää “white spaceja”. Paina lopuksi nappia "Add key".
12. Anna confirm-kentälle Githubin salasanasi
13. Avaimesi on nyt lisätty Githubiin!

**HUOM.** Sinulla tulee olla edellisessä kohdassa tekemäsi ssh-avaimen yksityinen osa (id_rsa) jokaisella koneella, josta haluat käyttää Githubia. Vaihtoehtoisesti voit luoda erillisen ssh-avaimen jokaiselle koneelle. Laitoksella riittää, että ssh-avaimen luomisen tekee vain kerran yhdellä koneella.

### Repositorion valmisteleminen käyttöä varten

**HUOMAA:** Tässä ohjeessa komentorivillä tarkoitetaan Linuxilla terminaalia ja Windowsin tapauksessa Git Bashia! Windowsin omat komentorivit eivät tunnista git-alkuisia komentoja, mikäli otit Gitin käyttöön yllä olevan linkin takana olevan Windows-ohjeen mukaan. Käytä Git Bashia.

1. Hankkiudu Githubin sivulla luomasi repositorion näkymään. Sinne pääsee vaikkapa etusivulta kun olet kirjautunut, klikkaamalla repositorion nimeä.
2. Kopioi vasemman sivupalkin alaosassa olevassa kentässä näkyvä kloonausosoite, joka on suunnilleen muotoa *git@github.com:käyttäjätunnuksesi/Fraktaaligeneraattori.git*. Jos osoite sen sijaan alkaa esimerkiksi *https://*, paina kentän läheisyydessä olevaa SSH-linkkiä jolloin osoitteen pitäisi muuttua oikeaan muotoon.
3. Avaa komentorivi ja anna komento tyyliin `git clone git@github.com:käyttäjätunnuksesi/Fraktaaligeneraattori.git`
4. Seuraavaksi ohjelma pyytää vahvistamaan äskeisen komennon (yes/no) - vastaa yes
  * Jos git push sanoo “Permission denied (publickey)”, kokeile ssh-avaimen generointia uudestaan tai komentoa ssh-add
5. Mene komentorivillä äsken kloonaamaasi hakemistoon (esim. Fraktaaligeneraattori) komennolla `cd Fraktaaligeneraattori` tms. Kaikki tiedostot voit listata komennolla `ls`.
6. Komennon `cd Fraktaaligeneraattori` jälkeen olet hakemistossa, johon tulet tallentamaan projektisi. Nyt komennolla `ls` tulisi näkyä tiedosto README.

### Pieni repotreeni

1. Varmista, että olet komentorivillä repositoriohakemistossasi (esim. Fraktaaligeneraattori)
2. Avaa README-tiedosto suosikkitekstieditorillasi, vaikkapa komennolla `nano README.md`
3. Tiedoston pitäisi aueta valitsemassasi editorissa. Kirjoita tiedostoon jotakin ja tallenna se. Nanossa tallenna ja sulje tiedosto painamalla *Ctrl + x*, ja vahvista tallennus painamalla *enter*.
4. Anna komentorivillä komento *git status*. Nyt näet luettelon tiedostoista, joita olet muokannut (modified), tässä tapauksessa README-tiedosto.
5. Anna komento git commit -am "eka muokkaus". Jos viesti (tässä eka muokkaus) unohtuu, avautuu editori. Poistu editorista komennolla `q`. Anna antamasi commit-komento uudelleen, tällä kertaa viestin kera.
6. Nyt tekemäsi muokkaukset (README-tiedoston muokkaus) ovat paikallisessa repositoriossasi. Sieltä ne pitää vielä työntää verkossa olevaan Githubin repoosi komennolla `git push`.
  * Jos git push sanoo "Permission denied (publickey)", kokeile ssh-avaimen generointia uudestaan tai komentoa `ssh-add`
7. Mene Githubin sivulla olevaan repositoriosi näkymään (kuten edellisen ohjeen kohdassa 1) ja päivitä näkymä. Huomaat, että README-tiedostoon tekemäsi muokkaukset ovat nyt Githubissa asti, antamasi viestin kera!

### Toinen repotreeni

1. Hankkiudu komentorivillä repositorion hakemistoosi (esim. OhHa). Anna komento `mkdir testihakemisto` luodaksesi uuden hakemiston. 
2. Lisää testihakemistoosi jokin tiedosto: etsi tietokoneeltasi luomasi hakemisto ja luo tai siirrä sinne vaikkapa tekstitiedosto.
3. Lisää luomasi hakemisto versionhallinnoitavaksi antamalla komentoriville komento `git add testihakemisto`. Nyt versionhallinta seuraa hakemistotasi siinä mielessä, että se näkyy status-komennolla, ja sen voi siirtää paikalliseen versionhallintaan (commit). Huomaa, että typötyhjä hakemisto ei tule hallinnoitavaksi add-komennolla.
4. Anna commit-komento (`git commit -m “uusi testitiedosto ja -hakemisto lisatty”`).
5. Anna push-komento (`git push`). Tarkista Githubin nettisivulta, että uusi hakemistosi ja sen sisältämä tiedosto ilmestyvät repositorionäkymääsi.

**Huom:** Jos haluat lisätä useita tiedostoja kerralla, se onnistuu komennolla `git add .`

Nyt osaat lisätä Githubiin tiedostoja ja hakemistoita: add - commit - push! Tee samaan malliin harjoitustyöllesi dokumentaatiohakemisto ja sinne ensimmäisellä viikolla tarvittava dokumentointi.

### Kolmas repotreeni: pull

Jos työskentelet useammalla kuin yhdellä koneella, voit versionhallinnan avulla pitää projektin ajan tasalla ilman että joudut siirtämään tiedostoja koneelta toiselle esimerkiksi muistitikulla. Sehän on yksi versionhallinnan hyödyistä! Tässä harjoituksessa pääset harjoittelemaan tiedostojen kopioimista Githubista koneellesi toisen repositoriokloonihakemiston avulla. Todellisessa tilanteessa harjoituksessa luotava toinen kloonihakemisto vastaa eri koneella olevaa kloonihakemistota. Et siis tarvitse toista kloonia (varjorepo) muuhun kuin tähän harjoitukseen.

1. Luo uudella nimellä (esim. varjorepo) toinen klooni repositoriosta antamalla komentorivillä komento tyyliin `git clone git@github.com:käyttäjätunnuksesi/Fraktaaligeneraattori.git varjorepo`. Klooni luodaan siis muuten kuten kohdassa “Repositorion valmistelu käyttöä varten”, paitsi että nyt kloonihakemisto nimetään itse.
2. Muokkaa alkuperäisessä repossa (esim. Fraktaaligeneraattori) olevaa tiedostoa README. Anna add-komento, commit-komento ja push-komento alkuperäisessä repositoriokloonihakemistossasi (Fraktaaligeneraattori), jotta äsken tehty muutos päätyy Githubiin asti.
3. Mene tämän harjoituksen alussa luomaasi varjorepoon. Avaa nyt README-tiedosto tässä uudessa repossa, jolloin huomaat että se ei ole muuttunut.
4. Vedä alkuperäisessä hakemistossasi (Fraktaaligeneraattori) tekemäsi muutokset varjorepoon Githubista komennolla `git pull`. Huomaat, että README-tiedosto päivittyy niiden muutosten mukaan, jotka teit alkuperäisessä kloonissa! Tarkista tämä vielä varjorepossa olevasta README-tiedostosta.

### Git & Netbeans

Git ja Netbeans ovat hyviä kavereita. Luo ensin Netbeans-projektisi [näiden ohjeiden](Maven-ja-PIT.md) mukaisesti. Käytä Netbeans-projektin tallennuspaikkana koneellasi olevaa repositoriokloonihakemistota: aseta Netbeansissa kohtaan “Project Location” koneella oleva repositorion hakemisto (esim. Fraktaaligeneraattori). Nyt tallennat projektiasi koko ajan repositorion hakemistoon.

1. Anna (kun olet ensin siirtynyt komentorivillä repositoriohakemistoosi) komentoriville komento `git status`. Huomaat kaksi uutta tiedostoa: harjoitustyösi lisäksi tiedoston .gitignore. Viimeksi mainittu on Netbeansin luoma tiedosto, joka antaa listan versionhallintaan kuulumattomista tiedostoista. Se pitää lisätä versionhallinnoitavaksi. Tiedostosta ei tarvitse ymmärtää enempää, mutta jos haluat tai tiedosto ei generoitunut automaattisesti, lue tämän dokumentin lopusta lyhyt .gitignore -selite.
2. Anna komento `git add harkkatyöprojektisiNimi`_ ja sen jälkeen komento `git add .gitignore`.
3. Nyt komennon git status pitäisi näyttää sekä harkkatyöprojektisi sisältöineen että .gitignore.

Anna commit-komento ja push-komento. Nyt harjoitustyösi löytyy Githubistasi!

**Nyt voit aloittaa harjoitustyösi tekemisen, mutta muista poistaa ylimääräinen harjoitteluun käyttämäsi testihakemisto!**

### Nyrkkisäännöt

* Uudella koneella aloittaessasi luo ssh-avain ja kloonaa (clone) haluamasi repositorio koneelle
* Työskentelyn aluksi vedä (pull) Githubista projektisi
* Tehdessäsi muutoksia, lisää (add) uudet tiedostot ja muutetut tiedostot, sekä tee commit kuvaavalla kommentilla.
* Add + Commit yhdistelmää voit ajatella työn tallentamisena.
  * Tee mieluummin liikaa kuin liian vähän committeja
  * git status komennolla voit kysellä mitä olet muuttanut ja mitä olet commitoimassa
  * Ongelmatilanteissa on mahdollista palata vanhaan committiin, vaikka viikon takaa!
* Viimeistään lopettaessasi työskentelyn työnnä (push) muutoksesi Githubiin.
* Tarkista selaimesta, että KAIKKI muutokset menivät repositorioosi: Muuten ohjaajat eivät niitä näe
* Repositorio on myös varmuuskopio työstäsi - jos tietokoneesi hajoaa tai laitoksen palvelimet reistailevat, on kaikki vaivalla tekemäsi työ tallessa Githubissa!
* Tiedoston poistaminen repositoriosta tehdään `git rm tiedostonnimi` -komennon avulla. HUOM ole huolellinen tämän käytössä, sillä komento poistaa tiedoston myös paikallisesta repositoriosta (siis omalta koneeltasi)
* **MUISTA:** Github-repositoriosi on julkinen. Sen näkee koko maailma. ÄLÄ pistä sinne esimerkiksi opiskelijanumeroasi.

Nyt voit jatkaa harjoitustyötäsi miltä tahansa tietokoneelta aina siitä mihin lopetit edellisellä kerralla.

### Lyhyt .gitignore -ohje

.gitignore on tiedosto, joka sisältää tiedon niistä tiedostoista ja hakemistoista, joita ei haluta versionhallintaan eikä Githubiin. Nämä esitetään sääntöinä, jokainen sääntö omalla rivillään. Yleensä nämä tiedostot ovat kehitysympäristöjen joka ajokerralla generoitavia tai arkaluontoista tietoa sisältäviä tiedostoja, joita ei haluta versionhallintaan viemään tilaa tai kaikkien nähtäville. **.gitignore tiedosto itsessään halutaan Githubiin.**

Netbeans luo .gitignore -tiedoston automaattisesti, kun Netbeans-projektin luo hakemistoon, joka on repositorio. Netbeans lisää sinne säännön */projektihakemistosi_nimi/nbproject/private/*, joka estää versionhallintaan menemästä tiedostoja, jotka Netbeans luo aina kun käännät ja ajat ohjelmasi. `git status` -komento ei siis huomaa lainkaan, vaikka private/ -hakemiston sisällä tapahtuu muutoksia.

Jos Netbeans jostain syystä ei tehnyt tällaista tiedostoa, voit luoda sen itse.
1. Tee tekstitiedosto, jolle annat nimeksi ".gitignore"
  * Tiedostolla ei ole tiedostopäätettä
2. Lisää tekstitiedostoon rivi */projektihakemistosi_nimi/nbproject/private/*
3. Lisää myös rivi */projektihakemistosi_nimi/nbproject/dist/*

Vastaavasti .gitignore-tiedostoon voi lisätä omia sääntöjä. Jokainen sääntö tulee omalle rivilleen. 

Säännöistä löytää lisää esimerkkejä osoitteissa:

http://git-scm.com/docs/gitignore

https://help.github.com/articles/ignoring-files

http://cfmumbojumbo.com/cf/index.cfm/coding/git-giving-files-the-cold-shoulder-gitignore/
