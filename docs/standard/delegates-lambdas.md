---
title: Delegados e lambdas
description: Saiba como os delegados, que definem um tipo que especifica uma determinada assinatura de método, podem ser chamados diretamente ou passados para outro método e chamados.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: a9ca935814d1a7f77ded5f371ccd496c3859c523
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635933"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="f202d-103">Delegados e lambdas</span><span class="sxs-lookup"><span data-stu-id="f202d-103">Delegates and lambdas</span></span>

<span data-ttu-id="f202d-104">Os delegados definem um tipo que especifica uma assinatura de método específica.</span><span class="sxs-lookup"><span data-stu-id="f202d-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="f202d-105">Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada.</span><span class="sxs-lookup"><span data-stu-id="f202d-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="f202d-106">O exemplo a seguir demonstra o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="f202d-107">A linha `public delegate string Reverse(string s);` cria um tipo de delegado de determinada assinatura, nesse caso, um método que usa um parâmetro de cadeia de caracteres e, em seguida, retorna um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f202d-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="f202d-108">O método `static string ReverseString(string s)`, que tem exatamente a mesma assinatura do tipo de delegado definido, implementa o delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="f202d-109">A linha `Reverse rev = ReverseString;` mostra que você pode atribuir um método a uma variável do tipo de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="f202d-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="f202d-110">A linha `Console.WriteLine(rev("a string"));` demonstra como usar uma variável de um tipo de delegado para invocar o delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="f202d-111">Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="f202d-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="f202d-112">Esses tipos `Func<>` `Action<>` são `Predicate<>`, e , e podem ser usados sem ter que definir novos tipos de delegados.</span><span class="sxs-lookup"><span data-stu-id="f202d-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="f202d-113">Existem algumas diferenças entre os três tipos que têm a ver com a forma como foram destinados a serem usados:</span><span class="sxs-lookup"><span data-stu-id="f202d-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="f202d-114">`Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="f202d-115">O método que encapsula não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="f202d-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="f202d-116">`Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente.</span><span class="sxs-lookup"><span data-stu-id="f202d-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="f202d-117">Projeções são um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="f202d-117">Projections are a good example.</span></span> <span data-ttu-id="f202d-118">O método que encapsula retorna um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="f202d-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="f202d-119">`Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="f202d-120">Também pode ser escrito `Func<T, bool>`como um , o que significa que o método retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="f202d-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="f202d-121">Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f202d-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="f202d-122">O programa continuará sendo executado exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="f202d-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="f202d-123">Para este exemplo simples, ter um método definido fora do método `Main` parece um pouco supérfluo.</span><span class="sxs-lookup"><span data-stu-id="f202d-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="f202d-124">.NET Framework 2.0 introduziu o conceito de *delegados anônimos,* que permitem criar delegados "inline" sem ter que especificar qualquer tipo ou método adicional.</span><span class="sxs-lookup"><span data-stu-id="f202d-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="f202d-125">No exemplo a seguir, um delegado anônimo filtra uma lista apenas para os números pares e, em seguida, imprime-os para o console.</span><span class="sxs-lookup"><span data-stu-id="f202d-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="f202d-126">Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="f202d-127">Mas em vez de ser uma definição separada, nós introduzimos _ad hoc_ em nossa chamada para o <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="f202d-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f202d-128">No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar.</span><span class="sxs-lookup"><span data-stu-id="f202d-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="f202d-129">É aí que as *expressões lambda* entram em cena.</span><span class="sxs-lookup"><span data-stu-id="f202d-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="f202d-130">Expressões lambda, ou apenas "lambdas" para abreviar, foram introduzidas em C# 3.0 como um dos principais blocos de construção da Linguagem Integrada Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="f202d-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="f202d-131">Elas são apenas uma sintaxe mais conveniente para usar delegados.</span><span class="sxs-lookup"><span data-stu-id="f202d-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="f202d-132">Eles declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam designados para um delegado.</span><span class="sxs-lookup"><span data-stu-id="f202d-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="f202d-133">Ao contrário dos representantes, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos LINQ.</span><span class="sxs-lookup"><span data-stu-id="f202d-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="f202d-134">Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="f202d-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="f202d-135">No exemplo anterior, a expressão lambda usada é `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="f202d-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="f202d-136">Novamente, é apenas uma sintaxe conveniente para o uso de delegados.</span><span class="sxs-lookup"><span data-stu-id="f202d-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="f202d-137">O que acontece sob as cobertas é semelhante ao que acontece com o delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="f202d-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="f202d-138">Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o snippet de código a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="f202d-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="f202d-139">O operador `+=` nesse contexto é usado para assinar um [evento](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="f202d-139">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="f202d-140">Para obter mais informações, consulte [Como se inscrever e cancelar a inscrição de eventos](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f202d-140">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="f202d-141">Recursos e leituras adicionais</span><span class="sxs-lookup"><span data-stu-id="f202d-141">Further reading and resources</span></span>

* [<span data-ttu-id="f202d-142">Delegados</span><span class="sxs-lookup"><span data-stu-id="f202d-142">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="f202d-143">Funções Anônimas</span><span class="sxs-lookup"><span data-stu-id="f202d-143">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="f202d-144">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="f202d-144">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
