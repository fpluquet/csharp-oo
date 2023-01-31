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
    string marque = "Peugeot";
    int anneeConstruction = 2022;
    float consommation = 1.8;
}
```

## Utilisation des attributs

Pour pouvoir utiliser des attributs sur des objets, il faut d'abord créer une instance de la classe. Pour créer une instance d'une classe, on utilise le mot clé `new` suivi du nom de la classe. Par exemple, pour créer une instance de la classe `Voiture`, on utilise la syntaxe suivante :

```csharp
Voiture v = new Voiture();
```

Une fois l'instance créée, on peut accéder aux attributs de l'objet en utilisant le point `.`. Par exemple, pour accéder à l'attribut `marque` de l'objet `v`, on utilise la syntaxe suivante :

```csharp
v.marque
```

On peut modifier la valeur d'un attribut en utilisant l'opérateur d'affectation `=`. Par exemple, pour modifier la valeur de l'attribut `marque` de l'objet `v`, on utilise la syntaxe suivante :

```csharp
v.marque = "Renault";
```

On peut alors afficher toutes les valeurs des attributs de l'objet `v` en utilisant la syntaxe suivante :

```csharp
Console.WriteLine(v.marque);
Console.WriteLine(v.anneeConstruction);
Console.WriteLine(v.consommation);
```




## Exercice 1

Créez une classe ```Personne``` avec les attributs ```nom```, ```age``` et ```adresse```. Initialisez les valeurs en définissant directement les valeurs par défaut. Affichez les valeurs de tous ses attributs.


<details>
	<summary>Solution</summary>

```csharp
class Personne {
    string nom = "Dupont";
    int age = 20;
    string adresse = "1 rue de la paix";
}
Personne p = new Personne();
Console.WriteLine(p.nom);
Console.WriteLine(p.age);
Console.WriteLine(p.adresse);
```

</details>

## Exercice 2

Créez plusieurs objets de la classe ```Personne``` et affichez ensuite les valeurs de chaque attribut pour chaque objet. Modifiez la valeur des attributs pour un seul objet ```Personne``` et affichez ensuite les valeurs de chaque attribut pour chaque objet.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    string nom = "Dupont";
    int age = 20;
    string adresse = "1 rue de la paix";
}
Personne p1 = new Personne();
Personne p2 = new Personne();
Personne p3 = new Personne();
Console.WriteLine(p1.nom);
Console.WriteLine(p1.age);
Console.WriteLine(p1.adresse);
Console.WriteLine(p2.nom);
Console.WriteLine(p2.age);
Console.WriteLine(p2.adresse);
Console.WriteLine(p3.nom);
Console.WriteLine(p3.age);
Console.WriteLine(p3.adresse);
p1.nom = "Dupond";
p1.age = 30;
p1.adresse = "2 rue de la paix";
Console.WriteLine(p1.nom);
Console.WriteLine(p1.age);
Console.WriteLine(p1.adresse);
Console.WriteLine(p2.nom);
Console.WriteLine(p2.age);
Console.WriteLine(p2.adresse);
Console.WriteLine(p3.nom);
Console.WriteLine(p3.age);
Console.WriteLine(p3.adresse);
```

On peut remarquer que les valeurs des attributs de l'objet ```p2``` et ```p3``` n'ont pas été modifiées.

</details>


## Exercice 3

Créez plusieurs objets de la classe ```Personne``` et modifiez leurs valeurs différentes pour chaque attribut. Affichez ensuite les valeurs de chaque attribut pour chaque objet.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    string nom = "Dupont";
    int age = 20;
    string adresse = "1 rue de la paix";
}
Personne p1 = new Personne();
Personne p2 = new Personne();
Personne p3 = new Personne();
p1.nom = "Dupond";
p1.age = 30;
p1.adresse = "2 rue de la paix";
p2.nom = "Durand";
p2.age = 40;
p2.adresse = "3 rue de la paix";
p3.nom = "Martin";
p3.age = 50;
p3.adresse = "4 rue de la paix";

