#Checkstyle-fu

Nyt kun checkstyle on hieman jo tullut tutuksi, niin on aika jatko-konfiguroida sitä. Lisäämme tällä kerralla JavaDoceja varten omat
konfiguraatiot ja pääsemme samalla eroon (suhteellisen ärsyttävistä) virheistä UI:n puolelta. Tavoitteet ovat siis:

1. Ominaisuus tiettyjen tiedostojen testaamattomuudelle
2. JavaDoc-määrittelyiden testaus

Aloitetaan siis lisäämällä seuraava pätkä viime viikolla luotuun checkstyle.xml-tiedostoon ```<module name='TreeWalker'>``` -tagin alaisuuteen (!): 

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
    <property name="checkFirstSentence" value="true"/>
  </module>
```

Jos laitoit väärään kohtaan, niin saat 100% varmasti virheviestejä. Jos ajoit nyt jo checkstylen, niin saat todella paljon uusia 
virheitä, koska checkstylen raportointi on nyt kattavampaa. Muutetaan siis vielä raportointi niin, että tietyt tiedostot
jätetään pois (esimerkiksi Main.java-tiedostosi). Lisää siis seuraava määritys ```<module name='TreeWalker'>```-tagin ulkopuolelle (!!)
esimerkiksi siis ```<module name='FileLength'>```-tagin ylä- tai alapuolelle, mutta kuitenkin niin, että se on ```<module name='Checker'>```-
tagin alaisuudessa:

```xml
    <module name="SuppressionFilter">
    	<property name="file" value="mysuppressions.xml" />
    </module>
```


Seuraavassa siis esimerkikki checkstyle.xml-tiedostosta: 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE module PUBLIC "-//Puppy Crawl//DTD Check Configuration 1.3//EN" "http://www.puppycrawl.com/dtds/configuration_1_3.dtd">
<module name='Checker'>

    <module name='TreeWalker'>

        <property name='tabWidth' value='4' />
	      
	      <!-- Paljon moduuleja välissä -->
        
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

    </module>

    <!-- File Length -->

    <module name="SuppressionFilter">
    	<property name="file" value="mysuppressions.xml" />
    </module>

    <module name='FileLength'>
        <property name='max' value='200' />
    </module>

</module>
```

Nyt puuttuu enää itse mysuppressions.xml-tiedoston luonti. Luo siis samaan kansioon missä checkstyle.xml-tiedostosi sijaitsee tiedosto
`mysuppressions.xml` ja anna sen sisällöksi seuraava:

```xml
<?xml version="1.0"?>

<!DOCTYPE suppressions PUBLIC
    "-//Puppy Crawl//DTD Suppressions 1.1//EN"
    "http://www.puppycrawl.com/dtds/suppressions_1_1.dtd">

<suppressions>
    <suppress files="<Tiedostosi1>.java" checks="[a-zA-Z0-9]*"/>
    <suppress files="<Tiedostosi2>.java" checks="[a-zA-Z0-9]*"/>
</suppressions>
```

Korvaamalla `<Tiedostosi1>` ja `<Tiedostosi2>` niillä tiedostojen nimillä, joita et halua testata, poistaa tiedostot checkstylen 
testauksen näköalueelta (voit kopioida kumman tahansa rivin ja liittää sen aina toisen alle, että saat enemmän kuin kaksi). 
Sallittuja tiedostoja ovat esimerkiksi UI-luokat. Siis esimerkiksi Swingin automaattisesti generoimat luokat ja GUI-editorin
avulla luodut UI-luokat. Eli jos luokka on 100% sinun tekemäsi, niin **älä** laita sitä pois checkstylestä.
