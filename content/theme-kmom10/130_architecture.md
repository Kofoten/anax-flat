Architecture
=========================

[FIGURE src="https://i.imgur.com/YtlzC35.png" class="right" caption="Folder structure"]

Som du kan se i bilden till höger har jag delat upp mona moduler i olika kategorier. Jag har försökt göra indelningen så logisk och tydlig som möjligt.

- Grid: Det som har att göra med det vertikala girdet.
- Layout: Det som styr vart objekt ligger i förhållande till objekt runt omkring.
- Plugins: Olika pluginstyles t.ex menyslidern.
- Theme: Det slutgiltiga temat med färger och andra finjusteringar
- Typography: Det som har att göra med det horisontella grided.

Dessa laddas i ordningen: grid, typography, plugins, layout, theme. Filerna i dessa mappar gör vad som står på mappen och allt utom theme bygger egentligen upp bastemat med det är alltid det temat som laddas från theme som har sista ordet då den alltid ska ladda sist och skriva över det som tidigare less moduler gjort om temaskaparen vill att det skall se ut på något annat sätt. Något jag jobbat mycket med är filerna i layout mappen och theme mappen för att få dessa att lira ordentligt med varandra.

Dessa filer bygger tillsammans upp ett tema. Layout står för positionering och theme för färger och vid behov också positionering. För att se exempel gå till [temaväljaren](/theme-selector) och byt till base eller default. Här ser du att det i base endast finns layout då allt fortfarande ligger nästan där det ska men om du byter tillbaka till default så ser du att färger och styling på länkar kommer tillbaka. Jag tycker att med denna uppbyggnad av modulerna så kan du bygga ett helt eget tema fast du använder base temat då din fil laddar sist eller om du vill flytta något så slipper du ändra i alla oloka temafiler utan du ändrar bara i den layoutfil ändringen berör. Då har man enligt mig lyckats, när en ändring på ett ställe slår igenom överallt utan trams och bråk. Din less kod blir också i de flesta fall mer DRY.
