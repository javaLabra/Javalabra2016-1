# Maven ja PIT

### Projektin luominen
Jos koneellasi ei ole ohjelmointikurssien jäljiltä NetBeansia, asennusohjeet löytyvät [täältä](https://github.com/UniversityHelsinkiTKTL/tmc-plugin-installation-guide/blob/master/TmcBeanssinAsennusOmalleKoneelle.md#tmc-netbeanssin-asennus).

Projekti luodaan normaalisti NetBeansin **New Project**-nappulasta. Nyt kuitenkin ei valita kategoriaa **Java**, vaan hieman alempaa etsitään kohta **Maven**. Oikeasta valikosta voidaan nyt valita **Java Application**.

Sivulla **Name and Location** kannattaa antaa ohjelmalle hyvä ja kuvaava nimi. Aseta **Project Location**:ksi Git-repositoriosi polku (omalle koneellesi luotu repositoriokansio, josta pushit ja commitit tehdään). Myös **Group id** täytyy vaihtaa ohjelman nimen mukaiseksi tai ainakin joksikin muuksi kuin _com.mycompany.enterprising.domain_ , ja se pitää kirjoittaa **pienillä kirjaimilla**. Tämä on tärkeää mutaatiotestauksen toiminnan kannalta. GroupId muuttaa ohjelman vakiopakkauksen nimen.

Maven ei eroa "normaalista" Java-projektista kovinkaan paljoa. Suurin ero on pom.xml-tiedosto joka kuvaa xml:nä projektin riippuvuudet eri kirjastoista. Lisäämme sinne valmiiksi muutaman testausta auttavan kirjaston, mutta jos aiot käyttää itse jotain apukirjastoja, ne voidaan lisätä tänne myös.

Nyt projektisi pom.xml:n pitäisi näyttää jotakuinkin seuraavalta:
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>superohjelma</groupId>
    <artifactId>SuperOhjelma</artifactId>
    <version>0.1.0</version>
    <packaging>jar</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
    
    <!-- Lisättävä osa tähän väliin-->

</project>
```

Tämän xml:n alkuosa on jokaisella projektille yksilöllinen. Siihen emme koske. Sen sijaan haluamme lisätä muuutaman riippuvuuden ja pluginin projektiin. Lisätään `</properties>`-tagin ja `</project>`-tagin väliin osa:
``` xml
<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
</dependencies>
    
<build>
    <plugins>
        <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
            <version>3.3</version>
        </plugin>
        <plugin>
            <groupId>org.pitest</groupId>
            <artifactId>pitest-maven</artifactId>
            <version>1.1.8</version>
        </plugin>
    </plugins>
</build>
```

Lisäyksen jälkeen pom.xml pitäisi näyttää jotakuinkin tältä:

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>superohjelma</groupId>
    <artifactId>SuperOhjelma</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
                <version>3.3</version>
            </plugin>
            <plugin>
                <groupId>org.pitest</groupId>
                <artifactId>pitest-maven</artifactId>
                <version>1.1.8</version>
            </plugin>
        </plugins>
    </build>
    
</project>
```

Tämän jälkeen projektille voi tehdä mutaatiotestausraportteja, joista käy ilmi myös rivikattavuus. Tehdään vielä näiden generoimisesta hieman helpompaa.

Lisää projektiin uusi tiedosto **New File...**-näppäimellä. Valitse **XML -> XML Document** ja anna sille nimeksi **nbactions**. Siirry seuraavan ikkunaan ja valitse **Well-formed Document**. Paina Finish. Nyt projektissa pitäisi olla uusi _nbactions.xml_-tiedosto. Jos se ei ole Project Files-kansiossa, siirrä se sinne. 

Avaa tiedosto ja korvaa sen sisältö tällä: 
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<actions>
    <action>
        <actionName>CUSTOM-pit</actionName>
        <displayName>pit</displayName>
        <goals>
            <goal>org.pitest:pitest-maven:mutationCoverage</goal>
        </goals>
    </action>
</actions>
```

Tallenna ja aja projektille **Clean and Build**. Nyt kun klikkaat projektia oikealla hiirennäppäimellä, **Custom**-valikon alta pitäisi löytyä  _pit-_vaihtoehto.

### Raportit

Lainaus Pit-testien sijainnista:
> Mutaatiotestaa ohjelmasi suorittamalla ensin testit ja sen jälkeen klikkaamalla NB:stä projektin kohdalla oikeaa nappia ja valitsemalla custom/pit

> tai vaihtoehtoisesti ollessasi projektihakemistossa antamalla komentoriviltä komennot mvn test ja mvn org.pitest:pitest-maven:mutationCoverage

> Edellinen onnistuu myös yhdellä komennolla mvn test org.pitest:pitest-maven:mutationCoverage

> Tulokset tulevat projektihakemistosi alihakemistoon target/pit-reports/aikaleima/index.html. Aikaleima on numerosarja joka kertoo suoritushetken, tyyliin 201311181742 (testi ajettu 18.11.2013 klo 1742). Avaa tulokset web-selaimella. Firefoxilla tämä tapahtuu komennolla open file. Voit myös avata selaimen terminaalissa menemällä ensin projektihakemistoon ja antamalla komento chromium-browser target/pit-reports/aikaleima/index.html. Kun ajat mutaatiotestit uudelleen, muista avat oikea raportti!

> Voit poistaa vanhat raportit painamalla vasara+harja-symbolia (clean and build) tai komentoriviltä komennolla mvn clean

> Raportista näet mitkä mutantit jäävät henkiin.

Kun lisäät pit-raportin viikkopalautukseen, siirrä koko aikaleimakansio target/pit-reports/-hakemistosta _dokumentaatio/pit/_-kansioon.

## Pitin konfigurointi
Pit-testaukseen voi suhteellisen helposti määrittää, mitkä luokat testataan. Jos tavoittelee 100% mutanttien tappamista, tai muuten vaan nätimpää dokumentaatiota, voi näin jättää muun muassa käyttöliittymän ja main-luokan pois mutaatiotestauksesta.

Lisäämällä pom.xml:ään plugin-tagien sisään configurationin, voi määrittää tarkasti, minkä pakettien sisällöt testataan. Eli jos testiraporttiin halutaan kuvitteellisesta ristinollaohjelmasta testata vain logiikka ja tekoäly, kerrotaan tämä targetClasses:n ja targetTests:n kautta näin:

Korvataan pom.xml:n pit-plugin kohta:
``` xml
            <plugin>
                <groupId>org.pitest</groupId>
                <artifactId>pitest-maven</artifactId>
                <version>1.1.8</version>
            </plugin>
```

Seuraavan tyylisellä (muuta param-kohdat omaa ohjelmaasi vastaaviksi):

``` xml
<plugin>
    <groupId>org.pitest</groupId>
    <artifactId>pitest-maven</artifactId>
    <version>1.1.8</version>
    <configuration>
        <targetClasses>
            <param>superohjelma.logiikka.*</param>
            <param>superohjelma.tekoaly.*</param>
        </targetClasses>
        <targetTests>
            <param>superohjelma.logiikka.*</param>
            <param>superohjelma.tekoaly.*</param>
        </targetTests>
    </configuration>
</plugin>
```
Eli jos haluat testata paketin joka NetBeanssissa on laivanupotus.logiikka, täytyy pom.xml:ään laittaa aivan suoraan `<param>superohjelma.logiikka.*</param>`.


### Virhetilanteet

* Jos pittiä ajaessa tulee kasa punaista tekstiä, joka näyttää suunnilleen tältä:

```
Failed to execute goal org.pitest:pitest-maven:0.30:mutationCoverage (default-cli) on project OhHa:
Execution default-cli of goal org.pitest:pitest-maven:0.30:mutationCoverage failed:
No mutations found. This probably means there is an issue with either the supplied classpath or filters.
```
* **Virhe voi johtua siitä, että projektissasi ei ole vielä yhtään testiä**, tee siis vähintään yksi testi ja yritä uudestaan. Jos virhe ei poistu, lue alaspäin.

* Se tarkoittaa, että pom.xml:n groupID ja projektin pakettien nimet eivät täsmää keskenään. Tai että konfiguroinnin parametrit osoittavat väärään paikkaan. Tai että testit eivät ole koodia vastaavissa paketeissa.

* Jos et ole konfiguroinut pittiä, tarkista että ohjelmasi oletuspaketin nimi ei ole eri kuin pom.xml:ssä oleva groupID. Tässä isoilla kirjaimilla on väliä, eli jos paketin nimi on "ohha" ja pom.xml:ssä lukee `<groupId>OhHa</groupId>`, ei pit-raportin generointi tule onnistumaan. Jos ero löytyy, korjaa jommankumman nimi.

* Jos olet konfiguroinut pittiä, tarkista ettet ole vahingossa lisännyt liian pitkää polkua.

* Tarkista että testisi ovat ohjelmakoodia vastaavissa paketeissa. Eli jos testaat ristinolla.logiikka- paketissa olevaa Ruutu-oliota, pitää Test Packagesissa olla paketti ristinolla.logiikka, jonka sisällä on RuutuTest.

* Jos Pit-raportti generoidaan oikein, mutta se näyttää 0% kaikessa vaikka toimivia testejä on, tarkista että testitiedostojen alussa on testitiedoston pakettia vastaava pakettimäärittely, esim: `package superohjelma.logiikka` 
