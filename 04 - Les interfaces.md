# Les interfaces en C#

## Exercice 1

Créez une interface `IAnimal` avec les méthodes suivantes :
- `void Manger()`
- `void Dormir()`

Créez deux classes `Chien` et `Chat` qui implémentent l'interface `IAnimal`, en affichant un message pour chaque méthode (par exemple "Le chien mange" pour ```Chien>>#Manger()```).

Créez une classe `Program` avec une méthode `Main` qui crée une instance de `Chien` et une instance de `Chat` et qui appelle les méthodes `Manger` et `Dormir` pour chaque instance.

Mettez ces deux instances dans un tableau d'`IAnimal` et appelez les méthodes `Manger` et `Dormir` pour chaque élément de la tableau.

<details>
<summary>Solution</summary>

```csharp
using System;

interface IAnimal
{
    void Manger();
    void Dormir();
}

class Chien : IAnimal
{
    public void Manger()
    {
        Console.WriteLine("Le chien mange.");
    }

    public void Dormir()
    {
        Console.WriteLine("Le chien dort.");
    }
}

class Chat : IAnimal
{
    public void Manger()
    {
        Console.WriteLine("Le chat mange.");
    }

    public void Dormir()
    {
        Console.WriteLine("Le chat dort.");
    }
}

class Program
{
    public static void Main()
    {
        Chien chien = new Chien();
        chien.Manger();
        chien.Dormir();

        Chat chat = new Chat();
        chat.Manger();
        chat.Dormir();

        IAnimal[] animaux = new IAnimal[] { chien, chat };
        foreach (IAnimal animal in animaux)
        {
            animal.Manger();
            animal.Dormir();
        }        
    }
}
```

</details>

## Exercice 2

Créez une interface `IForme` avec une méthode `double CalculerAire()`.

Créez deux classes `Rectangle` et `Cercle`.

Ajoutez la propriété `double Largeur` et `double Hauteur` à la classe `Rectangle` et la propriété `double Rayon` à la classe `Cercle`.

Créez des constructeurs pour les classes `Rectangle` et `Cercle` qui initialisent les propriétés.

Implémentez la méthode `CalculerAire` pour chaque classe. Pour le rectangle, l'aire est égale à `Largeur * Hauteur` et pour le cercle, l'aire est égale à `Math.PI * Rayon * Rayon`.

Créez une classe `Program` avec une méthode `Main` qui crée une instance de `Rectangle` et une instance de `Cercle` et qui appelle la méthode `CalculerAire` pour chaque instance.

Ajoutez une méthode `CalculerAire` à la classe `Program` qui prend en paramètre une instance de `IForme` et qui affiche l'aire de la forme. Utilisez cette méthode pour afficher l'aire du rectangle et du cercle.

Ajoutez une méthode `GetNbCôtés` à la classe `Rectangle` qui retourne le nombre de côtés du rectangle (4) et une méthode `GetNbCôtés` à la classe `Cercle` qui retourne le nombre de côtés du cercle (0). Appelez ces méthodes dans la méthode `Main`. 


<details>
<summary>Solution</summary>

Voici le code à obtenir :

```csharp
interface IForme
{
    double CalculerAire();
}

class Rectangle : IForme
{
    public double Largeur { get; set; }
    public double Hauteur { get; set; }

    public Rectangle(double largeur, double hauteur)
    {
        Largeur = largeur;
        Hauteur = hauteur;
    }

    public override double CalculerAire()
    {
        return Largeur * Hauteur;
    }

    public int GetNbCôtés()
    {
        return 4;
    }
}

class Cercle : IForme
{
    public double Rayon { get; set; }

    public Cercle(double rayon)
    {
        Rayon = rayon;
    }

    public override double CalculerAire()
    {
        return Math.PI * Rayon * Rayon;
    }

    public int GetNbCôtés()
    {
        return 0;
    }
}

class Program
{
    public static void Main()
    {
        Rectangle rectangle = new Rectangle(2, 3);
        Cercle cercle = new Cercle(4);

        Console.WriteLine($"Aire du rectangle : {rectangle.CalculerAire()}");
        Console.WriteLine($"Aire du cercle : {cercle.CalculerAire()}");

        CalculerAire(rectangle);
        CalculerAire(cercle);
    }

    public static void CalculerAire(IForme forme)
    {
        Console.WriteLine($"Aire : {forme.CalculerAire()}");
    }
}
```

</details>

## Exercice 3

Si on part de la solution de l'exercice 2, quelles sont les lignes suivantes qui seront correctes lors de la compilation ? Pour celles qui ne le sont pas, expliquez pourquoi.

```csharp
IForme forme1 = new Rectangle(2,3);
IForme forme2 = new Cercle(4,5);
Rectangle rectangle = new Rectangle(6,7);
Cercle cercle = new Cercle(1,2);

forme1.CalculerAire();
forme2.CalculerAire();
forme1.GetNbCôtés();
forme2.GetNbCôtés();

rectangle.CalculerAire();
cercle.CalculerAire();
rectangle.GetNbCôtés();
cercle.GetNbCôtés();

List<IForme> formes = new List<IForme>();

formes.Add(rectangle);
formes.Add(cercle);

foreach (IForme forme in formes)
{
    forme.CalculerAire();
    forme.GetNbCôtés();
}
```

