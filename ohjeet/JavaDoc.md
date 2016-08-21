# JavaDoc

Osa ohjelmiston dokumentointia on lähdekoodin *API-kuvaus*.  Javassa lähdekoodi dokumentoidaan käyttäen *JavaDoc*-työkalua.  Dokumentointi on kuin kommenttien kirjoittamista, mutta erityisillä avainsanoilla.  JavaDoc työkalu, jota voi käyttää suoraan NetBeanssin valikoista tekee kaikesta lähdekoodidokumentoinnista automaattisesti HTML-sivun.

Seuraava metodi on kommentoitu vapaamuotoisesti.  Kommentista käy ilmi mitä metodi tekee, mutta muotoiltua dokumentointisivua siitä ei saa tehtyä automaattisesti.
``` java
/* 
 * Kertoo kuinka todennäköistä onnistuminen on käyttäjän syötteellä.
 * HUOM: käyttää yläluokan metodia ja palauttaa arvon vähennettynä kalibroinnilla
 */
public int onnistumistodennakoisyys(int syote) {
    int tn = super.laskeTn(syote) - this.kalibrointi;
    return tn;
}
```

JavaDoc-dokumentoinnilla sama kuvaus olisi seuraavaa:
``` java
/**
 * Metodi kertoo mikä on onnistumistodennäköisyys syöteluvulla
 * ottaen huomioon olion konstruktorissa asetetun kalibrointiarvon.
 *
 * @param   syote   Käyttäjän antama syöte
 * 
 * @return todennäköisyys kalibroituna
 */
public int onnistumistodennakoisyys(int syote) {
    int tn = super.laskeTn(syote) - this.kalibrointi;
    return tn;
}
```

JavaDocin @param jne. avainsanoja ei onneksi tarvitse opetella ulkoa, koska NetBeans osaa täydentää myös JavaDoc-dokumentointia.  Private & package -näkyvyydellä olevat metodit eivät tule dokumentointiin.

Myös luokkia voi ja kannattaa dokumentoida. Se tapahtuu samalla tavoin kuin metodienkin dokumentointi.
``` java
/**
 * Luokka tarjoaa useita todennäköisyyslaskentaan tarvittavia metodeita.
 */
public class Todennakoisyyslaskin {
    /* ... */
}
```

JavaDocista saa luotua HTML-version valitsemalla NetBeansissa *Run -> Generate JavaDoc*

Mikäli painike ei ole käytössä, voi saman hoitaa komentoriviltä menemällä projektin juureen ja komentamalla `javadoc -d target/javadoc -sourcepath src/main/java/projekti`. Muista korvata sourcepath polulla oman projektisi java-tiedostoihin! 

**HUOM:** JavaDoc päättyy aina pisteeseen! Lopeta jokainen lause, jonka kirjoitat, pisteeseen. NetBeans antaa tästä vinkin lihavoimalla ensimmäisen lauseen JavaDocissa, joka päättyy pisteeseen (ns. tärkein lause).

### Attribuuttien dokumentointi

Oliomuuttujille ei yleisesti ottaen tarvitse kirjoittaa JavaDoc-kommentteja, sillä ne ovat usein yksityisiä ja täten eivät kuulu luokan JavaDocilla kuvattavaan APIin. Jos sinulla on koodissasi julkisia (public) muuttujia, ne suositellaankin ensisijaisesti muutettavaksi yksityisiksi (private), jolloin JavaDoc-kommentteja voidaan kirjoittaa niiden setteri- ja getterimetodeille.

Jos sinulla kaikesta huolimatta on julkisia muuttujia, JavaDoc-syntaksin mukaan niiden dokumentointi tehdään kuten metodienkin: 
``` java
/**
 * Kalibrointiarvo todennäköisyyden laskemiseen.
 */
public int kalibrointi = 20;
```
 
### Tarkempi dokumentointi

