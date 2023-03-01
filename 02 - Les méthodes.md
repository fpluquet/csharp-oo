# Les méthodes

## Exercice 1

Soit le code suivant :

```csharp
class Calculette
{
    double resultat = 0;
}

class Program
{
    public static void Main()
    {
        Calculette calculette1 = new Calculette(); // Calculette initialisée à 0
        Calculette calculette2 = new Calculette(15); // Calculette initialisée à 15

        calculette1.ajouter(5);
        calculette1.afficher(); // doit afficher 5
        calculette1.multiplier(2); 
        calculette1.afficher(); // doit afficher 10
        calculette1.remiseAZero();
        calculette1.afficher(); // doit afficher 0

        calculette2.afficher(); // doit afficher 15
        calculette2.execute(multiplierPar: 3);
        calculette2.afficher(); // doit afficher 45
        calculette2.execute(soustraire: 7);
        calculette2.afficher(); // doit afficher 38
        calculette2.execute(ajouter: 9);
        calculette2.afficher(); // doit afficher 46
    }
}
```

Ajoutez les méthodes dans la classe ```Calculette``` pour que le code ci-dessus fonctionne sans changer le Main.