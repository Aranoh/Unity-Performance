# Unity API calls

Met het gebruik van Unity API calls moet je altijd goed opletten. Je weet van tevoren vaak niet wat er achter de schermen gebeurd. 
Iets wat lijkt een makkelijke functie aanroep te zijn in Unity kan achter de schermen voor behoorlijk wat framerate loss of garbage allocation 
zorgen. Om een complete lijst met API calls te geven die achter de schermen te druk zijn om te gebruiken in een update loop is bijna niet te doen. 
Development van Unity staat ook niet stil dus deze lijst van functies zal constant veranderen. Met behulp van Unity profiling zou je er snel achter 
moeten komen waar je teveel gebruik maakt van zware API calls. Door het op een slimme manier omschrijven van je code kan veel van de zware code 
weg gewerkt worden zodat het geen framerate meer hoeft te kosten.

### Array returning API calls
Door het gebruik API calls die Arrays teruggeven kan snel veel framerate verloren gaan, vooral als dit in een 'update loop' gebeurd. 
Het is aan te raden deze functies niet in een 'update loop' te gebruiken of naar alternatieven te zoeken.  

Hieronder een paar voorbeelden van werkwijzen die toegepast kunnen worden:

#### Zoeken alternatieven  
```C#
void Update() {
        int fingerCount = 0;
        foreach (Touch touch in Input.touches) {
            if (touch.phase != TouchPhase.Ended && touch.phase != TouchPhase.Canceled)
                fingerCount++;
            
        }
        if (fingerCount > 0)
            print("User has " + fingerCount + " finger(s) touching the screen");
        
    }
```  
[Unity Docs](https://docs.unity3d.com/ScriptReference/Input-touches.html)
