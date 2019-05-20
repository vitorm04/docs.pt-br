---
title: Iterar em coleções em C#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 931f0662b71b4dd99ac4a419c279be5058c61e92
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635515"
---
# <a name="iterators-c"></a><span data-ttu-id="48f02-102">Iteradores (C#)</span><span class="sxs-lookup"><span data-stu-id="48f02-102">Iterators (C#)</span></span>

<span data-ttu-id="48f02-103">Um *iterador* pode ser usado para percorrer coleções, como listas e matrizes.</span><span class="sxs-lookup"><span data-stu-id="48f02-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="48f02-104">Um método iterador ou um acessador `get` realiza uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="48f02-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="48f02-105">Um método iterador usa a instrução [yield return](../../../csharp/language-reference/keywords/yield.md) para retornar um elemento de cada vez.</span><span class="sxs-lookup"><span data-stu-id="48f02-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="48f02-106">Quando uma instrução `yield return` for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="48f02-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="48f02-107">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="48f02-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="48f02-108">Um iterador é consumido no código cliente, usando uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="48f02-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="48f02-109">No exemplo a seguir, a primeira iteração do loop `foreach` faz que a execução continue no método iterador `SomeNumbers` até que a primeira instrução `yield return` seja alcançada.</span><span class="sxs-lookup"><span data-stu-id="48f02-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="48f02-110">Essa iteração retorna um valor de 3 e o local atual no método iterador é mantido.</span><span class="sxs-lookup"><span data-stu-id="48f02-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="48f02-111">Na próxima iteração do loop, a execução no método iterador continuará de onde parou, parando novamente quando alcançar uma instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="48f02-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="48f02-112">Essa iteração retorna um valor de 5 e o local atual no método iterador é mantido novamente.</span><span class="sxs-lookup"><span data-stu-id="48f02-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="48f02-113">O loop terminará quando o final do método iterador for alcançado.</span><span class="sxs-lookup"><span data-stu-id="48f02-113">The loop completes when the end of the iterator method is reached.</span></span>

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

<span data-ttu-id="48f02-114">O tipo de retorno de um método iterador ou acessador `get` pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="48f02-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="48f02-115">Você pode usar uma instrução `yield break` para terminar a iteração.</span><span class="sxs-lookup"><span data-stu-id="48f02-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="48f02-116">Todos os exemplos neste tópico, exceto o exemplo Iterador Simples, incluem diretivas [using](../../../csharp/language-reference/keywords/using-directive.md) para os namespaces `System.Collections` e `System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="48f02-116">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="48f02-117">Iterador simples</span><span class="sxs-lookup"><span data-stu-id="48f02-117">Simple Iterator</span></span>

<span data-ttu-id="48f02-118">O exemplo a seguir contém uma única instrução `yield return` que está dentro de um loop [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="48f02-118">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="48f02-119">Em `Main`, cada iteração do corpo da instrução `foreach` cria uma chamada à função iteradora, que avança para a próxima instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="48f02-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a><span data-ttu-id="48f02-120">Criando uma classe de coleção</span><span class="sxs-lookup"><span data-stu-id="48f02-120">Creating a Collection Class</span></span>

<span data-ttu-id="48f02-121">No exemplo a seguir, a classe `DaysOfTheWeek` implementa a interface <xref:System.Collections.IEnumerable>, que requer um método <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="48f02-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="48f02-122">O compilador chama implicitamente o método `GetEnumerator`, que retorna um <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="48f02-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="48f02-123">O método `GetEnumerator` retorna cada cadeia de caracteres, uma de cada vez, usando a instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="48f02-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

<span data-ttu-id="48f02-124">O exemplo a seguir cria uma classe `Zoo` que contém uma coleção de animais.</span><span class="sxs-lookup"><span data-stu-id="48f02-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="48f02-125">A instrução `foreach`, que faz referência à instância de classe (`theZoo`), chama implicitamente o método `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="48f02-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="48f02-126">As instruções `foreach`, que fazem referência às propriedades `Birds` e `Mammals`, usam o método iterador nomeado `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="48f02-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="48f02-127">Usando iteradores com uma lista genérica</span><span class="sxs-lookup"><span data-stu-id="48f02-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="48f02-128">No exemplo a seguir, a classe <xref:System.Collections.Generic.Stack%601> genérica implementa a interface genérica <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="48f02-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="48f02-129">O método <xref:System.Collections.Generic.Stack%601.Push%2A> atribui valores a uma matriz do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="48f02-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="48f02-130">O método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> retorna os valores da matriz usando a instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="48f02-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="48f02-131">Além do método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genérico, o método <xref:System.Collections.IEnumerable.GetEnumerator%2A> não genérico também deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="48f02-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="48f02-132">Isso ocorre porque <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="48f02-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="48f02-133">A implementação não genérica adia a implementação genérica.</span><span class="sxs-lookup"><span data-stu-id="48f02-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="48f02-134">O exemplo usa iteradores nomeados para dar suporte a várias maneiras de iterar na mesma coleção de dados.</span><span class="sxs-lookup"><span data-stu-id="48f02-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="48f02-135">Esses iteradores nomeados são as propriedades `TopToBottom` e `BottomToTop` e o método `TopN`.</span><span class="sxs-lookup"><span data-stu-id="48f02-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="48f02-136">A propriedade `BottomToTop` usa um iterador em um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="48f02-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a><span data-ttu-id="48f02-137">Informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="48f02-137">Syntax Information</span></span>

