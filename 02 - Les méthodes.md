# Les méthodes

## Exercice 1

Soit le code suivant :

```csharp
class Calculette
{
    double Resultat = 0;
}

class Program
{
    public static void Main()
    {
        Calculette calculette1 = new Calculette(); // Calculette initialisée à 0
        Calculette calculette2 = new Calculette(15); // Calculette initialisée à 15

        calculette1.Ajouter(5);
        calculette1.Afficher(); // doit afficher 5
        calculette1.Multiplier(2); 
        calculette1.Afficher(); // doit afficher 10
        calculette1.RemiseAZero();
        calculette1.Afficher(); // doit afficher 0

        calculette2.Afficher(); // doit afficher 15
        calculette2.Executer(multiplierPar: 3);
        calculette2.Afficher(); // doit afficher 45
        calculette2.Executer(soustraire: 7);
        calculette2.Afficher(); // doit afficher 38
        calculette2.Executer(ajouter: 9);
        calculette2.Afficher(); // doit afficher 47
    }
}
```

Ajoutez les méthodes dans la classe ```Calculette``` pour que le code ci-dessus fonctionne sans changer le Main.

<details>
<summary>Solution</summary>

```csharp
class Calculette
{
    private double Resultat = 0;

    //public Calculette() : this(0)
    //{
    //}

    //public Calculette(double r)
    //{
    //    this.Resultat = r;
    //}

    // les deux constructeurs sont équivalents à :

    public Calculette(double r = 0)
    {
        this.Resultat = r;
    }

    public void Ajouter(double terme)
    {
        this.Resultat += terme;
    }

    public void Afficher()
    {
        Console.WriteLine(this.Resultat);
    }

    public void Multiplier(double facteur)
    {
        this.Resultat *= facteur;
    }

    public void Soustraire(double terme)
    {
        this.Resultat -= terme;
    }

    public void RemiseAZero()
    {
        this.Resultat = 0;
    }

    public void Executer(double multiplierPar = 1, double ajouter = 0, double soustraire = 0)
    {
        this.Multiplier(multiplierPar);
        this.Ajouter(ajouter);
        this.Soustraire(soustraire);
    }
}

class Program
{
    public static void Main()
    {
        Calculette calculette1 = new Calculette(); // Calculette initialisée à 0
        Calculette calculette2 = new Calculette(15); // Calculette initialisée à 15

        calculette1.Ajouter(5);
        calculette1.Afficher(); // doit afficher 5
        calculette1.Multiplier(2);
        calculette1.Afficher(); // doit afficher 10
        calculette1.RemiseAZero();
        calculette1.Afficher(); // doit afficher 0


        calculette2.Afficher(); // doit afficher 15
        calculette2.Executer(multiplierPar: 3);
        calculette2.Afficher(); // doit afficher 45
        calculette2.Executer(soustraire: 7);
        calculette2.Afficher(); // doit afficher 38
        calculette2.Executer(ajouter: 9);
        calculette2.Afficher(); // doit afficher 47
        calculette2.Executer(soustraire: 2, multiplierPar: 2);
        calculette2.Afficher(); // doit afficher 92
        calculette2.RemiseAZero();

        calculette2.Executer();
        calculette2.Afficher(); // doit afficher 0
    }
}
```
</details>