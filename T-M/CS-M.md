# Creating Strings

Generoi kaikki mahdolliset erilaiset merkkijonot hyödyntämällä annetun merkkijonon kaikkia kirjaimia.

**Sisääntulo**

---

Merkkijono, joka on pituudeltaan n ja sisältää merkkejä väliltä a-z.

**Ulostulo**

---

Luku k, joka kertoo mahdollisten merkkijonojen määrän, jonka jälkeen k määrä mahdollisia merkkijonoja aakkosjärjestyksessä.

**Rajoitukset**

---

Pituus n on pienemmillään 1 ja suurimmillaan 8.

**Esimerkki**

---

Sisääntulo: aabac

Ulostulo: 20 aaabc aaacb aabac aabca aacab aacba abaac abaca abcaa acaab acaba acbaa baaac baaca bacaa bcaaa caaab caaba cabaa cbaaa

**Huomiot**

---

- Mahdolliset ja toisistaan erilaiset merkkijonot voidaan selvittää kaavan P(Erilaiset merkkijonot) = (annettun merkkijonon pituuden kertoma)/(annettun merkkijonon aakkosten kertomien kerroin), jonka takia esimerkin sisätulo merkkijonon aabac tapauksessa saadaan P(EM) = (5!)/(3!x1!x1!) = 20.
- Tarkastamalla esimerkin ulostulon merkkijonojen aakkosjärjestystä huomataan, että merkkijono aaabc muutetaan 19 kierroksen aikana yhden liikkeen kautta vähitellen merkkijonoksi cbaaa, joten on mahdollista tulostaa kaikki erilaiset merkkijonot while loopin kautta.
- Koska annettu merkkijono koostuu a-z kirjaimista, on helpoin tapaus ainoastaan yhdestä kirjaimesta koostuva merkkijono riippumatta pituudesta ja vaikein tapaus merkkijono pituudeltaan 8, joka koostuu eri kirjaimista. 
- Kirjaimet a-z on arvoitettu siten, että a omistaa pienimmän arvon ja z suurimman arvon, jonka takia vertailut kirjaimien välillä voidaan tehdä.

**Aakkosjärjestys algoritmi**

---

Oletetaan, että annettaan merkkijono abc, joka täytyy muuttaa muotoon cba ainoastaan 6 kierroksen aikana yhden liikkeen avulla.Mahdolliset liikkeet ovat paikkojen vaihto siirtopaalun edessä olevan kirjaimen kanssa ja siirtopaalun kirjaimen vaihto, joita hyödyntämällä tehtävä voidaan suorittaa seuraavasti:

1. abc (Siirtopaalun kirjaimen c vaihtaminen kirjaimeen b)
2. acb (Siirtopaalun kirjaimen b vaihtaminen kirjaimeen c)
3. bac (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
4. bca (Siirtopaalun kirjaimen vaihtaminen kirjaimeen b)
5. cab (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
6. cba (Tavoite saavutettu, joten liikkeitä ei enää tarvita)

Samanlaiset toimet tapahtuvat myös esimerkin tapauksessa, sillä:

1. aaabc (Siirtopaalun kirjaimen c vaihtaminen kirjaimeen b)
2. aaacb (Siirtopaalun kirjaimen b vaihtaminen kirjaimeen c)
3. aabac (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
4. aabca (Siirtopaalun kirjaimen c vaihtaminen kirjaimen c)
5. aacab (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
6. aacba (Siirtopaalun kirjaimen b vaihtaminen kirjaimeen c)
7. abaac (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
8. abaca (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
9. abcaa (Siirtopaalun kirjaimen c vaihtaminen kirjaimeen b)
10. acaab (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
11. acaba (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
12. acbaa (Siirtopaalun kirjaimen b vaihtaminen kirjaimeen c)
13. baaac (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
14. baaca (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
15. bacaa (Kirjaimen a vaihto siirtopaalun kirjaimen c kanssa)
16. bcaaa (Siirtopaalun kirjaimen c vaihtaminen kirjaimeen b)
17. caaab (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
18. caaba (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
19. cabaa (Kirjaimen a vaihto siirtopaalun kirjaimen b kanssa)
20. cbaaa (Tavoite saavutettu, joten liikkeitä ei enää tarvita)


**Ratkaisun osiot**

---

1. Sisääntulon merkkijonon varastoiminen
2. Merkkijonon kirjainten arvon ja määrän varastointi
3. Mahdollisten merkkijonojen laskeminen
4. Ensimmäisen merkkijonon luonti
5. Merkkijonojen tulostaminen

**Ratkaisu**

---

Ensimmäisen osion pseudokoodi voisi olla muodoltaan:

1. Luo String muuttuja
2. Luo tarvittava koodi, jonka avulla ohjelma ottaa sisätulon merkkijonon
3. Varastoi sisätulo String muuttujaan

Toisen osion pseudokoodi voisi olla muodoltaan:

1. Valitse tietorakenne, joka mahdollistaa avain-arvo parit ja järjestää avaimet pienemmästä suurempaa riippumatta niiden sisältämistä arvoista
2. Luo while-looppi, jossa käyt läpi merkkijonon jokaisen kirjaimen siten, että lisäät uuden kirjain arvon tietorakenteeseen ja päivität entisten avainten kirjain määrät

Kolmannen osion pseudokoodi voisi olla muodoltaan:

1. Luo funktio, joka mahdollistaa n! laskennan, eli luvun 3 antaminen sille saisi sen palauttamaan luvun 6
2. Käytä funktiota laskemaan kaikki mahdolliseet merkkijonojen määrä antamalla merkkijonon pituus
3. Luo while-looppi, jossa käyt tietorakenteen varastoimat avain-arvo parit siten, että käytät funktiota laskemaan jokaisen avaimen arvon kertoimen ja kerrot sen toistuvien merkkijonojen kanssa
4. Loopin päätyttyä, jaa kaikki mahdolliset merkkijonojen määrä toistuvien merkkijonojen määrällä, jonka jälkeen varastoi se muuttujaksi

Neljännnen osion pseudokoodi voisi olla muodoltaan:

1. Luo String muuttuja, jonka haluat edustavan muutettavaa merkkijonoa
2. Luo while-looppi, jossa käyt pienemmästä avaimesta suurempaan järjestetyn tietorakenteen siten, että avaimen arvon mukainen kirjain lisätään siihen liitetyn arvon määrän String muuttujaan

Viimeisen osion pseudokoodi voisi olla muodoltaan:

1. Luo While-looppi, joka suorittaa mahdollisten merkkijonojen määrän kierroksia ja tulostaa jokaisella kierroksella muutettavan merkkijonon 
2. Lisää loopin sisälle tarvittavan if-lauseet, jotka toteuttavan aakkosjärjestys algoritmin toiminnan
    