<span data-ttu-id="48f02-138">Um iterador pode ocorrer como um método ou como um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="48f02-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="48f02-139">Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um finalizador estático.</span><span class="sxs-lookup"><span data-stu-id="48f02-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="48f02-140">Deve haver uma conversão implícita do tipo de expressão na instrução `yield return` para o argumento de tipo no IEnumerable\<T> retornado pelo iterador.</span><span class="sxs-lookup"><span data-stu-id="48f02-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the IEnumerable\<T> returned by the iterator.</span></span>

<span data-ttu-id="48f02-141">Em C#, um método iterador não pode ter os parâmetros `in`, `ref` nem `out`.</span><span class="sxs-lookup"><span data-stu-id="48f02-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="48f02-142">No C#, a "yield" não é uma palavra reservada e, só terá um significado especial, quando for usada antes de uma palavra-chave `return` ou `break`.</span><span class="sxs-lookup"><span data-stu-id="48f02-142">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="48f02-143">Implementação Técnica</span><span class="sxs-lookup"><span data-stu-id="48f02-143">Technical Implementation</span></span>

<span data-ttu-id="48f02-144">Embora você escreva um iterador como um método, o compilador o traduz em uma classe aninhada que é, na verdade, uma máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="48f02-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="48f02-145">Essa classe mantém o controle da posição do iterador enquanto o loop `foreach` no código cliente continuar.</span><span class="sxs-lookup"><span data-stu-id="48f02-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="48f02-146">Para ver o que o compilador faz, você pode usar a ferramenta Ildasm.exe para exibir o código Microsoft Intermediate Language que é gerado para um método iterador.</span><span class="sxs-lookup"><span data-stu-id="48f02-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="48f02-147">Quando você cria um iterador para uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), não é necessário implementar toda a interface <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="48f02-147">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="48f02-148">Quando o compilador detecta o iterador, ele gera automaticamente os métodos `Current`, `MoveNext` e `Dispose` da interface <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="48f02-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="48f02-149">A cada iteração sucessiva do loop `foreach` (ou a chamada direta ao `IEnumerator.MoveNext`), o próximo corpo de código do iterador continua, depois da instrução `yield return` anterior.</span><span class="sxs-lookup"><span data-stu-id="48f02-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="48f02-150">Em seguida, ele continuará até a próxima instrução `yield return`, até que o final do corpo do iterador seja alcançado ou até que uma instrução `yield break` seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="48f02-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="48f02-151">Iteradores não dão suporte ao método <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="48f02-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="48f02-152">Para iterar novamente desde o início, você deve obter um novo iterador.</span><span class="sxs-lookup"><span data-stu-id="48f02-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="48f02-153">Chamar <xref:System.Collections.IEnumerator.Reset%2A> no iterador retornado por um método iterador lança um <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="48f02-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="48f02-154">Para obter informações adicionais, consulte a [Especificação da linguagem C#](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="48f02-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="48f02-155">Uso de iteradores</span><span class="sxs-lookup"><span data-stu-id="48f02-155">Use of Iterators</span></span>

<span data-ttu-id="48f02-156">Os iteradores permitem que você mantenha a simplicidade de um loop `foreach` quando for necessário usar um código complexo para preencher uma sequência de lista.</span><span class="sxs-lookup"><span data-stu-id="48f02-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="48f02-157">Isso pode ser útil quando você quiser fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="48f02-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="48f02-158">Modificar a sequência de lista após a primeira iteração de loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="48f02-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="48f02-159">Evitar o carregamento completo de uma grande lista antes da primeira iteração de um loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="48f02-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="48f02-160">Um exemplo é uma busca paginada para carregar um lote de linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="48f02-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="48f02-161">Outro exemplo é o método <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, que implementa os iteradores dentro do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48f02-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="48f02-162">Encapsular a criação da lista no iterador.</span><span class="sxs-lookup"><span data-stu-id="48f02-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="48f02-163">No método iterador, você pode criar a lista e, em seguida, gerar cada resultado em um loop.</span><span class="sxs-lookup"><span data-stu-id="48f02-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="48f02-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48f02-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="48f02-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="48f02-165">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="48f02-166">yield</span><span class="sxs-lookup"><span data-stu-id="48f02-166">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)
- [<span data-ttu-id="48f02-167">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="48f02-167">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="48f02-168">Genéricos</span><span class="sxs-lookup"><span data-stu-id="48f02-168">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
