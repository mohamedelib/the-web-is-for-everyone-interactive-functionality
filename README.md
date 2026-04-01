# AdConnect website
[Live website](https://mohamedelib.github.io/the-startup-responsive-interactive-website/)

## Korte uitleg van de opdracht en oplossing
Voor dit project heb ik een deel van de AdConnect website opnieuw ontworpen en uitgebreid. De opdracht was om een duidelijkere en beter werkende website te maken. Ik heb een nieuwe home pagina gemaakt, de Talent Award pagina verbeterd en een studenten pagina ontwikkeld voor genomineerde studenten.

De Talent Award pagina toont een overzicht van genomineerde studenten. Vanaf deze pagina kan de gebruiker doorklikken naar een studenten pagina.

De studenten pagina toont informatie over een specifieke student zoals naam, opleiding en instelling. De gegevens komen uit een externe database en worden dynamisch geladen.



## Responsive

De website is gebouwd met de Mobile First methode.

Op kleine schermen staat de inhoud onder elkaar.
Op grotere schermen verschijnen meerdere kolommen.

<img width="1153" height="413" alt="image" src="https://github.com/user-attachments/assets/58308f17-8a69-4fed-86e4-7e5dc78a0c3b" />
<img width="1067" height="425" alt="image" src="https://github.com/user-attachments/assets/92c61c4e-b312-4833-9cac-509c8a5b79a2" />
<img width="1135" height="431" alt="image" src="https://github.com/user-attachments/assets/06767217-62ce-4313-8e94-c2a5b4e353ca" />



## Toegankelijkheid
De website is mobile first opgebouwd. Het ontwerp start bij een one column layout en schaalt mee naarmate er meer schermruimte beschikbaar is.

Bij grotere schermen worden elementen naast elkaar geplaatst, zoals de navigatie. Van de breedte wordt steeds beter gebruik gemaakt, terwijl de inhoud overzichtelijk en leesbaar blijft. 

Deze aanpak volgt de stappen van mobile first en responsive design en zorgt voor een consistente ervaring op elk apparaat.

## Huisstijl

De website gebruikt kleuren uit de AdConnect styleguide.
Titels, witruimte en afbeeldingen zorgen voor een duidelijke structuur en focus op de studenten.

<img width="213" height="432" alt="image" src="https://github.com/user-attachments/assets/d019084a-f6d4-42f9-b864-00b9cd87f9c0" />


## Interactief

Op de Talent Award pagina staan kaarten van studenten.
Wanneer een gebruiker op een kaart klikt opent de studenten pagina van die persoon.
Dit gebeurt via een dynamische route.


## Interacties

De belangrijkste interacties zijn het sorteren van data uit de database en het
comment systeem op de nominatie pagina.

## Feed-forward

De button met de tekst "Laat je reactie achter" laat zien dat je een comment kan plaatsen.
<img width="588" height="40" alt="image" src="https://github.com/user-attachments/assets/23ee7483-fbc1-4ae3-abd0-1a1ece342097" />


## Feedback

Wanneer je een veld niet heb ingevuld, komt er een rode styling te voorschijn met 2 messages. De messages geven extra feedback aan de gebruiker 
<img width="628" height="221" alt="image" src="https://github.com/user-attachments/assets/28228f1d-78a9-4208-8507-c310ee1d3c7a" />

Wanneer je comment gelukt is krijg je gelijk feedback. 
<img width="674" height="513" alt="image" src="https://github.com/user-attachments/assets/6734f2d2-82f9-4827-b120-39ae791c927a" />

## Kenmerken

HTML zorgt voor de structuur van de pagina.
CSS regelt de layout met grid en media queries en de styleguide.
JavaScript haalt data op uit een API en toont deze op de pagina.

### HTML
<section class="nominatiebericht">
<h2 id="berichtenn">Berichten</h2>
<div class="comments-list">
    {% for comment in comments %}
      <div class="commentcard">
        <div class="row1">
          <p>{{ comment.name }}</p>
          <p>{{ comment.date_created }}</p>
        </div>
        <p>{{ comment.comment }}</p>
        <p>Nominatie #{{ comment.nomination }}</p>
      </div>
    {% endfor %}
</div>

<form class="comment-form" action="/Talentaward/student/{{ studentTitle }}/comment" method="POST">
  <label>Comment
    <textarea placeholder="Schrijf jouw reactie..." name="message">{{ form.message }}</textarea>
  </label>
  <label>Naam
    <input type="text" placeholder="Jouw naam" name="afzender" value="{{ form.afzender }}">
  </label>
  <button type="submit">Laat je reactie achter</button>
</form>

De pagina gebruikt semantische HTML.
Twee headers bevatten de navigatie en het logo.
Main bevat het studentprofiel, de video, het verhaal en de reacties.
Reacties worden opgehaald met een for-loop in Liquid en getoond in de comments-list.
Het formulier verstuurt data via method= POST naar de database.
Bij een leeg veld krijgt het element de class field-error zodat het opvalt.
Een succesbericht wordt getoond via een andere partialview als de reactie geplaatst is.



## Videofragment interactie:

https://github.com/user-attachments/assets/865db40a-854e-478b-aa00-e6bdb88a2d87


Ontwerpkeuzes
Fout- en succesmeldingen zitten in aparte partials zodat ik code niet hoef te herhalen.
Na een mislukte submit blijven ingevulde waardes staan zodat de gebruiker niet opnieuw hoeft te typen.



## GEBRUIKERSTEST

In [issue 7](https://github.com/mohamedelib/the-web-is-for-everyone-interactive-functionality/issues/7) beschrijf ik de user story voor het plaatsen van een comment bij een Talent Award kandidaat.

Wat ik testte

Ik wilde weten of gebruikers zonder problemen een reactie kunnen achterlaten bij een kandidaat. Ik focuste op het comment formulier en de feedback na het versturen.

Probleem

Het formulier staat helemaal onderaan de pagina. Gebruikers moeten eerst langs alle berichten scrollen voordat ze zelf iets kunnen typen. Dat is onhandig.

Oplossing

Ik heb de comments sectie en de form gescheiden van elkaar. Hierdoor kun je scrollen in de comment lijst en staat de form altijd onderaan.

Waarom dit werkt

De gebruiker ziet gelijk dat hij een comment kan achterlaten zonder dat hij eerst door de berichten moest scrollen.

Feedback na actie

Na het plaatsen van een reactie verschijnt er een succesbericht. De reactie is direct zichtbaar tussen de andere berichten. Dit bevestigt dat de actie is gelukt.




