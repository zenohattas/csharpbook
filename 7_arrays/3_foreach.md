# Foreach loops

Wanneer je geen indexering nodig hebt, maar toch snel over alle elementen in een array wenst te gaan, dan is het **foreach** statement een zeer nuttig is.
Een foreach loop zal ieder element in de array een voor een in een tijdelijke variabele plaatsen (de **iteration variable**).
Volgende code toont de werking waarbij we een array van doubles hebben en alle elementen er in op het scherm willen tonen:

```csharp
double[] killdeathRates= {1.2, 0.89, 3.15, 0.1};
foreach (double kdrate in killdeathRates)
{
   Console.WriteLine($"Kill/Death rate is {kdrate}");
}
```

De eerste keer dat we in de loop gaan zal het element ``killdeathRates[0]`` aan ``kdrate`` toegewezen worden voor gebruik in de loop-body, vervolgens wordt ``killdeathRates[1]`` toegewezen, enz.

Het voordeel is dat je dus geen teller/index nodig hebt en dat foreach zelf de lengte van de array zal bepalen.

## Opgelet bij het gebruik van foreach loops

* De foreach iteration variable is *read-only*: je kan dus geen waarden in de array aanpassen, enkel uitlezen.
* De foreach gebruik je enkel als je alle elementen van een array wenst te benaderen. In alle andere gevallen zal je een ander soort loop (for, while, etc.) moeten gebruiken.

# var keyword

C# heeft een **``var``** keyword. Je mag dit keyword gebruiken ter vervanging van het type (bv int) op voorwaarde dat de compiler kan achterhalen wat het type moet zijn.

```csharp
var getal= 5; //var zal int zijn
var myArray= new double[20]; //var zal double[] zijn
var tekst= "Hi there handsome"; //var zal string zijn
```

**Opgelet**: het ``var`` keyword is gewoon een *lazy programmer syntax toevoeging* om te voorkomen dat je als programmer niet constant het type moet schrijven

Bij javascript heeft var een totaal andere functie: het zegt eigenlijk "het type dat je in deze variabele kan steken is...variabel", m.a.w. het kan de ene  keer een string zijn, dan een int. Bij C# gaat dit niet: eens je een variabele aanmaakt dan zal dat type onveranderbaar zijn.

> JavaScript is a dynamically typed language, while c# is (usually) a statically typed language ([stackoverflow.com](https://stackoverflow.com/questions/8457813/difference-between-the-implementation-of-var-in-javascript-and-c-sharp))

# var en foreach

Wanneer je de Visual Studio [code snippet](https://msdn.microsoft.com/en-us/library/z41h7fat.aspx) voor foreach gebruikt ``foreach [tab][tab]`` dan zal deze code ook een var gebruiken voor de iteration variabele. De compiler kan aan de te gebruiken array zien wat het type van een individueel element in de array moet zijn.
De foreach van zonet kan dus herschreven worden naar:

```csharp
foreach (var kdrate in killdeathRates)
{
   Console.WriteLine($"Kill/Death rate is {kdrate}");
}
```