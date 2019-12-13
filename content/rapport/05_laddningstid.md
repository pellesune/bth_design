---
---
Laddningstid (kmom05)
=========================
Uppgiften går ut på att att mäta hur snabbt tre olika webbplatser laddas, samt om de innehåller några saker som kan förbättras vad gäller laddningstid och användbarhet.

Urval
-------------------------
<table style="border-spacing: 4px; border-collapse: separate">
    <tr>
        <td style="width: 30%;"><a href="../htdocs/img/theSun.jpg"><img src="../htdocs/img/theSun.jpg" style="width: 200px;" target="_blank" alt="_"></a></td>
        <td>
            <a href="https://www.thesun.co.uk/"><b>The Sun</b></a><br />
            En brittisk nyhetssajt, vald dels med anledning av parlamentsvalet och dels för att nyhetssajter ofta har mycket bilder, annonser och andra saker som ska laddas.
        </td>
    </tr>
    <tr>
        <td style="width: 30%;"><a href="../htdocs/img/axiell.jpg"><img src="../htdocs/img/axiell.jpg" style="width: 200px;" target="_blank" alt="_"></a></td>
        <td>
            <a href="https://www.axiell.com/se/"><b>Axiell</b></a><br />
            Ett större företag fokus på bibliotek, arkiv och museer. Webbplatsens innehåll illusteras av en stor mängd bilder.  
        </td>
    </tr>
        <td style="width: 30%;"><a href="../htdocs/img/arngren.jpg"><img src="../htdocs/img/arngren.jpg" style="width: 200px;" target="_blank" alt="_"></a></td>
        <td>
            <a href="http://arngren.net/"><b>Arngren.net</b></a><br />
            Tips från en norsk bekant. En rörig webbplats många bilder och gif:ar. Vi ville ha med den bara för att det är ett hemskt exempel på en webbplats.
        </td>
    </tr>
</table>