Console.WriteLine(p1.nom);
Console.WriteLine(p1.age);
Console.WriteLine(p1.adresse);
Console.WriteLine(p2.nom);
Console.WriteLine(p2.age);
Console.WriteLine(p2.adresse);
Console.WriteLine(p3.nom);
Console.WriteLine(p3.age);
Console.WriteLine(p3.adresse);
```

</details>

## Exercice 4

Ajoutez à la classe un nouvel attribut ```numeroTelephone``` à la classe ```Personne``` et affectez une valeur à ce nouvel attribut pour chaque objet ```Personne```. Affichez la valeur de ce nouvel attribut pour chaque objet ```Personne```.

<details>
    <summary>Solution</summary>

```csharp
class Personne {
    string nom = "Dupont";
    int age = 20;
    string adresse = "1 rue de la paix";
    string numeroTelephone = "0123456789";
}
Personne p1 = new Personne();
Personne p2 = new Personne();
Personne p3 = new Personne();
p1.nom = "Dupond";
p1.age = 30;
p1.adresse = "2 rue de la paix";
p1.numeroTelephone = "0123456788";
p2.nom = "Durand";
p2.age = 40;
p2.adresse = "3 rue de la paix";
p2.numeroTelephone = "0123456787";
p3.nom = "Martin";
p3.age = 50;
p3.adresse = "4 rue de la paix";
p3.numeroTelephone = "0123456786";
Console.WriteLine(p1.numeroTelephone);
Console.WriteLine(p2.numeroTelephone);
Console.WriteLine(p3.numeroTelephone);
``` 

</details>

## Exercice 5

Créez une classe ```Adresse``` avec les attributs ```numeroRue```, ```nomRue``` et ```codePostal```.
Créez une classe ```Personne``` avec les attributs ```nom```, ```age``` et ```adresse``` (de type ```Adresse```). Initialisez les valeurs en utilisant le constructeur.
Créez plusieurs objets de la classe ```Personne``` avec des valeurs différentes pour chaque propriété.
Affichez ensuite les valeurs de chaque propriété pour chaque objet ```Personne```, y compris les propriétés de l'objet ```Adresse``` associé.
Modifiez la valeur d'une des propriétés de l'objet ```Adresse``` associé à un objet ```Personne``` et affichez à nouveau les détails pour cet objet ```Personne```.

<details>
    <summary>Solution</summary>

```csharp
class Adresse {
    int numeroRue;
    string nomRue;
    string codePostal;
}

class Personne {
    string nom;
    int age;
    Adresse adresse;
}

Adresse a1 = new Adresse();
a1.numeroRue = 1;
a1.nomRue = "rue de la paix";
a1.codePostal = "75000";

Personne p1 = new Personne();
p1.nom = "Dupont";
p1.age = 20;
p1.adresse = a1;

Console.WriteLine(p1.nom);
Console.WriteLine(p1.age);
Console.WriteLine(p1.adresse.numeroRue);
Console.WriteLine(p1.adresse.nomRue);
Console.WriteLine(p1.adresse.codePostal);

a1.numeroRue = 2;

Console.WriteLine(p1.nom);
Console.WriteLine(p1.age);
Console.WriteLine(p1.adresse.numeroRue);
Console.WriteLine(p1.adresse.nomRue);
Console.WriteLine(p1.adresse.codePostal);
```

</details>

## Exercice 6

Créez une classe ```Client``` avec les attributs ```nom```, ```prenom``` et ```adresse``` (de type ```Adresse```). Créez une classe ```CompteBancaire``` avec les attributs ```numeroCompte```, ```solde``` et ```client``` (de type ```Client```). Créez un ```Client``` et plusieurs ```CompteBancaire``` associé à ce client.  Affichez les détails de chaque compte bancaire, y compris le numéro de rue de l'adresse du client du compte.

<details>
    <summary>Solution</summary>

```csharp
class Adresse {
    int numeroRue;
    string nomRue;
    string codePostal;
}

class Client {
    string nom;
    string prenom;
    Adresse adresse;
}

class CompteBancaire {
    string numeroCompte;
    double solde;
    Client client;
}

Adresse a1 = new Adresse();
a1.numeroRue = 1;
a1.nomRue = "rue de la paix";
a1.codePostal = "75000";

Client c1 = new Client();
c1.nom = "Dupont";
c1.prenom = "Jean";
c1.adresse = a1;

CompteBancaire cb1 = new CompteBancaire();
cb1.numeroCompte = "123456789";
cb1.solde = 1000;
cb1.client = c1;

CompteBancaire cb2 = new CompteBancaire();
cb2.numeroCompte = "987654321";
cb2.solde = 2000;
cb2.client = c1;

Console.WriteLine(cb1.numeroCompte);
Console.WriteLine(cb1.solde);
Console.WriteLine(cb1.client.nom);
Console.WriteLine(cb1.client.prenom);
Console.WriteLine(cb1.client.adresse.numeroRue);
Console.WriteLine(cb1.client.adresse.nomRue);
Console.WriteLine(cb1.client.adresse.codePostal);

Console.WriteLine(cb2.numeroCompte);
Console.WriteLine(cb2.solde);
Console.WriteLine(cb2.client.nom);
Console.WriteLine(cb2.client.prenom);
Console.WriteLine(cb2.client.adresse.numeroRue);
Console.WriteLine(cb2.client.adresse.nomRue);
Console.WriteLine(cb2.client.adresse.codePostal);
```

</details>