# Unity API calls

Met het gebruik van Unity API calls moet je altijd goed opletten. Je weet van tevoren vaak niet wat er achter de schermen gebeurd. 
Iets wat lijkt een makkelijke functie aanroep te zijn in Unity kan achter de schermen voor behoorlijk wat framerate loss of garbage allocation 
zorgen. Om een complete lijst met API calls te geven die achter de schermen te druk zijn om te gebruiken in een update loop is bijna niet te doen. 
Development van Unity staat ook niet stil dus deze lijst van functies zal constant veranderen. Met behulp van Unity profiling zou je er snel achter 
moeten komen waar je teveel gebruik maakt van zware API calls. Door het op een slimme manier omschrijven van je code kan veel van de zware code 
weg gewerkt worden zodat het geen framerate meer hoeft te kosten.

#### Array returning API calls
Door het gebruik van Array returning API calls kan snel veel framerate verloren gaan. Het is aan te raden deze functies niet in een 'update loop' te gebruiken 
of naar alternatieven te zoeken.  
Hieronder een paar voorbeelden van werkwijzen die toegepast kunnen worden:

