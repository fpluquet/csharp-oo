# Le polymorpshime

## Exercice 1

Soit le code suivant :

```csharp
using System;
using System.Collections.Generic;

public abstract class Personnage
{
    public string Nom { get; set; }
    public int PointsDeVie { get; set; }

    public Personnage(string nom)
    {
        Nom = nom;
        PointsDeVie = 50;
    }

    public abstract void Attaquer(Personnage cible);

    public virtual bool PeutSeProtéger(Personnage attaquant)
    {
        return false;
    }

    public bool EstVivant()
    {
        return PointsDeVie > 0;
    }
}

public class Guerrier : Personnage
{
    public Guerrier(string nom) : base(nom) { }

    public override void Attaquer(Personnage cible)
    {
        Console.WriteLine($"{Nom} attaque {cible.Nom} avec son épée !");
        if (!this.PeutSeProtéger(cible))
        {
            cible.PointsDeVie -= 20;
            Console.WriteLine($"{cible.Nom} perd 20 points de vie. Points de vie restants : {cible.PointsDeVie}");
        }
        else
        {
            Console.WriteLine($"{cible.Nom} se protège. Aucun dégât n'est infligé.");
        }
    }

}

public class Mage : Personnage
{
    public Mage(string nom) : base(nom) { }

    public override void Attaquer(Personnage cible)
    {
        Console.WriteLine($"{Nom} lance une boule de feu sur {cible.Nom} !");
        if (!this.PeutSeProtéger(cible))
        {
            cible.PointsDeVie -= 30;
            Console.WriteLine($"{cible.Nom} perd 30 points de vie. Points de vie restants : {cible.PointsDeVie}");
        }
        else
        {
            Console.WriteLine($"{cible.Nom} se protège. Aucun dégât n'est infligé.");
        }
    }

    public override bool PeutSeProtéger(Personnage attaquant)
    {
        return attaquant is Mage || attaquant is Guerrier;
    }
}

public class Archer : Personnage
{
    public Archer(string nom) : base(nom) { }

    public override void Attaquer(Personnage cible)
    {
        Console.WriteLine($"{Nom} tire une flèche sur {cible.Nom} !");
        if (this.PeutSeProtéger(cible))
        {
            Console.WriteLine($"{cible.Nom} se protège. Aucun dégât n'est infligé.");
            return;
        }
        cible.PointsDeVie -= 15;
        Console.WriteLine($"{cible.Nom} perd 15 points de vie. Points de vie restants : {cible.PointsDeVie}");
    }

    public override bool PeutSeProtéger(Personnage attaquant)
    {
        return attaquant.PointsDeVie < 35;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Personnage guerrier = new Guerrier("Conan");
        Personnage mage = new Mage("Gandalf");
        Personnage archer = new Archer("Legolas");

        List<Personnage> personnages = new List<Personnage> { guerrier, mage, archer };

        AfficheVies(personnages);

        foreach (Personnage personnage in personnages)
        {
            Console.WriteLine($"====== Combat avec {personnage.Nom} ======");
            foreach (Personnage cible in personnages)
            {
                if (cible != personnage)
                {
                    personnage.Attaquer(cible);
                }
            }
            Console.WriteLine();
        }

        AfficheVies(personnages);
    }

    private static void AfficheVies(List<Personnage> personnages)
    {
        foreach (Personnage personnage in personnages)
        {
            Console.WriteLine($"{personnage.Nom} est {(personnage.EstVivant() ? "vivant" : "mort")} avec {personnage.PointsDeVie} points de vie.");
        }
        Console.WriteLine();
    }
}
```

1. Sans utiliser de votre ordinateur, exécutez le code sur une feuille. Quel est le résultat ?
2. Exécutez le code sur votre ordinateur. Comparez le résultat avec votre prédiction.
3. Commentez le code pour expliquer ce qui se passe.
4. Ajoutez un nouveau type de personnage, le ```Paladin```. Un paladin est un personnage qui peut se protéger contre les attaques de mages et d'archers. Un paladin ne peut pas se protéger contre les attaques de guerriers. Un paladin inflige 25 points de dégâts lorsqu'il attaque. Implémentez le code nécessaire pour que le programme fonctionne avec un paladin en plus dans les personnages.