Metod
-------------------------
De verktyg vi använt oss av i vår undersökning har främst varit *Chrome DevTools* och *[Google Pagespeed insights](https://developers.google.com/speed/pagespeed/insights/)*. Verktygen användes för mätningar av tre sidor på de utvalda webbplatserna.

Resultat
-------------------------
<table style="border-spacing: 4px; border-collapse: separate">
    <tr>
        <th></th>
        <th>The Sun</th>
        <th>Axiell</th>
        <th>Arngren.net</th>
    </tr>
    <tr>
        <th style="width: 10%; vertical-align:middle;">Pagespeed-betyg</th>
        <td style="width: 30%;" valign=top>
            Desktop: <b>19</b><br />
            Mobile: <b>5</b>
        </td>
        <td style="width: 30%;" valign=top>
            Desktop: <b>97</b><br />
            Mobile: <b>78</b>
        </td>
        <td style="width: 30%;" valign=top>
            Desktop: <b>98</b><br />
            Mobile: <b>58</b>
        </td>
    </tr>
    <tr>
        <th style="width: 10%; vertical-align:middle;">Devtools networks (snitt)</th>
        <td style="width: 30%;" valign=top>
            Cache disabled Load: <b>9,23 s</b><br />
            Cache enabled Load: <b>7,16 s</b><br />
            Requests: <b>474,33</b><br />
            Resources: <b>16,91 MB</b>
        </td>
        <td style="width: 30%;" valign=top>
            Cache disabled Load: <b>1,37 s</b><br />
            Cache enabled Load: <b>0,52 s</b><br />
            Requests: <b>49,33</b><br />
            Resources: <b>2,07 MB</b>    
        </td>
        <td style="width: 30%;" valign=top>
            Cache disabled Load: <b>7,34 s</b><br />
            Cache enabled Load: <b>1,48 s</b><br />
            Requests: <b>160</b><br />
            Resources: <b>1,42 MB</b>
        </td>
    </tr>
    <tr>
        <th style="width: 10%; vertical-align:middle;">Åtgärd</th>
        <td style="width: 30%;" valign=top>
            En översyn av inläsning av JS-kod och formatmallar skulle behövas för att de inte ska blockerar sidans första rending. Man skulle även kunna minifiera JS-filerna samt rensa CSS-filer på av oanvända regler, samt se över bildformat och bildstorlek samt se till att bildkodningen är optimalt.
        </td>
        <td style="width: 30%;" valign=top>
            En översyn av inläsning av JS-kod och formatmallar skulle behövas för att de inte ska blockerar sidans första rending. Man skulle även kunna minifiera JS-filerna samt rensa CSS-filer på av oanvända regler, samt se över bildformat och bildstorlek samt se till att bildkodningen är optimalt.
        </td>
        <td style="width: 30%;" valign=top>
            En översyn av bildformat och bildstorlek skulle behövas, samt se till att bildkodningen är optimalt. GIF-filer skulle bytas mot annat format eller uteslutas helt.
        </td>
    </tr>
</table>

[Dokument med rådata](../content/rapport/laddningstid_kmom05.pdf)

Analys
-------------------------
Både Axiell och Arngren.net lämpade sig väl för dessa tester, the Sun var däremot lite krångligare. Den webbplatsen har många element som är dynamiska, det sker konstant requests vilket gör att laddtiden på sätt och viss är missvisande eftersom den aldrig laddas klart. Den gemensamman nämnaren när det kommer till förbättringsmöjligheter på webbplatserna är dock *bilder*. Alla tre har förbättringspotential när det kommer till just bildhantering; bildformat, bildstorlek och bildkodningen.

För vår del anser vi att laddtider som överstiger 3 sekunder är för långsamt. Det finnas naturligtvis undantag, förväntad laddtid är avhängigt innehåll, men tre sekunder är en vår generella brytpunkt. På de premiserna är det bara Axiell som klarar sig helt, även om Arngren.net klarar sig efter den cachats. The Sun, liksom många nyhetssajter, har så mycket innehåll att en regel på tre sekunder troligen är ett allt för högt krav, men nästan 10 sekunder i snitt är i vårt tycke allt för segt. Cachad snittar the Sun på 66 requests/s, medan Axiell snittar på 95 requests/s och Arngren.net på 108 requests/s (ocachade snittar respektive webbplats på 51 requests/s, 36 requests/s och 22 requests/s). En osäkerhetsfaktor när det kommer till the Sun är dock att mätningarna gjordes på dagen för parlamentsvalet i Storbritannien. Sajten kan således varit under ett högt tryck vid tidpunkten för mätningarna.

Något vi blev varse under arbetet med uppgiften var att inte dela upp testandet. Vi satt med diametralt olika uppkopplingar vilket naturligtvis påverkade resultatet, alla tester är därför utförda i en session och på samma dator med WiFi-uppkoppling på 115/85 Mbit/s (nät på 1000/1000 Mbit/s).

### Rangordning av webbplatserna
1. <b>Axiell</b>. Webbplatsen har en rimlig mängd resurer och bra laddtid. Den får även höga betyg i Pagespeed insights för såväl *mobile* som *desktop*.
2. <b>Arngren.net</b>. Trots en stor mängd resurser på startsidan, även om dessa är små, har webbplatsen bra laddtid när den cachats. Första laddningen är lite långsam, men cachad har den bra laddtid. Den får även höga betyg i Pagespeed insights för *desktop*, men relativt lågt för *mobile*.
3. <b>The Sun</b>. Webbplatsen har många och tunga resurser, laddtiden är långsam och även cachad (i den mån den kan bli det) är dess laddtid längre än Arngren.net ocachad. Den får även väldigt låga betyg i Pagespeed insights för såväl *mobile* som *desktop*.

Övrigt
-------------------------
Undersökningen och rapporten gjordes av mig, Kapten Skägg (roju19), i samarbete med Aztechno Dreamer (seva19).
