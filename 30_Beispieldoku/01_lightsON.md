Angabe: P:\\\\ento

![[index.html]]

In HTML-Tags werden Java-Script-Funktionen  oft mit sogennanten Ereignishandlern aufegrufen. Hier z.B. OnClick
Events: siehe=[JavaScript Events Examples (w3schools.com)](https://www.w3schools.com/js/js_events_examples.asp)


```js
  <center><a href="#" onclick="myClick(1,1)">
```


Hier wird bei Klick auf das jeweilige Element (image bzw. eigentlich auf den Link) die Funktion myClick aufgerufen. Diese erhält 2 Parameter: spalte,zeile



Einstellungen
Globale Variablen

```js
var maxZeile = 5;

var maxSpalte = 5;

  

//hier gilt js Syntax

function myClick(spalte,zeile) {

   //alert ("myClick");

   console.log(spalte+" "+ zeile);

   //Welches bild?

   toggleImage(zeile, spalte)

   //Bild oben

   var oben = zeile -1;

   var unten = zeile +1;

   var links = spalte -1;

   var rechts = spalte +1;

   //if (oben>0)

      toggleImage(oben, spalte);

   //if (unten<6) 

      toggleImage(unten, spalte);

   //if (links>0) 

      toggleImage(zeile, links);

   //if (rechts<6) 

      toggleImage(zeile, rechts);

  

}
```



Um den Code für das Ändern des Bildes nicht 5 mal redundant zu haben, wird dieser in der Funktion toggleImage eingefügt. 
  

```js
function toggleImage(zeile, spalte) {

   //Am beginn brechen wir die Funktion mit return false ab, falls

   //ein Parameter nicht im gültigen Bereich ist

   if (zeile<1 || spalte <1 || zeile>maxzeile || spalte>maxSpalte) return flase;

   var bildid = "bild"+ spalte+ zeile;

   //Bild ist ein Objekt (HTML benutzt DOM - Document Object Model)

   var bild = document.getElementById(bildid);

   //console.log(bild);

   if (bild.src.indexOf('off.gif') >= 0) {

      //off.gif gefunden

      bild.src = "images/on.gif";

   } else {

      bild.src = "images/off.gif";

  

   }

}

  
  

</script>

  

</body></html>
```


 Um die Schritte mitzuzählen und Seitenbereich damit befüllen fügen wir am Ende unserer Funktion myClick folgenden Code ein. 

```js
   schritte++;

   counter.innerHTML = schritte;
```



Nur noch der Reset Button

```js
function reset() {

   schritte = 0;

   counter.innerHTML = schritte;

   for (var zeile = 1;zeile<=maxzeile; zeile++) {

      for (var splate = 1;spalte<=maxspalte; spalte++) {

         var bildid = "bild"+spalte+zeile;

         var bild = document.getElementById(bildid);

         bild.src = "images/off.gif";

   }

   }

}
```

