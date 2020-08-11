---
title: Delegados e lambdas
description: Saiba como os delegados, que definem um tipo que especifica uma assinatura de método específico, podem ser chamados diretamente ou passados para outro método e chamados.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 1307599a3832be5f48cd62a7b8c1be7f76a3d4a5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063738"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="f6df9-103">Delegados e lambdas</span><span class="sxs-lookup"><span data-stu-id="f6df9-103">Delegates and lambdas</span></span>

<span data-ttu-id="f6df9-104">Delegados definem um tipo que especifica uma assinatura de método em particular.</span><span class="sxs-lookup"><span data-stu-id="f6df9-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="f6df9-105">Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada.</span><span class="sxs-lookup"><span data-stu-id="f6df9-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="f6df9-106">O exemplo a seguir demonstra o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="f6df9-107">A linha `public delegate string Reverse(string s);` cria um tipo de delegado de determinada assinatura, nesse caso, um método que usa um parâmetro de cadeia de caracteres e, em seguida, retorna um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f6df9-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="f6df9-108">O método `static string ReverseString(string s)`, que tem exatamente a mesma assinatura do tipo de delegado definido, implementa o delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="f6df9-109">A linha `Reverse rev = ReverseString;` mostra que você pode atribuir um método a uma variável do tipo de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="f6df9-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="f6df9-110">A linha `Console.WriteLine(rev("a string"));` demonstra como usar uma variável de um tipo de delegado para invocar o delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="f6df9-111">Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="f6df9-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="f6df9-112">Esses tipos são `Func<>` , `Action<>` e `Predicate<>` , e podem ser usados sem a necessidade de definir novos tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="f6df9-113">Há algumas diferenças entre os três tipos que devem ser feitas com a maneira como se destinam a serem usadas:</span><span class="sxs-lookup"><span data-stu-id="f6df9-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="f6df9-114">`Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="f6df9-115">O método encapsulado não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="f6df9-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="f6df9-116">`Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente.</span><span class="sxs-lookup"><span data-stu-id="f6df9-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="f6df9-117">As projeções são um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="f6df9-117">Projections are a good example.</span></span> <span data-ttu-id="f6df9-118">O método que ele encapsula retorna um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="f6df9-119">`Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="f6df9-120">Ele também pode ser escrito como um `Func<T, bool>` , o que significa que o método retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="f6df9-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="f6df9-121">Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="f6df9-122">O programa continuará sendo executado exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="f6df9-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="f6df9-123">Para este exemplo simples, ter um método definido fora do método `Main` parece um pouco supérfluo.</span><span class="sxs-lookup"><span data-stu-id="f6df9-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="f6df9-124">.NET Framework 2,0 introduziu o conceito de *delegados anônimos*, que permitem criar delegados "embutidos" sem precisar especificar nenhum tipo ou método adicional.</span><span class="sxs-lookup"><span data-stu-id="f6df9-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="f6df9-125">No exemplo a seguir, um delegado anônimo filtra uma lista para apenas os números pares e, em seguida, imprime-as no console.</span><span class="sxs-lookup"><span data-stu-id="f6df9-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="f6df9-126">Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="f6df9-127">Mas, em vez de ser uma definição separada, apresentamos o _ad hoc_ em nossa chamada para o <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="f6df9-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f6df9-128">No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar.</span><span class="sxs-lookup"><span data-stu-id="f6df9-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="f6df9-129">É aí que as *expressões lambda* entram em cena.</span><span class="sxs-lookup"><span data-stu-id="f6df9-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="f6df9-130">As expressões lambda ou apenas "lambdas" para abreviar foram introduzidas em C# 3,0 como um dos principais blocos de construção da LINQ (linguagem integrada de consulta).</span><span class="sxs-lookup"><span data-stu-id="f6df9-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="f6df9-131">Elas são apenas uma sintaxe mais conveniente para usar delegados.</span><span class="sxs-lookup"><span data-stu-id="f6df9-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="f6df9-132">Eles declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam atribuídos a um delegado.</span><span class="sxs-lookup"><span data-stu-id="f6df9-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="f6df9-133">Ao contrário dos delegados, eles podem ser diretamente atribuídos como o lado direito do registro de evento ou em várias cláusulas e métodos LINQ.</span><span class="sxs-lookup"><span data-stu-id="f6df9-133">Unlike delegates, they can be directly assigned as the right-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="f6df9-134">Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="f6df9-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="f6df9-135">No exemplo anterior, a expressão lambda usada é `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="f6df9-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="f6df9-136">Novamente, é apenas uma sintaxe conveniente para usar delegados.</span><span class="sxs-lookup"><span data-stu-id="f6df9-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="f6df9-137">O que acontece nos bastidores é semelhante ao que acontece com o delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="f6df9-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="f6df9-138">Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o snippet de código a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="f6df9-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="f6df9-139">O operador `+=` nesse contexto é usado para assinar um [evento](../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="f6df9-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="f6df9-140">Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6df9-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="f6df9-141">Recursos e leituras adicionais</span><span class="sxs-lookup"><span data-stu-id="f6df9-141">Further reading and resources</span></span>

* [<span data-ttu-id="f6df9-142">Representantes</span><span class="sxs-lookup"><span data-stu-id="f6df9-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="f6df9-143">Funções anônimas</span><span class="sxs-lookup"><span data-stu-id="f6df9-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="f6df9-144">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="f6df9-144">Lambda expressions</span></span>](../csharp/language-reference/operators/lambda-expressions.md)
