# Projekta darbs "Citātu izgūšanas un analīzes programma"
**Izstrādāja: Ance Riņķe; Paula Ekerte; Dāvis Kononovs**
---
## Projekta uzdevums

Šī projekta, kas veikts Python galvenais uzdevums ir izmantojot tīmekļa skrāpēšanas (webscraping) principu, iegūtu datus no vietnes [quotes.toscrape.com](https://quotes.toscrape.com). Programmas mērķis ir:

	- Automātiski ielādēt visus citātus no vietnes, to autorus un saistītās kategorijas.
	- Piedāvāt lietotājam iespēju izmantot dažādas funkcijas komandrindas saskarnē:
 	- Skatīt citātus pēc autora vārda.
	- Skatīt citātus pēc tēmas jeb taga.
 	- Apskatīt detalizētu informāciju par autoru.
  	- Sakārtot autorus pēc dzimšanas datuma.
  	- Iegūt nejauši izvēlētu citātu.
  	- Meklēt citātus pēc atslēgvārda.

Šī programma parāda praktisku piemēru, kā veikt datu vākšanu no tīmekļa, strukturēt to lietotājam saprotamā formā, un nodrošināt ērtu piekļuvi šiem datiem.

---

## Izmantotās Python bibliotēkas

Programmas izstrādes laikā tika izmantotas šādas Python bibliotēkas:

- **requests**  
	Šī bibliotēka ir viena no visbiežāk izmantotajām HTTP pieprasījumu veikšanai Python valodā. Projektā tā tiek izmantota, lai lejupielādētu HTML saturu no ārējās vietnes quotes.toscrape.com. Katras lapas saturs tiek iegūts ar requests.get() funkciju, kas ļauj piekļūt citātiem, autoru lapām un pārvietoties pa vairākiem lapošanas līmeņiem. Šīs bibliotēkas vienkāršā sintakse un uzticamība padara to ļoti piemērotu webscraping uzdevumiem.

- **BeautifulSoup (no bs4)**  
	Bibliotēka, kas ļauj analizēt un strukturēt HTML dokumentus. Projektā BeautifulSoup tiek izmantota, lai no ielādētā HTML koda "izvilktu" konkrētus datus — piemēram, atrastu katru citātu, autora vārdu, tagus, kā arī atsevišķas autora biogrāfijas lapas datus, piemēram, dzimšanas datumu un vietu. Tā ļauj viegli navigēt HTML kokā un meklēt elementus pēc klasēm, tagiem vai atribūtiem, kas padara datu vākšanu efektīvu un saprotamu.

- **datetime**  
	Šī Python iebūvētā bibliotēka nodrošina darbu ar datumiem un laikiem. Programmā tā tiek izmantota, lai pārveidotu autoru dzimšanas datumus no teksta ("January 1, 1900") uz datetime objektu formātu. Tas ļauj sakārtot autorus pēc dzimšanas gadiem un pēc tam attēlot tos hronoloģiskā secībā. datetime.strptime() funkcija tiek izmantota datuma pārformatēšanai no teksta formāta uz Python objektu, kas vēlāk ļauj veikt datumu salīdzināšanu.

- **random**  
	Šī bibliotēka tiek izmantota, lai nodrošinātu nejaušības funkcionalitāti. Projektā tā tiek lietota, lai izvadītu nejauši izvēlētu citātu no visiem savāktajiem. Funkcija random.choice() izvēlas vienu elementu no saraksta, un šajā gadījumā tā palīdz lietotājam ieraudzīt dažādus iedvesmojošus vai pārdomu pilnus citātus, nezinot iepriekš, kurš tiks parādīts.

---

## Lietotās datu struktūras

Projekta ietvaros ir izmantotas vairākas Python iebūvētas datu struktūras:

- **Vārdnīca (`dict`)**  
  Saglabā visu autoru informāciju (`data["authors"]`), kā arī visus citātus (`data["quotes"]`), kur katrs ieraksts satur tekstu, autoru un tagus.

- **Saraksts (`list`)**  
  Satur visus citātus, katrs kā vārdnīca ar nepieciešamo informāciju. Arī izmantots autoru un tagu saglabāšanai un kārtošanai.

- **Kopa (`set`)**  
  Lietota, lai saglabātu unikālos tagus un autorus, pirms tie tiek konvertēti uz sarakstu.

- **Datetime objekti**  
  Dzimšanas datumu saglabāšanai kā `datetime` objekti, lai būtu iespējams tos loģiski kārtot.

---

## Programmatūras izmantošana

Lietotājs palaižot programmu terminālī, saņem sarakstu ar sekojošām izvēlēm:

1. **Citāts pēc autora**  
	Šī funkcionalitāte ļauj lietotājam izvēlēties konkrētu autoru, lai apskatītu visus viņa citātus, kas atrodami vietnē quotes.toscrape.com. Programma piedāvā sarakstu ar visiem pieejamajiem autoriem, no kura lietotājs var izvēlēties konkrēto pēc tā nummerācijas vai arī manuāli ievadot autora vārdu. Ja autora vārds eksistē datu kopā, programma izvada visus šī autora citātus. 

2. **Citāts pēc kategorijas (taga)**  
	Lietotājam tiek piedāvāts saraksts ar visām tēmām (tagiem), kas atroda konkrētajā vietnē, piemēram: life, love, truth, inspirational, utt. Lietotājs var izvēlēties tēmu no saraksta vai arī to ievadīt manuāli. Pēc tam programma izvada visus citātus, kuri saistīti ar izvēlēto kategoriju.

4. **Informācija par autoru**  
	Lietotājam ir iespēja iegūt papildus informāciju par konkrētu autoru. Ievadot autora vārdu vai izvēloties to no saraksta, programma parāda šādu informāciju:

dzimšanas datumu,

dzimšanas vietu,

īsu biogrāfisku aprakstu.

5. **Autoru kārtošana pēc dzimšanas gada**  
	Programma ļauj lietotājam apskatīt visu autoru sarakstu, sakārtotu hronoloģiskā secībā — sākot no vecākā autora līdz jaunākajam. Dzimšanas datumi tiek apstrādāti kā datetime objekti, kas nodrošina precīzu kārtošanu.

6. **Nejaušs citāts**  
	Lai padarītu programmu dinamiskāku un pārsteidzošāku, ir ieviesta funkcija, kas lietotājam parāda nejauši izvēlētu citātu no visa datu kopuma. Tas sniedz iespēju iepazīties ar dažādiem autoriem un tematiem bez iepriekšējas izvēles. 

7. **Citātu meklēšana pēc atslēgvārda**  
	Lietotājs var ievadīt jebkādu vārdu vai frāzi, un programma veic meklēšanu visos citātos, lai atrastu tos, kuros šis vārds/izteiciens parādās. Tas ļauj atrast konkrētiem vārdiem atbilstošus citātus — piemēram, ja ievada "happiness", tiks parādīti visi citāti, kuros šis vārds ir minēts.

Programmas darbība turpinās līdz lietotājs ievada `'stop'`.

---

## Secinājumi

Šis projekts ir lielisks piemērs tam, kā ar Python palīdzību iegūt strukturētus datus no tīmekļa un pārveidot tos par interaktīvu rīku. Tas parāda, cik vienkārši var savienot webscraping ar praktisku pielietojumu — šajā gadījumā, iespēju ērti pārlūkot citātus pēc autora, tēmas vai atslēgvārda.

Projekta gaitā nācās strādāt gan ar datu apstrādi, gan domāt par to, kā padarīt lietotāja pieredzi saprotamu un ērtu, izmantojot vienkāršu komandrindas izvēlni. Tika izmantotas dažādas Python iespējas un bibliotēkas, kas ne tikai automatizē darbu ar datiem.

