# Les Classes Génériques en C#

## Exercice 1 : Compréhension de Code

### Question 1

Considérez le code suivant :

```csharp
public class GenericList<T>
{
    private T[] elements;
    private int count = 0;

    public GenericList(int capacity)
    {
        elements = new T[capacity];
    }

    public void Add(T item)
    {
        if (count < elements.Length)
        {
            elements[count] = item;
            count++;
        }
        else
        {
            throw new InvalidOperationException("List capacity exceeded.");
        }
    }

    public T GetElement(int index)
    {
        if (index >= 0 && index < count)
        {
            return elements[index];
        }
        else
        {
            throw new ArgumentOutOfRangeException("Index out of range.");
        }
    }
}
```

Quel est le rôle de la classe `GenericList<T>` et comment fonctionne-t-elle ?

<details>
<summary>Solution</summary>

La classe `GenericList<T>` est une liste générique qui peut contenir des éléments de n'importe quel type spécifié au moment de l'instanciation de la liste. Elle utilise un tableau interne `elements` pour stocker les éléments et un compteur `count` pour suivre le nombre d'éléments ajoutés.

- Le constructeur `GenericList(int capacity)` initialise le tableau `elements` avec une capacité donnée.
- La méthode `Add(T item)` ajoute un élément à la liste si la capacité n'est pas dépassée ; sinon, elle lève une exception `InvalidOperationException`.
- La méthode `GetElement(int index)` retourne l'élément à l'index spécifié si celui-ci est valide ; sinon, elle lève une exception `ArgumentOutOfRangeException`.

</details>

### Question 2

Quelle sera la sortie du code suivant ?

```csharp
GenericList<string> stringList = new GenericList<string>(3);
stringList.Add("Hello");
stringList.Add("World");
Console.WriteLine(stringList.GetElement(0));
Console.WriteLine(stringList.GetElement(1));
Console.WriteLine(stringList.GetElement(2));
```

<details>
<summary>Solution</summary>

Le code lèvera une exception `ArgumentOutOfRangeException` lorsque la méthode `GetElement(2)` sera appelée car il n'y a que deux éléments dans la liste (indices 0 et 1). La sortie sera :

```
Hello
World
Exception: ArgumentOutOfRangeException
```
</details>


---

## Exercice 2 : Production de Code

### Question 1

Implémentez une classe générique `Pair<T1, T2>` qui peut contenir deux valeurs de types différents.

<details>
<summary>Solution</summary>

```csharp
public class Pair<T1, T2>
{
    public T1 First { get; set; }
    public T2 Second { get; set; }

    public Pair(T1 first, T2 second)
    {
        First = first;
        Second = second;
    }

    public override string ToString()
    {
        return $"({First}, {Second})";
    }
}
```

</details>

### Question 2

Utilisez la classe `Pair<T1, T2>` pour créer une liste de paires et afficher leur contenu. Chaque paire doit contenir un `string` et un `int`.

<details>
<summary>Solution</summary>

```csharp
List<Pair<string, int>> pairs = new List<Pair<string, int>>
{
    new Pair<string, int>("One", 1),
    new Pair<string, int>("Two", 2),
    new Pair<string, int>("Three", 3)
};

foreach (var pair in pairs)
{
    Console.WriteLine(pair);
}
```

La sortie sera :

```
(One, 1)
(Two, 2)
(Three, 3)
```

</details>

---

## Exercice 3 : Compréhension et Production de Code

### Question 1

Considérez le code suivant pour une pile générique :

```csharp
public class Stack<T>
{
    private List<T> elements = new List<T>();

    public void Push(T item)
    {
        elements.Add(item);
    }

    public T Pop()
    {
        if (elements.Count == 0)
        {
            throw new InvalidOperationException("Stack is empty.");
        }
        T item = elements[elements.Count - 1];
        elements.RemoveAt(elements.Count - 1);
        return item;
    }

    public T Peek()
    {
        if (elements.Count == 0)
        {
            throw new InvalidOperationException("Stack is empty.");
        }
        return elements[elements.Count - 1];
    }

    public int Count => elements.Count;
}
```

Ajoutez une méthode `Clear` pour vider la pile et une méthode `Contains` pour vérifier si un élément est présent dans la pile.

<details>
<summary>Solution</summary>

```csharp
public class Stack<T>
{
    private List<T> elements = new List<T>();

    public void Push(T item)
    {
        elements.Add(item);
    }

    public T Pop()
    {
        if (elements.Count == 0)
        {
            throw new InvalidOperationException("Stack is empty.");
        }
        T item = elements[elements.Count - 1];
        elements.RemoveAt(elements.Count - 1);
        return item;
    }

    public T Peek()
    {
        if (elements.Count == 0)
        {
            throw new InvalidOperationException("Stack is empty.");
        }
        return elements[elements.Count - 1];
    }

    public int Count => elements.Count;

    public void Clear()
    {
        elements.Clear();
    }

    public bool Contains(T item)
    {
        return elements.Contains(item);
    }
}
```

</details>

### Question 2

Écrivez un programme qui utilise la classe `Stack<T>` pour inverser les éléments d'un tableau de chaînes de caractères.

<details>
<summary>Solution</summary>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        string[] words = { "apple", "banana", "cherry" };
        Stack<string> stack = new Stack<string>();

        foreach (var word in words)
        {
            stack.Push(word);
        }

        for (int i = 0; i < words.Length; i++)
        {
            words[i] = stack.Pop();
        }

        foreach (var word in words)
        {
            Console.WriteLine(word);
        }
    }
}
```

La sortie sera :

```
cherry
banana
apple
```

</details>

