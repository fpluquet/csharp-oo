# Les attributs

Les attributs sont les propriétés des objets. Les attributs en C# ont une syntaxe particulière. Ils sont définis par un type, nom et une valeur. Les attributs sont définis dans la classe et sont accessibles par les instances de la classe. Chaque instance d'une classe possède ses propres valeurs d'attributs. 

Le type d'un attribut est défini par un type primitif (int, float,  ...) ou un type défini par l'utilisateur (une autre classe). Le nom d'un attribut est défini par une chaîne de caractères. La valeur d'un attribut est défini par une expression.

## Définition d'une classe avec des attributs

La syntaxe pour définir une classe avec des attributs est la suivante :

```csharp
class <nom de la classe> {
    [<type> <nom> = <valeur par défaut>;] 
    [<type> <nom> = <valeur par défaut>;] 
    [<type> <nom> = <valeur par défaut>;] 
    [<type> <nom> = <valeur par défaut>;] 
    ...
}
```

Par exemple, la classe suivante définit une classe `Voiture` avec 3 attributs :

```csharp
class Voiture {
    string Marque = "Peugeot";
    int AnneeConstruction = 2022;
    float Consommation = 1.8;
}
```

## Utilisation des attributs

Pour pouvoir utiliser des attributs sur des objets, il faut d'abord créer une instance de la classe. Pour créer une instance d'une classe, on utilise le mot clé `new` suivi du nom de la classe. Par exemple, pour créer une instance de la classe `Voiture`, on utilise la syntaxe suivante :

```csharp
Voiture v = new Voiture();
```

Une fois l'instance créée, on peut accéder aux attributs de l'objet en utilisant le point `.`. Par exemple, pour accéder à l'attribut `Marque` de l'objet `v`, on utilise la syntaxe suivante :

```csharp
v.Marque
```

On peut modifier la valeur d'un attribut en utilisant l'opérateur d'affectation `=`. Par exemple, pour modifier la valeur de l'attribut `Marque` de l'objet `v`, on utilise la syntaxe suivante :

```csharp
v.Marque = "Renault";
```

On peut alors afficher toutes les valeurs des attributs de l'objet `v` en utilisant la syntaxe suivante :

```csharp
Console.WriteLine(v.Marque);
Console.WriteLine(v.AnneeConstruction);
Console.WriteLine(v.Consommation);
```




## Exercice 1

Créez une classe ```Personne``` avec les attributs ```Nom```, ```Age``` et ```Adresse```. Initialisez les valeurs en définissant directement les valeurs par défaut. Affichez les valeurs de tous ses attributs.


<details>
	<summary>Solution</summary>

```csharp
class Personne {
    public string Nom = "Dupont";
    public int Age = 20;
    public string Adresse = "1 rue de la paix";
}

class Program {
    public static void Main() {
        Personne p = new Personne();
        Console.WriteLine(p.Nom);
        Console.WriteLine(p.Age);
        Console.WriteLine(p.Adresse);
    }
}
```

</details>

## Exercice 2

Créez plusieurs objets de la classe ```Personne``` et affichez ensuite les valeurs de chaque attribut pour chaque objet. Modifiez la valeur des attributs pour un seul objet ```Personne``` et affichez ensuite les valeurs de chaque attribut pour chaque objet.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    public string Nom = "Dupont";
    public int Age = 20;
    public string Adresse = "1 rue de la paix";
}

class Program {
    public static void Main() {
        Personne p1 = new Personne();
        Personne p2 = new Personne();
        Personne p3 = new Personne();
        Console.WriteLine(p1.Nom);
        Console.WriteLine(p1.Age);
        Console.WriteLine(p1.Adresse);
        Console.WriteLine(p2.Nom);
        Console.WriteLine(p2.Age);
        Console.WriteLine(p2.Adresse);
        Console.WriteLine(p3.Nom);
        Console.WriteLine(p3.Age);
        Console.WriteLine(p3.Adresse);
        p1.Nom = "Dupond";
        p1.Age = 30;
        p1.Adresse = "2 rue de la paix";
        Console.WriteLine(p1.Nom);
        Console.WriteLine(p1.Age);
        Console.WriteLine(p1.Adresse);
        Console.WriteLine(p2.Nom);
        Console.WriteLine(p2.Age);
        Console.WriteLine(p2.Adresse);
        Console.WriteLine(p3.Nom);
        Console.WriteLine(p3.Age);
        Console.WriteLine(p3.Adresse);
    }
}
```

On peut remarquer que les valeurs des attributs de l'objet ```p2``` et ```p3``` n'ont pas été modifiées.

</details>


## Exercice 3

Créez plusieurs objets de la classe ```Personne``` et modifiez leurs valeurs différentes pour chaque attribut. Affichez ensuite les valeurs de chaque attribut pour chaque objet.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    public string Nom = "Dupont";
    public int Age = 20;
    public string Adresse = "1 rue de la paix";
}

class Program {
    public static void Main() {
        Personne p1 = new Personne();
        Personne p2 = new Personne();
        Personne p3 = new Personne();
        p1.Nom = "Dupond";
        p1.Age = 30;
        p1.Adresse = "2 rue de la paix";
        p2.Nom = "Durand";
        p2.Age = 40;
        p2.Adresse = "3 rue de la paix";
        p3.Nom = "Martin";
        p3.Age = 50;
        p3.Adresse = "4 rue de la paix";

        Console.WriteLine(p1.Nom);
        Console.WriteLine(p1.Age);
        Console.WriteLine(p1.Adresse);
        Console.WriteLine(p2.Nom);
        Console.WriteLine(p2.Age);
        Console.WriteLine(p2.Adresse);
        Console.WriteLine(p3.Nom);
        Console.WriteLine(p3.Age);
        Console.WriteLine(p3.Adresse);
    }
}
```

