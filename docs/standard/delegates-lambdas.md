---
title: Delegados e lambdas
description: Saiba como delegados definem um tipo, que especifica a assinatura de um método específico, que pode ser chamado diretamente ou passado para outro método e, em seguida, chamado.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: e392f6b2e57bebf1ab916bc6142aebbc8f341db2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615306"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="9ab90-103">Delegados e lambdas</span><span class="sxs-lookup"><span data-stu-id="9ab90-103">Delegates and lambdas</span></span>

<span data-ttu-id="9ab90-104">Os delegados definem um tipo, que especifica uma assinatura de método específica.</span><span class="sxs-lookup"><span data-stu-id="9ab90-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="9ab90-105">Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada.</span><span class="sxs-lookup"><span data-stu-id="9ab90-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="9ab90-106">O exemplo a seguir demonstra o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* <span data-ttu-id="9ab90-107">A linha `public delegate string Reverse(string s);` cria um tipo de delegado de determinada assinatura, nesse caso, um método que usa um parâmetro de cadeia de caracteres e, em seguida, retorna um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9ab90-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="9ab90-108">O método `static string ReverseString(string s)`, que tem exatamente a mesma assinatura do tipo de delegado definido, implementa o delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="9ab90-109">A linha `Reverse rev = ReverseString;` mostra que você pode atribuir um método a uma variável do tipo de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="9ab90-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="9ab90-110">A linha `Console.WriteLine(rev("a string"));` demonstra como usar uma variável de um tipo de delegado para invocar o delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="9ab90-111">Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="9ab90-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="9ab90-112">Eles são `Func<>`, `Action<>` e `Predicate<>`, e podem ser usados em vários locais das APIs .NET sem a necessidade de definir novos tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="9ab90-113">Obviamente, há algumas diferenças entre os três, que você verá em suas assinaturas e que geralmente têm a ver com a maneira como eles deveriam ser usados:</span><span class="sxs-lookup"><span data-stu-id="9ab90-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="9ab90-114">`Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
* <span data-ttu-id="9ab90-115">`Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente.</span><span class="sxs-lookup"><span data-stu-id="9ab90-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="9ab90-116">As projeções são um excelente exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="9ab90-116">Projections are a prime example of this.</span></span>
* <span data-ttu-id="9ab90-117">`Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="9ab90-118">Ele também pode ser escrito como um `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="9ab90-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="9ab90-119">Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="9ab90-120">O programa continuará sendo executado exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="9ab90-120">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

<span data-ttu-id="9ab90-121">Para este exemplo simples, ter um método definido fora do método `Main` parece um pouco supérfluo.</span><span class="sxs-lookup"><span data-stu-id="9ab90-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="9ab90-122">É por isso que o .NET Framework 2.0 introduziu o conceito de **delegados anônimos**.</span><span class="sxs-lookup"><span data-stu-id="9ab90-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="9ab90-123">Com suporte deles, você pode criar delegados "embutidos" sem precisar especificar tipos ou métodos adicionais.</span><span class="sxs-lookup"><span data-stu-id="9ab90-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="9ab90-124">Você simplesmente embute a definição do delegado onde precisar dela.</span><span class="sxs-lookup"><span data-stu-id="9ab90-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="9ab90-125">Para dar um exemplo, vamos trocá-lo e usar nosso delegado anônimo para filtrar uma lista com apenas os números pares e, em seguida, imprimi-los no console.</span><span class="sxs-lookup"><span data-stu-id="9ab90-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="9ab90-126">Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="9ab90-127">Mas em vez de ele ser uma definição separada, nós o introduzimos _ad hoc_ em nossa chamada ao método <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ab90-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9ab90-128">No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar.</span><span class="sxs-lookup"><span data-stu-id="9ab90-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="9ab90-129">É aí que as **expressões lambda** entram em cena.</span><span class="sxs-lookup"><span data-stu-id="9ab90-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="9ab90-130">As expressões lambda ou apenas "lambdas" para abreviar, foram introduzidas pela primeira vez no C# 3.0 como um dos principais elementos de construção da LINQ (Consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="9ab90-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="9ab90-131">Elas são apenas uma sintaxe mais conveniente para usar delegados.</span><span class="sxs-lookup"><span data-stu-id="9ab90-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="9ab90-132">Elas declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam atribuídas a um delegado.</span><span class="sxs-lookup"><span data-stu-id="9ab90-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="9ab90-133">Ao contrário dos representantes, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos LINQ.</span><span class="sxs-lookup"><span data-stu-id="9ab90-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="9ab90-134">Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="9ab90-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="9ab90-135">No exemplo anterior, a expressão lambda usada é `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="9ab90-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="9ab90-136">Mais uma vez, trata-se apenas de uma sintaxe **muito** conveniente para usar delegados, de modo que o que acontece nos bastidores é semelhante ao que acontece com o delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="9ab90-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="9ab90-137">Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o snippet de código a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="9ab90-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

<span data-ttu-id="9ab90-138">O operador `+=` nesse contexto é usado para assinar um [evento](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="9ab90-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="9ab90-139">Para obter mais informações, confira [Como: realizar e cancelar a assinatura de eventos](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="9ab90-139">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="9ab90-140">Recursos e leituras adicionais</span><span class="sxs-lookup"><span data-stu-id="9ab90-140">Further reading and resources</span></span>

* [<span data-ttu-id="9ab90-141">Delegados</span><span class="sxs-lookup"><span data-stu-id="9ab90-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="9ab90-142">Funções Anônimas</span><span class="sxs-lookup"><span data-stu-id="9ab90-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="9ab90-143">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="9ab90-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
