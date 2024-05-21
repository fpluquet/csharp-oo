# Les itérateurs en C#

## Exercice 1 : Compréhension de l'IEnumerator

### Question 1.1
Expliquez ce que fait le code suivant et décrivez son résultat attendu :

```csharp
using System;
using System.Collections;

public class NombreCollection : IEnumerable
{
    private int[] nombres = {1, 2, 3, 4, 5};

    public IEnumerator GetEnumerator()
    {
        for (int i = 0; i < nombres.Length; i++)
        {
            yield return nombres[i] * nombres[i];
        }
    }
}

public class Programme
{
    public static void Main()
    {
        NombreCollection collection = new NombreCollection();

        foreach (int nombre in collection)
        {
            Console.WriteLine(nombre);
        }
    }
}
```

<details>
<summary>Solution</summary>
Ce code définit une collection de nombres (`NombreCollection`) qui implémente `IEnumerable`, permettant l'itération sur un tableau d'entiers. La méthode `GetEnumerator` utilise `yield return` pour retourner le carré de chaque élément du tableau. Dans la méthode `Main`, un objet de `NombreCollection` est créé et itéré avec une boucle `foreach`, imprimant le carré de chaque nombre sur la console. Le résultat attendu est :
```
1
4
9
16
25
```
</details>

### Question 1.2
Identifiez et expliquez les modifications nécessaires pour que la collection puisse être parcourue en ordre inverse.

<details>
<summary>Solution</summary>
Pour parcourir la collection en ordre inverse, nous devons modifier la méthode `GetEnumerator` comme suit :

```csharp
public IEnumerator GetEnumerator()
{
    for (int i = nombres.Length - 1; i >= 0; i--)
    {
        yield return nombres[i] * nombres[i];
    }
}
```
Cette modification inverse l'ordre de l'itération en commençant par la fin du tableau et en allant vers le début. Ainsi, le résultat de l'itération serait :
```
25
16
9
4
1
```
</details>

## Exercice 2 : Production de code avec IEnumerator

