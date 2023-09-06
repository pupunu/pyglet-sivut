# Kurssisivupohja

## Käyttöönotto

Kloonaa repo tai ota template käyttöön githubissa. Templaten saa käyttöön klikkaamalla "Use this template" githubissa, jolloin githubissa voi luoda uuden repon, jossa on pohjana templaten tiedostot. Tämän jälkeen template repo pitää kuitenkin kloonata, jos haluaa tiedostot paikallisesti.

Mene paikallisesti sivun hakemistoon ja aja komento `bundle install`. Tämän jälkeen pohjan voi käynnistää paikallisesti komennolla `bundle exec jekyll serve -w -l`.

### _config.yml

Hakemiston juuressa on tiedosto `_config.yml`. Muokkaa kurssin tiedot tiedostoon seuraavasti

* `title: Kurssin nimi` korvaa "Kurssin nimi" kurssin nimellä. Laita nimeen `&shy;` merkintä niihin kohtiin, josta teksti voidaan tavuttaa. Tämä saa kurssin nimen rivittymään tavuviivoineen oikein pienessä tilassa.
* `baseurl: "/course-template-light"` Korvaa "/course-template-light" repon nimellä, jossa kurssi sivu julkaistaan. 
* `url: "https://millakortelainen.github.io/course-template-light/"` Vaihda url osoite sivun osoitteeksi. Tämän saa yleensä sillä, että julkaiee sivun github pages:ssä. Käytännössä osoite on muotoa `https://<käyttäjä/organisaatio>.github.io/<repon-nimi>/`.

### Materiaali

Materiaali on jaettu kahteen osaan. Staattiset sivut, jossa voi olla tietoa kurssista on hakemistossa `_pages`. Kurssimateriaali on hakemistossa `_content`. Sivun etusivu on tiedosto `index.md` joka on hakemiston juuressa.

Jokaisen sivun alussa on "frontmatter", joka on merkitty viivojen sisälle

```jekyll
---
layout: default
nav-title: Etusivu
---
```

Se sisältää metatietoja sivusta, jota voidaan käyttää sivun kääntämisvaiheessa.

#### _pages

Hakemisto staattisille. Lisää määre `hidden: true` frontmatteriin, jotta sivu ei tule näkyviin valikkoon. 

Sivut järjestetään valikkoon aakkosjärjestyksessä.
TODO: sivut järjestetään annetun arvon perusteella. 

#### _content

Kurssimateriaali on hakemistossa `_content`. Jokaisella kurssin osalle voidaan tehdä oma kansio, johon tehdään tiedosto `index.md`, joka on materiaalisivu. Tiedoston alkuun lisätään frontmatter, joka sisältää kentät 

```
---jekyll
nav-title: Osa 1
sub-sections:
      - sub-section-title: Osa 1-1 Otsikko
      - sub-section-title: Osa 1-2 Otsikko
      - sub-section-title: Osa 1-3 Otsikko
---
```

Materiaalin voi kirjoittaa tälle sivulle tai sille voi tehdä alaosioa, jolloin ne liitetään materiaaliin käyttämällä `{% include_relative osa-1-1.md %}`.

### Sivun layout

_Frontmatterissa_ on kenttä `layout`. Layout tyyppejä on kaksi `chapter` ja `default`. Sivujen layout on `chapter` oletusarvoisesti.

#### `chapter`

Yksinkertainen materiaalisivu.

#### `default`

Etusivu tyyppinen sivu, jossa sivun otsikko on korostettu värilliseen laatikkoon.

### Github Action konfigurointi

Github Actions tarvitaan, jotta itsetehdyt pluginit toimii. Sitä ei tarvitse erikseen konfiguroida.