</details>

## Exercice 4

Ajoutez à la classe un nouvel attribut ```NumeroTelephone``` à la classe ```Personne``` et affectez une valeur à ce nouvel attribut pour chaque objet ```Personne```. Affichez la valeur de ce nouvel attribut pour chaque objet ```Personne```.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    public string Nom = "Dupont";
    public int Age = 20;
    public string Adresse = "1 rue de la paix";
    public string NumeroTelephone = "0123456789";
}

class Program {
    public static void Main() {
        Personne p1 = new Personne();
        Personne p2 = new Personne();
        Personne p3 = new Personne();
        p1.Nom = "Dupond";
        p1.Age = 30;
        p1.Adresse = "2 rue de la paix";
        p1.NumeroTelephone = "0123456788";
        p2.Nom = "Durand";
        p2.Age = 40;
        p2.Adresse = "3 rue de la paix";
        p2.NumeroTelephone = "0123456787";
        p3.Nom = "Martin";
        p3.Age = 50;
        p3.Adresse = "4 rue de la paix";
        p3.NumeroTelephone = "0123456786";
        Console.WriteLine(p1.NumeroTelephone);
        Console.WriteLine(p2.NumeroTelephone);
        Console.WriteLine(p3.NumeroTelephone);
    }
}
``` 

</details>

## Exercice 5

Créez une classe ```Adresse``` avec les attributs ```NumeroRue```, ```NomRue``` et ```CodePostal```.
Créez une classe ```Personne``` avec les attributs ```Nom```, ```Age``` et ```Adresse``` (de type ```Adresse```). Initialisez les valeurs en utilisant le constructeur.
Créez plusieurs objets de la classe ```Personne``` avec des valeurs différentes pour chaque propriété.
Affichez ensuite les valeurs de chaque propriété pour chaque objet ```Personne```, y compris les propriétés de l'objet ```Adresse``` associé.
Modifiez la valeur d'une des propriétés de l'objet ```Adresse``` associé à un objet ```Personne``` et affichez à nouveau les détails pour cet objet ```Personne```.

<details>
    <summary>Solution</summary>

```csharp
class Adresse {
    public int NumeroRue;
    public string NomRue;
    public string CodePostal;
}

class Personne {
    public string Nom;
    public int Age;
    public Adresse Adresse;
}

class Program {
    static void Main() {
        Adresse a1 = new Adresse();
        a1.NumeroRue = 1;
        a1.NomRue = "rue de la paix";
        a1.CodePostal = "75000";

        Personne p1 = new Personne();
        p1.Nom = "Dupont";
        p1.Age = 20;
        p1.Adresse = a1;

        Console.WriteLine(p1.Nom);
        Console.WriteLine(p1.Age);
        Console.WriteLine(p1.Adresse.NumeroRue);
        Console.WriteLine(p1.Adresse.NomRue);
        Console.WriteLine(p1.Adresse.CodePostal);

        a1.NumeroRue = 2;

        Console.WriteLine(p1.Nom);
        Console.WriteLine(p1.Age);
        Console.WriteLine(p1.Adresse.NumeroRue);
        Console.WriteLine(p1.Adresse.NomRue);
        Console.WriteLine(p1.Adresse.CodePostal);
    }
}
```

</details>

## Exercice 6

Créez une classe ```Client``` avec les attributs ```Nom```, ```Prenom``` et ```Adresse``` (de type ```Adresse```). Créez une classe ```CompteBancaire``` avec les attributs ```NumeroCompte```, ```Solde``` et ```Client``` (de type ```Client```). Créez un ```Client``` et plusieurs ```CompteBancaire``` associés à ce client.  Affichez les détails de chaque compte bancaire, y compris le numéro de rue de l'Adresse du client du compte.

<details>
    <summary>Solution</summary>

```csharp
class Adresse {
    public int NumeroRue;
    public string NomRue;
    public string CodePostal;
}

class Client {
    public string Nom;
    public string Prenom;
    public Adresse Adresse;
}

class CompteBancaire {
    public string NumeroCompte;
    public double Solde;
    public Client Client;
}

class Program {
    public static void Main() {
        Adresse a1 = new Adresse();
        a1.NumeroRue = 1;
        a1.NomRue = "rue de la paix";
        a1.CodePostal = "75000";

        Client c1 = new Client();
        c1.Nom = "Dupont";
        c1.Prenom = "Jean";
        c1.Adresse = a1;

        CompteBancaire cb1 = new CompteBancaire();
        cb1.NumeroCompte = "123456789";
        cb1.Solde = 1000;
        cb1.Client = c1;

        CompteBancaire cb2 = new CompteBancaire();
        cb2.NumeroCompte = "987654321";
        cb2.Solde = 2000;
        cb2.Client = c1;

        Console.WriteLine(cb1.NumeroCompte);
        Console.WriteLine(cb1.Solde);
        Console.WriteLine(cb1.Client.Nom);
        Console.WriteLine(cb1.Client.Prenom);
        Console.WriteLine(cb1.Client.Adresse.NumeroRue);
        Console.WriteLine(cb1.Client.Adresse.NomRue);
        Console.WriteLine(cb1.Client.Adresse.CodePostal);

        Console.WriteLine(cb2.NumeroCompte);
        Console.WriteLine(cb2.Solde);
        Console.WriteLine(cb2.Client.Nom);
        Console.WriteLine(cb2.Client.Prenom);
        Console.WriteLine(cb2.Client.Adresse.NumeroRue);
        Console.WriteLine(cb2.Client.Adresse.NomRue);
        Console.WriteLine(cb2.Client.Adresse.CodePostal);
    }
}
```

</details>