### Question 2.1
Créez une classe `FibonacciCollection` qui implémente `IEnumerable` pour générer les `n` premiers nombres de la série de Fibonacci (si vous ne savez pas ce qu'est la suite de Fibonacci, merci de lire https://fr.wikipedia.org/wiki/Suite_de_Fibonacci). Implémentez le constructeur pour recevoir le nombre d'éléments souhaités.

Le programme principal devra être le suivant :

```csharp
public class Programme
{
    public static void Main()
    {
        FibonacciCollection fibonacci = new FibonacciCollection(10);

        foreach (int number in fibonacci)
        {
            Console.WriteLine(number);
        }
    }
}
```

Il devra produire la sortie suivante :
    
```
0
1
1
2
3
5
8
13
21
34
```

<details>
<summary>Solution</summary>

```csharp
using System;
using System.Collections;

public class FibonacciCollection : IEnumerable
{
    private int _count;

    public FibonacciCollection(int count)
    {
        _count = count;
    }

    public IEnumerator GetEnumerator()
    {
        int prev = -1, next = 1, sum;
        for (int i = 0; i < _count; i++)
        {
            sum = prev + next;
            prev = next;
            next = sum;
            yield return sum;
        }
    }
}

public class Programme
{
    public static void Main()
    {
        FibonacciCollection fibonacci = new FibonacciCollection(10);

        foreach (int number in fibonacci)
        {
            Console.WriteLine(number);
        }
    }
}
```
Cette implémentation génère les `n` premiers nombres de la série de Fibonacci et les imprime sur la console.
</details>

## Exercice 3 : Compréhension et utilisation de l'indexeur (this[])

### Question 3.1
Expliquez ce que fait le code suivant et décrivez son résultat attendu :

```csharp
using System;

public class Semaine
{
    private string[] jours = {"Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche"};

    public string this[int index]
    {
        get { return jours[index]; }
        set { jours[index] = value; }
    }
}

public class Programme
{
    public static void Main()
    {
        Semaine semaine = new Semaine();
        Console.WriteLine(semaine[0]);
        semaine[0] = "Lundi Modifié";
        Console.WriteLine(semaine[0]);
    }
}
```

<details>
<summary>Solution</summary>
Ce code définit une classe `Semaine` qui utilise un tableau de chaînes pour stocker les jours de la semaine. L'indexeur `this[int index]` permet d'accéder et de modifier les éléments du tableau via l'index. Dans la méthode `Main`, un objet de `Semaine` est créé et le premier jour ("Lundi") est affiché, puis modifié en "Lundi Modifié" et affiché à nouveau. Le résultat attendu est :
```
Lundi
Lundi Modifié
```
</details>

### Question 3.2
Ajoutez une méthode à la classe `Semaine` pour retourner les jours de la semaine qui contienne le `string` passé en paramètre, en utilisant un itérateur (via le `yield`).

Le programme principal devra être le suivant :

```csharp
public class Programme
{
    public static void Main()
    {
        Semaine semaine = new Semaine();
        foreach (var jour in semaine.GetJoursAvec("di"))
        {
            Console.WriteLine(jour); 
        }
    }
}
```

Il devra produire la sortie suivante :

```
Lundi
Mardi
Mercredi
Jeudi
Vendredi
Samedi
```

<details>
<summary>Solution</summary>

```csharp
using System;
using System.Collections;

public class Semaine
{
    private string[] jours = {"Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche"};

    public string this[int index]
    {
        get { return jours[index]; }
        set { jours[index] = value; }
    }

    public IEnumerable GetJoursAvec(string texte)
    {
        foreach (var jour in jours)
        {
            if (jour.Contains(texte))
            {
                yield return jour;
            }
        }
    }
}

public class Programme
{
    public static void Main()
    {
        Semaine semaine = new Semaine();
        foreach (var jour in semaine.GetJoursAvec("di"))
        {
            Console.WriteLine(jour); 
        }
    }
}
```
Cette méthode `GetJoursAvec` utilise `yield return` pour retourner les jour de la semaine qui contiennent le texte passé en paramètre. 

</details>

## Exercice 4 : Production de code avec un indexeur

### Question 4.1
Créez une classe `Livre` qui permet d'accéder et de modifier les chapitres d'un livre en utilisant un indexeur. La classe doit également implémenter `IEnumerable` pour permettre l'itération sur les chapitres.


Le programme principal devra être le suivant :

```csharp
public class Programme
{
    public static void Main()
    {
        Livre livre = new Livre();
        livre[0] = "Chapitre 1: Introduction";
        livre[1] = "Chapitre 2: Le commencement";
        livre[2] = "Chapitre 3: L'aventure";

        foreach (var chapitre in livre)
        {
            Console.WriteLine(chapitre);
        }
    }
}
```

Il devra produire la sortie suivante :

```
Chapitre 1: Introduction
Chapitre 2: Le commencement
Chapitre 3: L'aventure
```

<details>
<summary>Solution</summary>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

public class Livre : IEnumerable
{
    private List<string> chapitres = new List<string>();

    public string this[int index]
    {
        get { return chapitres[index]; }
        set 
        { 
            if (index >= 0 && index < chapitres.Count)
                chapitres[index] = value; 
            else if (index == chapitres.Count)
                chapitres.Add(value);
        }
    }

    public IEnumerator GetEnumerator()
    {
        foreach (var chapitre in chapitres)
        {
            yield return chapitre;
        }
    }
}

public class Programme
{
    public static void Main()
    {
        Livre livre = new Livre();
        livre[0] = "Chapitre 1: Introduction";
        livre[1] = "Chapitre 2: Le commencement";
        livre[2] = "Chapitre 3: L'aventure";

        foreach (var chapitre in livre)
        {
            Console.WriteLine(chapitre);
        }
    }
}
```
Cette classe `Livre` utilise une liste de chaînes pour stocker les chapitres et permet l'accès et la modification via un indexeur. Elle implémente également `IEnumerable` pour permettre l'itération sur les chapitres. Dans la méthode `Main`, trois chapitres sont ajoutés et ensuite affichés.
</details>