# Citātu izgūšanas un analīzes programma

## Projekta uzdevums

Šī Python programmā tiek izmantots tīmekļa skrāpēšanas (web scraping) princips, lai iegūtu datus no vietnes [quotes.toscrape.com](https://quotes.toscrape.com). Programmas mērķis ir:

	- Automātiski ielādēt visus citātus no vietnes, to autorus un saistītās kategorijas (tagus).
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
  Nodrošina HTTP pieprasījumu veikšanu, lai ielādētu tīmekļa lapas saturu.

- **BeautifulSoup (no bs4)**  
  Lietota HTML dokumenta parsēšanai, lai izgūtu konkrētus datus (citātus, autorus, tagus) no lapas struktūras.

- **datetime**  
  Nodrošina datumu apstrādi, kas nepieciešama autoru dzimšanas datumu salīdzināšanai un kārtošanai.

- **random**  
  Izmantota nejauša citāta izvēlei no ielādētā datu kopuma.

Šīs bibliotēkas izvēlētas to vienkāršības, dokumentācijas un piemērotības dēļ šim uzdevumam. Tās ir bieži izmantotas datu apstrādes un tīmekļa skrāpēšanas projektos.

---

## Lietotās datu struktūras

Projekta ietvaros ir izmantotas vairākas lietotāja definētas un Python iebūvētas datu struktūras:

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

Lietotājs palaizh programmu terminālī, kur viņam tiek piedāvātas sekojošas izvēles:

1. **Citāts pēc autora**  
   Lietotājs var izvēlēties autoru no saraksta vai ievadīt viņa vārdu, lai iegūtu visus autora citātus.

2. **Citāts pēc kategorijas (taga)**  
   Lietotājs izvēlas vai ievada kādu no tagiem (piemēram, "life", "love", "inspirational"), lai redzētu ar šo tēmu saistītos citātus.

3. **Informācija par autoru**  
   Lietotājs var pieprasīt detalizētu informāciju par autoru, piemēram, dzimšanas datumu, vietu un īsu biogrāfiju.

4. **Autoru kārtošana pēc dzimšanas gada**  
   Parāda visus autorus sarindotus no vecākā uz jaunāko.

5. **Nejaušs citāts**  
   Parāda vienu nejauši izvēlētu citātu.

6. **Citātu meklēšana pēc atslēgvārda**  
   Meklē visus citātus, kuros parādās lietotāja ievadītais vārds vai frāze.

Programmas darbība turpinās līdz lietotājs ievada `'stop'`.

---

## Secinājumi

Šis projekts ir labs piemērs, kā iegūt un izmantot strukturētus datus no tīmekļa, pielietot Python datu struktūras un veidot praktisku, interaktīvu programmatūru ar komandrindas saskarni. Tas uzlabo gan datu apstrādes, gan lietotāja pieredzes veidošanas prasmes.


