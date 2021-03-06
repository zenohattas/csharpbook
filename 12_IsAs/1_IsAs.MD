# Is en As

We introduceren twee nieuwe C# keywords: ``is`` en ``as``. 

## Is keyword
Het ``is`` keyword is een operator die je kan gebruiken om te weten te komen of:
* Een object van een bepaalde type is
* Een object een bepaalde interface bevat

``is`` geeft een bool terug.

### Is voorbeeld 1
Stel dat we volgende drie klassen hebben:
```csharp
class Vehicle {}

class Car: Vehicle{}

class Person {}
```
Een Car **is** een Vehikel.
Een Person **is geen** Vehikel.

Stel dat we enkele variabelen hebben als volgt:
```csharp
Car myCar= new Car();
Person rambo= new Person();
```

We kunnen nu de objecten met ``is`` bevragen of ze van een bepaalde type zijn:
```csharp
if(myCar is Vehicle)
{
    Console.WriteLine("The first object is a Vehicle");
}
if(rambo is Vehicle)
{
    Console.WriteLine("The second object is a Vehicle");
}
```

De uitvoer zal worden:``The first object is a Vehicle``.

### Is voorbeeld 2
Ook kunnen we dus ``is`gebruiken om te weten of een klasse een specifieke interface heeft.
Stel:
```csharp
interface IDeletable{ ...};

class Book: IDeletable { ... };

class Person { ... };
```

In actie:
```csharp
Person tim= new Person();
Book gameofthrones = new Book();

if(gameofthrones is IDeletable)
{
    Console.WriteLine("I can delete game of thrones");
}
if(tim is IDeletable)
{
    Console.WriteLine("I can delete tim");
}
```

Ouput: ``I can delete game of thrones``.

## As keyword met voorbeeld
Wanneer we objecten van het ene naar het andere type willen omzetten dan doen we dit vaak met behulp van [casting](/1_csharpbasics/4_converteren_casting.md):
```csharp
Student fritz= new Student();
Mens jos = (Mens)fritz;
```

 Het probleem bij casting is dat dit niet altijd lukt. Indien de conversie niet mogelijk is zal een Exception gegenereerd worden en je programma zal  crashen als  je niet aan [Exception handling doet](https://codevan1001nacht.wordpress.com/2013/11/06/exception-handling/).

 Het ``as`` keyword lost dit op. Het keyword zegt aan de compiler 'probeer dit object te converteren.Als het niet lukt, zet het dan op ``null`` in plaats van een Exception te werpen.
 
 De code van daarnet herschrijven we dan naar:

 ```csharp
Student fritz= new Student();
Mens jos =fritz as Mens;
```
Indien nu de casting niet lukt (omdat ´´Student´´ misschien geen childklasse van ´´Mens´´ blijkt te zijn) dan zal ``jos`` de waarde ``null`` hebben gekregen.

We kunnen dan vervolgens bijvoorbeeld schrijven:
 ```csharp
Student fritz= new Student();
Mens jos =fritz as Mens;
if(jos!=null)
{
    //Doe Mens-zaken   
}
```

# Why should I care?
![](/assets/care.jpg)

De ``is`` en ``as`` keywords laten toe om meer dynamische code te schrijven. Mogelijk weet je niet op voorhand wat voor datatype je code zal moeten verwerken en wordt polymorfisme je oplossing. Maar dan? Dan komen ``is`` en ``as`` to the rescue!

Je , dank zij polymorfisme, gevuld lijst van objecten van allerhande typen wordt nu beheersbaarder. Je kan nu , met ``is`` een element bevragen of hij van een bepaald type is. Vervolgens kan je met ``as`` het element even 'omzetten' naar z'n effectieve type (en dus meer doen dan wat hij kan in de vermomming van z'n eigen basistype).