<details>
<summary>Solution</summary>

Voici les commentaires sur chaque ligne :
    
```csharp
IForme forme1 = new Rectangle(); // Correct
IForme forme2 = new Cercle(); // Correct
Rectangle rectangle = new Rectangle(); // Correct
Cercle cercle = new Cercle(); // Correct

forme1.CalculerAire(); // Correct
forme2.CalculerAire(); // Correct
forme1.GetNbCôtés(); // Incorrect : la méthode GetNbCôtés n'est pas définie dans l'interface IForme
forme2.GetNbCôtés(); // Incorrect : la méthode GetNbCôtés n'est pas définie dans l'interface IForme

rectangle.CalculerAire(); // Correct
cercle.CalculerAire(); // Correct

rectangle.GetNbCôtés(); // Correct
cercle.GetNbCôtés(); // Correct

List<IForme> formes = new List<IForme>();

formes.Add(rectangle); // Correct
formes.Add(cercle); // Correct

foreach (IForme forme in formes)
{
    forme.CalculerAire(); // Correct
    forme.GetNbCôtés(); // Incorrect : la méthode GetNbCôtés n'est pas définie dans l'interface IForme
}
```

</details>



## Exercice 4

Implémentez l'interface `IComparable` pour les classes `Rectangle` et `Cercle` de l'exercice 2. L'ordre de tri doit être basé sur l'aire de la forme. Créez une liste de rectangles et triez-la. Créez une liste de cercles et triez-la. Créez une liste de formes et triez-la. Affichez à chaque fois l'aire des formes triées.

<details>
<summary>Solution</summary>

Voici le code à obtenir :

```csharp
interface IForme : IComparable<IForme>
{
    double CalculerAire();
}

class Rectangle : IForme, IComparable<Rectangle>, IComparable<IForme>
{
    public double Largeur { get; set; }
    public double Longueur { get; set; }

    public Rectangle(double largeur, double longueur)
    {
        Largeur = largeur;
        Longueur = longueur;
    }

    public double CalculerAire()
    {
        return Largeur * Longueur;
    }

    public int GetNbCôtés()
    {
        return 4;
    }

    public int CompareTo(Rectangle? other) // permet de comparer des rectangles entre eux
    {
        if (other == null) return 1; // on considère que si other est null, this est 'plus grand'
        Console.WriteLine("Dans le Rectangle>>CompareTo(Rectangle)");
        return CalculerAire().CompareTo(other.CalculerAire());
        // on pourrait aussi l'écrire comme ça
        // int monAire = this.CalculerAire();
        // int autreAire = other.CalculerAire();
        // if(monAire < autreAire) 
        //    return -1
        // if(monAire == autreAire)
        //    return 0
        // // ici on sait forcément que monAire > autreAire
        // return 1
    }
    public int CompareTo(IForme? other) // permet de comparer des formes entre elles
    {
        if (other == null) return 1; // on considère que si other est null, this est 'plus grand'
        Console.WriteLine("Dans le Rectangle>>CompareTo(IForme)");
        return CalculerAire().CompareTo(other.CalculerAire());
    }
}

    class Cercle : IForme, IComparable<Cercle>, IComparable<IForme>
{
    public double Rayon { get; set; }

    public Cercle(double rayon)
    {
        Rayon = rayon;
    }

    public double CalculerAire()
    {
        return Math.PI * Rayon * Rayon;
    }

    public int GetNbCôtés()
    {
        return 0;
    }

    public int CompareTo(Cercle? other) // permet de comparer des cercles entre eux
    {
        if (other == null) return 1; // on considère que si other est null, this est 'plus grand'
        Console.WriteLine("Dans le Cercle>>CompareTo(Cercle)");
        return CalculerAire().CompareTo(other.CalculerAire());
    }

    public int CompareTo(IForme? other) // permet de comparer des formes entre elles
    {
        if (other == null) return 1; // on considère que si other est null, this est 'plus grand'
        Console.WriteLine("Dans le Cercle>>CompareTo(IForme)");
        return CalculerAire().CompareTo(other.CalculerAire());
    }
}

class Program
{
    public static void Main()
    {
        Rectangle rectangle1 = new Rectangle(2, 3);
        Rectangle rectangle2 = new Rectangle(8, 9);
        Cercle cercle1 = new Cercle(5);
        Cercle cercle2 = new Cercle(2);

        List<Rectangle> rectangles = new List<Rectangle> { rectangle1, rectangle2 };
        rectangles.Sort();
        foreach (Rectangle rectangle in rectangles)
        {
            Console.WriteLine(rectangle.CalculerAire());
        }

        List<Cercle> cercles = new List<Cercle> { cercle1, cercle2 };
        cercles.Sort();

        foreach (Cercle cercle in cercles)
        {
            Console.WriteLine(cercle.CalculerAire());
        }

        List<IForme> formes = new List<IForme> { rectangle1, rectangle2, cercle1, cercle2 };
        formes.Sort();

        foreach (IForme forme in formes)
        {
            Console.WriteLine(forme.CalculerAire());
        }
    }
}
```

</details>
