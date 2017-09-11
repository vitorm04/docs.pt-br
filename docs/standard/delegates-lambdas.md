---
title: Delegados e lambdas
description: "Saiba como delegados definem um tipo, que especifica a assinatura de um método específico, que pode ser chamado diretamente ou passado para outro método e, em seguida, chamado."
keywords: .NET, .NET Core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.translationtype: HT
ms.sourcegitcommit: ef6d1bf9a7153f7adf635d13b4dcfb7647ed2e33
ms.openlocfilehash: d04a158db4f97a0e37f8a92149a3f237ee2e5434
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---

# <a name="delegates-and-lambdas"></a><span data-ttu-id="71aa1-104">Delegados e lambdas</span><span class="sxs-lookup"><span data-stu-id="71aa1-104">Delegates and lambdas</span></span>

<span data-ttu-id="71aa1-105">Os delegados definem um tipo, que especifica uma assinatura de método específica.</span><span class="sxs-lookup"><span data-stu-id="71aa1-105">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="71aa1-106">Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada.</span><span class="sxs-lookup"><span data-stu-id="71aa1-106">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="71aa1-107">O exemplo a seguir demonstra o uso de um delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-107">The following example demonstrates delegate use.</span></span>

```csharp
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

*   <span data-ttu-id="71aa1-108">Na linha 4, criamos um tipo de delegado de uma determinada assinatura, nesse caso um método que usa um parâmetro de cadeia de caracteres e retorna um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="71aa1-108">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="71aa1-109">Na linha 6, definimos a implementação do delegado fornecendo um método que tem exatamente a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="71aa1-109">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="71aa1-110">Na linha 13, o método é atribuído a um tipo que está de acordo com o delegado `Reverse`.</span><span class="sxs-lookup"><span data-stu-id="71aa1-110">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="71aa1-111">Por fim, na linha 15 invocamos o delegado passando uma cadeia de caracteres a ser revertida.</span><span class="sxs-lookup"><span data-stu-id="71aa1-111">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="71aa1-112">Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="71aa1-112">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="71aa1-113">Eles são `Func<>`, `Action<>` e `Predicate<>`, e podem ser usados em vários locais das APIs .NET sem a necessidade de definir novos tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-113">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="71aa1-114">Obviamente, há algumas diferenças entre os três, que você verá em suas assinaturas e que geralmente têm a ver com a maneira como eles deveriam ser usados:</span><span class="sxs-lookup"><span data-stu-id="71aa1-114">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="71aa1-115">`Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-115">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="71aa1-116">`Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente.</span><span class="sxs-lookup"><span data-stu-id="71aa1-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="71aa1-117">As projeções são um excelente exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="71aa1-117">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="71aa1-118">`Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-118">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="71aa1-119">Ele também pode ser escrito como um `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="71aa1-119">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="71aa1-120">Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-120">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="71aa1-121">O programa continuará sendo executado exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="71aa1-121">The program will continue running exactly the same.</span></span>

```csharp
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

<span data-ttu-id="71aa1-122">Para este exemplo simples, ter um método definido fora do método Main() parece um pouco supérfluo.</span><span class="sxs-lookup"><span data-stu-id="71aa1-122">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="71aa1-123">É por isso que o .NET Framework 2.0 introduziu o conceito de **delegados anônimos**.</span><span class="sxs-lookup"><span data-stu-id="71aa1-123">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="71aa1-124">Com suporte deles, você pode criar delegados "embutidos" sem precisar especificar tipos ou métodos adicionais.</span><span class="sxs-lookup"><span data-stu-id="71aa1-124">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="71aa1-125">Você simplesmente embute a definição do delegado onde precisar dela.</span><span class="sxs-lookup"><span data-stu-id="71aa1-125">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="71aa1-126">Para dar um exemplo, vamos trocá-lo e usar nosso delegado anônimo para filtrar uma lista com apenas os números pares e, em seguida, imprimi-los no console.</span><span class="sxs-lookup"><span data-stu-id="71aa1-126">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="71aa1-127">Observe as linhas realçadas.</span><span class="sxs-lookup"><span data-stu-id="71aa1-127">Notice the highlighted lines.</span></span> <span data-ttu-id="71aa1-128">Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="71aa1-129">Mas em vez dele ser uma definição separada, nós o introduzimos _ad hoc_ em nossa chamada para o método `FindAll()` do tipo `List<T>`.</span><span class="sxs-lookup"><span data-stu-id="71aa1-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="71aa1-130">No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar.</span><span class="sxs-lookup"><span data-stu-id="71aa1-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="71aa1-131">É aí que as **expressões lambda** entram em cena.</span><span class="sxs-lookup"><span data-stu-id="71aa1-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="71aa1-132">As expressões lambda ou apenas "lambdas" para abreviar, foram introduzidas pela primeira vez no C# 3.0 como um dos principais elementos de construção da LINQ (Consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="71aa1-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="71aa1-133">Elas são apenas uma sintaxe mais conveniente para usar delegados.</span><span class="sxs-lookup"><span data-stu-id="71aa1-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="71aa1-134">Elas declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam atribuídas a um delegado.</span><span class="sxs-lookup"><span data-stu-id="71aa1-134">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="71aa1-135">Diferente dos delegados, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos Linq.</span><span class="sxs-lookup"><span data-stu-id="71aa1-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="71aa1-136">Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="71aa1-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
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

<span data-ttu-id="71aa1-137">Se observar as linhas realçadas, você pode ver qual é a aparência de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="71aa1-137">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="71aa1-138">Mais uma vez, trata-se apenas de uma sintaxe **muito** conveniente para usar delegados, de modo que o que acontece nos bastidores é semelhante ao que acontece com o delegado anônimo.</span><span class="sxs-lookup"><span data-stu-id="71aa1-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="71aa1-139">Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o trecho de código a seguir ilustra.</span><span class="sxs-lookup"><span data-stu-id="71aa1-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

## <a name="further-reading-and-resources"></a><span data-ttu-id="71aa1-140">Recursos e leituras adicionais</span><span class="sxs-lookup"><span data-stu-id="71aa1-140">Further reading and resources</span></span>

*   [<span data-ttu-id="71aa1-141">Delegados</span><span class="sxs-lookup"><span data-stu-id="71aa1-141">Delegates</span></span>](https://msdn.microsoft.com/library/ms173171.aspx)
*   [<span data-ttu-id="71aa1-142">Funções Anônimas</span><span class="sxs-lookup"><span data-stu-id="71aa1-142">Anonymous Functions</span></span>](https://msdn.microsoft.com/library/bb882516.aspx)
*   [<span data-ttu-id="71aa1-143">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="71aa1-143">Lambda expressions</span></span>](https://msdn.microsoft.com/library/bb397687.aspx)