## Exercice 2

Soit le code suivant :

```csharp
class A
{
    public virtual void M_virtual()
    {
        Console.WriteLine("A>>M_virtual");
    }

    public void M_nonVirtual()
    {
        Console.WriteLine("A>>M_nonVirtual");
    }


}

class B : A
{
    public override void M_virtual()
    {
        Console.WriteLine("B>>M_virtual");
    }
    public void M_nonVirtual()  // override impossible, new possible, new virtual possible
    {
        Console.WriteLine("B>>M_nonVirtual");
    }
}

class C : A
{

}

class L : C
{
    
}

class D : C
{
    public override void M_virtual()
    {
        Console.WriteLine("D>>M_virtual");
    }
    public new virtual void M_nonVirtual() // override impossible
    {
        Console.WriteLine("D>>M_new nonVirtual");
    }
}

class E : D
{
    public override void M_nonVirtual()
    {
        Console.WriteLine("E>>M_new nonVirtual");
    }

}
class F : A
{
    public new void M_virtual()
    {
        Console.WriteLine("F>>M_virtual");
    }
}

class M : F
{
    //public override void M_virtual() <-- impossible
    //{
    //    Console.WriteLine("M>>M_virtual");
    //}

    public new virtual void M_virtual()
    {
        Console.WriteLine("M>>M_virtual");
    }
}


class N : M
{
    public new virtual void M_virtual()
    {
        Console.WriteLine("N>>N_virtual");
    }
}
class G : D
{
    public new void M_virtual()
    {
        Console.WriteLine("G>>M_virtual");
    }
}

abstract class H
{
    public abstract void M();
}

class I : H
{
    public override void M()
    {
        Console.WriteLine("Je suis un I");
    }
}

class J : I
{
    public virtual void M()
    {
        Console.WriteLine("Je suis J");
    }
}
class K : J
{
    public override void M()
    {
        Console.WriteLine("JE suis K");
    }
}
class Program
{
    public static void Main() {
        A a1 = new A();
        a1.M_virtual();
        a1.M_nonVirtual();

        A a2 = new B();
        a2.M_virtual();
        a2.M_nonVirtual();

        A a3 = new C();
        a3.M_virtual();
        a3.M_nonVirtual();

        A a4 = new D();
        a4.M_virtual();
        a4.M_nonVirtual();

        C c = new D();
        c.M_virtual();
        c.M_nonVirtual();

        D d = new E();
        d.M_virtual();
        d.M_nonVirtual();

        A a5 = new E();
        a5.M_virtual();
        a5.M_nonVirtual();

        C c12 = new L();
        c12.M_virtual();

        A a6 = new F();
        a6.M_virtual();

        A a7 = new G();
        a7.M_virtual();

        I i1 = new J();
        i1.M();

        I i2 = new K();
        i2.M();

        J j = new K();
        j.M();
    }
}
```

1. Sans utiliser de votre ordinateur, exécutez le code sur une feuille. Quel est le résultat ?
2. Exécutez le code sur votre ordinateur. Comparez le résultat avec votre prédiction.

<details>
<summary>Solution</summary>

```csharp
A>>M_virtual
A>>M_nonVirtual
B>>M_virtual
A>>M_nonVirtual
A>>M_virtual
A>>M_nonVirtual
D>>M_virtual
A>>M_nonVirtual
D>>M_virtual
A>>M_nonVirtual
D>>M_virtual
E>>M_new nonVirtual
D>>M_virtual
A>>M_nonVirtual
A>>M_virtual
A>>M_virtual
D>>M_virtual
Je suis un I
Je suis un I
JE suis K
```
</details>