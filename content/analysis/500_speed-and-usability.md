Hastighet och användbarhet
======================
Jag har försökt få tre webbplatser som har större skillnader i resultat för att lättare kunna se vad som gör en sida långsammare eller inte. Två sidor är samma som i förra kursmomentet där en sida är ”lightweight” så att säga med nästan bara text och den andra sidan har mycket och stora bilder med animationer på knappar med mera. Sen har jag försökt ta en mittemellan sida vilket resulterade i Wikipedia.

För att samla in alla mätvärden använde jag Chrome DevTools och Google PageSpeed. För det som skulle göras kändes det som att det skulle bli tillräckligt exakta och bra värden för att jämföra med. Jag började med att samla informationen från DevTools genom att gå in på sidorna och ladda om den utan caching och notera laddningstiden, mängden data och antalet requests. Sedan gick jag vidare till att använda PageSpeed och notera betyget och förbättringsalternativen.

All data finns i den länkade Excel-filen: [PageLoadTimes.xlsx](https://files.rasmussteen.com/School/PageLoadTimes.xlsx)

###Archlinux.org

![Archlinux.org](image/archlinux.png?w=960)
[https://www.archlinux.org/](https://www.archlinux.org/)

Mätvärden DevTools
| Tid (ms) | DOM (ms) | Load (ms) | Items | Size (KB)
--- | --- | --- | --- | --- | ---
T1 | 542 | 509 | 514 | 8 | 146
T2 | 524 | 491 | 491 | 8 | 146
T3 | 509 | 484 | 479 | 8 | 146
T4 | 505 | 472 | 483 | 8 | 146
T5 | 531 | 501 | 499 | 8 | 146
Avg | 522,2 | 491,4 | 493,2 | 8 | 146

PageSpeed Data, tabellen nedan visar på möjliga förbättringar.

Mobile (Needs Work) | Desktop (Needs Work)
--- | ---
Redirects | Redirects
Compression | Compression
Renderblocking | Renderblocking

Med mätdatat i bakhuvudet så känns det som att aktivera komprimering är en bra ide samt att fixa till dessa redirects. Jag noterade även att en bild (logotypen) alltid laddades jättesent, där kanske renderblockingen kommer ifrån.

###Wikipedia.org

![Wikipedia.org](image/wikipedia.png?w=960)
[https://sv.wikipedia.org/wiki/Portal:Huvudsida](https://sv.wikipedia.org/wiki/Portal:Huvudsida)

Mätvärden DevTools
| Tid (ms) | DOM (ms) | Load (ms) | Items | Size (KB)
--- | --- | --- | --- | --- | ---
T1 | 1420 | 715 | 1550 | 64 | 579
T2 | 1360 | 666 | 1480 | 64 | 560
T3 | 1310 | 650 | 1420 | 64 | 583
T4 | 1400 | 675 | 1460 | 64 | 571
T5 | 1390 | 693 | 1460 | 64 | 579
Avg | 1376 | 679,8 | 1474 | 64 | 574,4

PageSpeed Data, tabellen nedan visar på möjliga förbättringar.

Mobile (Needs Work) | Desktop (Good)
--- | ---
Redirects | Redirects
Renderblocking | Renderblocking
Caching | Caching
Optimize Images |

Jag blir förvånad över att se att denna sida inte utnyttjar caching till fullo då det finns en del bilder på denna sida, det är något man kan förbättra. Att optimera bilder för mobila enheter borde också kunna klaras av. Fixa till redirects.

###Taxicaller.com

![Taxicaller.com](image/taxicaller.png?w=960)
[https://www.taxicaller.com/en/](https://www.taxicaller.com/en/)

Mätvärden DevTools
| Tid (ms) | DOM (ms) | Load (ms) | Items | Size (MB)
--- | --- | --- | --- | --- | ---
T1 | 2780 | 913 | 2270 | 61 | 2
T2 | 2730 | 850 | 2220 | 61 | 2
T3 | 2760 | 909 | 2260 | 61 | 2
T4 | 2830 | 886 | 2640 | 61 | 2
T5 | 3780 | 914 | 3580 | 63 | 2
Avg | 2976 | 894,4 | 2594 | 61,4 | 2

PageSpeed Data, tabellen nedan visar på möjliga förbättringar.

Mobile (Poor) | Desktop (Needs Work)
--- | ---
Redirects | Optimize Images
Renderblocking | Renderblocking
Caching | Redirects
Compression | Minify CSS
Optimize Images | Caching
Minify CSS | Minify HTML
Minify HTML |

Minifya HTML och CSS är uppenbara saker att göra. Optimera bilder, speciellt eftersom sidan har många och stora bilder. Dem kanske skulle skaffa sig Cimage.

###Sammanfattning

Med all denna data så syns tydligt att det verkar svårt att komma undan redirects och renderblocking. Det var något som alla sidor hade gemensamt. Archlinux hade det problemet och den är 146 kb. Procentuellt så är det jättemycket tid förlorat jämfört med till exempel taxicaller. Man måste inte alltid ha www framför det gåt att ha \*.domän och alltid visa huvudsidan där och bara visa något annat om det faktiskt finns en subdomän. Renderblocking kan nog vara svår att bli av med men en del grejor kan man verkligen sätta inline-css på som en knapp vars enda style var att den skulle vara blå kunde definitivt haft inline css.

Prispallen (laddnigshastighet)

1. Archlinux

2. Wikipedia

3. Taxicaller

Inte ett helt oväntat resultat. Det syntes tydligt vilken sida som skulle ladda snabbast när man besökte dem första gången. Archlinux är väldigt ”lightweight” och visar bara information. Snabbt går det också. Och taxicaller med alla sina animationer och senaste css tog längst tid. Den tog för mig ca 2,5 sekunder att ladda vilket jag tycker är väldigt lång tid.Wikipedia låg precis på gränsen med 1,5 sekunder. Archlinux klarade sig bra på ca 0,5 sekunder. Där i mitten ungefär ligger hastigheten jag tycker är acceptabel, måste jag get ett exakt svar skulle jag säga 1,25 sekunder.

Jag har jobbat ensam och mitt namn är Rasmus Steen.