Laajennetaan vielä alussa esiteltyä esimerkkiä.  Metodille annetaan toinen parametri ja tämä dokumentoidaan omana @param-rivinä.  Lisäksi dokumentointiin lisätään "See Also" -kohta, jonka kautta HTML-dokumentissa liikkuminen laskukone-pakkauksen Laskenta-luokan laskeTn(int)-metodiin on helppoa.  Tämä ilmaistaan muodossa laskukone.Laskenta#laskeTn(int).  NetBeanssin control+space osaa täydentää projektin koodin mukaan tämän polun!
``` java
/**
 * Metodi kertoo mikä on onnistumistodennäköisyys syöteluvulla
 * ottaen huomioon olion konstruktorissa asetetun kalibrointiarvon.
 *
 * @param   syote   Käyttäjän antama syöte
 * @param   kayttajanKorjaus    Käyttäjän antama korjausarvo
 * 
 * @see    laskukone.Laskenta#laskeTn(int)
 *
 * @return todennäköisyys kalibroituna
 */
public int onnistumistodennakoisyys(int syote, int kayttajanKorjaus) {
    int tn = super.laskeTn(syote) - this.kalibrointi - kayttajanKorjaus;
    return tn;
}
```

Lisää ohjeita löydät [JavaDocin Wikipedia-sivulta](http://en.wikipedia.org/wiki/Javadoc).

### JavaDocin Generointi 
Jos haluat saada projektisi JavaDocista helposti selattavan html-sivun ja NetBeansin oma "Generate JavaDoc"-näppäin on harmaana, ei kannata huolestua, voimme lisätä sen helposti samaan custom-valikkoon kuin pit.

Lisää pom.mxl:ään tämä plugin:

``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    <version>2.10.3</version>
</plugin> 
```

Tämän jälkeen build-osan pitäisi näyttää suunnilleen tältä (paitsi jos olet konfiguroinut pittiä, jolloin sen sisällä on configuration-blokki):
``` xml
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
        <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-javadoc-plugin</artifactId>
             <version>2.10.3</version>
        </plugin> 
    </plugins>
</build>
```

Sitten lisätään plugin vielä NetBeansin Custom -valikkoon. Lisää nbactions.xml tiedostoon seuraava "action-palikka" muiden actioneiden rinnalle:
``` xml
    ...
    <action>
        <actionName>CUSTOM-Javadoc</actionName>
        <displayName>Javadoc</displayName>
        <goals>
            <goal>javadoc:javadoc</goal>
        </goals>
    </action>
    ...
```

Tiedostosi tulisi nyt näyttää jotakuinkin tältä (riippuen configuraatioista, pieniä eroja saattaa olla pitissä ja check-stylessä).

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
    
    <action>
        <actionName>CUSTOM-checkstyle</actionName>
        <displayName>Checkstyle</displayName>
        <goals>
            <goal>jxr:jxr</goal>
            <goal>checkstyle:checkstyle</goal>
        </goals>
    </action>
    
    <action>
        <actionName>CUSTOM-Javadoc</actionName>
        <displayName>Javadoc</displayName>
        <goals>
            <goal>javadoc:javadoc</goal>
        </goals>
    </action>
</actions>
```

Nyt voit generoida JavaDocin klikkaamalla projektin nimeä oikealla hiirennäppäimellä ja valitsemalla `custom-JavaDoc`.

## Deadline 5: JavaDoc-Checkstyle

Lisätään Checkstyleen moduuli jolla tarkistetaan JavaDocin oikeus. Moduulit lisätään TreeWalker-moduulin tägien väliin.

```xml
  <module name="JavadocMethod">
    <property name="scope" value="public"/>
    <property name="allowMissingParamTags" value="false"/>
    <property name="allowMissingPropertyJavadoc" value="true"/>
    <property name="allowMissingThrowsTags" value="false"/>
    <property name="allowMissingReturnTag" value="false"/>
    <property name="allowThrowsTagsForSubclasses" value="true"/>
  </module>
        
  <module name="JavadocStyle">
    <property name="scope" value="public"/>
    <property name="checkEmptyJavadoc" value="true"/>
  </module>
```

Tämän seurauksena uusia virheitä tulee ilmestymään paljon, sillä Checkstylen tarkistus on nyt kattavampi. Korjaa kaikki uudet virheet.
