#RAUPJC 0.DZ
#JMBAG: 0036485747
<hr>
#1
Nakon što je projektu konzolna aplikacija dodana referenca na class library te je projekt build-an, u bin/debug folderu konzolne aplikacije nalazi se .dll class library projekta.
Ako taj .dll pobrišemo i pokušamo pokrenuti .exe, aplikacija se zapravo neće pokrenuti. Potrebno je ponovno build-ati cijeli soulution kako bi se ponovno kreirao .dll class projekta. Datoteka .exe konzolne aplikacije ovisi o .dll datoteci class library projekta.

#2
Ako izmjenimo string koji ispisuje MyConsole.PrintHelloWorld() metoda i pokrenemo konzolnu aplikaciju bez prevođenja, ispisat će se stari string.
Konzolna aplikacija je zapravo koristila neizmjenjenu .dll datoteku. Projekt konzolne aplikacije je potrebno ponovno prevesti kako bi se ažurirala .dll datoteka.

#3
Ispisalo se: "Pero: Hello World"

#4
Nakon što smo dodali PeroClassLibrary kao referencu i build-ali, u bin/debug folderu se nalazi i PeroClassLibrary.dll

#5
Nakon brisanja originalnog .dll-a sa disku, aplikacija i dalje radi jer je u bin/debug folderu konzolne aplikacije .dll od zadnjeg builda.
Nakon brisanja originalnog .dll-a sa diska, build projekta i dalje prolazi jer se projekt sada referencira na .dll iz bin/debug foldera, a ne na sada nepostojeći originalni .dll.

#6
Navedeno se odnosi na MonoDevelop IDE.
Ako pobrišemo NodaTime direktorij iz packages direktorija, aplikaciju možemo buildati ako nismo koristili NodaTime paket (dobivamo warning). Ako smo u programu koristili NodaTime paket compiler će javiti error koji nam govori da build proces nije uspio pronaći NodaTime namespace iako je NodaTime naveden u packages.config datoteci. S obzirom da je NodaTime paket naveden u packages.config datoteci možemo desnim klikom na packages direktorij te odabirom opcije restore ili update ponovno skinuti NodaTime paket. Build proces nakon toga prolazi.
<div style="padding-bottom: 10px"><img src="https://raw.githubusercontent.com/Sokre95/RAUPJC_0DZ/master/nodaTIme.png" width="248px"></div>
<div><img src="https://raw.githubusercontent.com/Sokre95/RAUPJC_0DZ/master/error.png" width="348px"></div>