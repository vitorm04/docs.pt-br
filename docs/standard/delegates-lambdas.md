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

# <a name="delegates-and-lambdas"></a>Delegados e lambdas

Os delegados definem um tipo, que especifica uma assinatura de método específica. Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada. O exemplo a seguir demonstra o uso de um delegado.

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

*   Na linha 4, criamos um tipo de delegado de uma determinada assinatura, nesse caso um método que usa um parâmetro de cadeia de caracteres e retorna um parâmetro de cadeia de caracteres.
*   Na linha 6, definimos a implementação do delegado fornecendo um método que tem exatamente a mesma assinatura.
*   Na linha 13, o método é atribuído a um tipo que está de acordo com o delegado `Reverse`.
*   Por fim, na linha 15 invocamos o delegado passando uma cadeia de caracteres a ser revertida.

Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos. Eles são `Func<>`, `Action<>` e `Predicate<>`, e podem ser usados em vários locais das APIs .NET sem a necessidade de definir novos tipos de delegado. Obviamente, há algumas diferenças entre os três, que você verá em suas assinaturas e que geralmente têm a ver com a maneira como eles deveriam ser usados:

*   `Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.
*   `Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente. As projeções são um excelente exemplo disso.
*   `Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado. Ele também pode ser escrito como um `Func<T, bool>`.

Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado. O programa continuará sendo executado exatamente da mesma forma.

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

Para este exemplo simples, ter um método definido fora do método Main() parece um pouco supérfluo. É por isso que o .NET Framework 2.0 introduziu o conceito de **delegados anônimos**. Com suporte deles, você pode criar delegados "embutidos" sem precisar especificar tipos ou métodos adicionais. Você simplesmente embute a definição do delegado onde precisar dela.

Para dar um exemplo, vamos trocá-lo e usar nosso delegado anônimo para filtrar uma lista com apenas os números pares e, em seguida, imprimi-los no console.

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

Observe as linhas realçadas. Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado. Mas em vez dele ser uma definição separada, nós o introduzimos _ad hoc_ em nossa chamada para o método `FindAll()` do tipo `List<T>`.

No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar. É aí que as **expressões lambda** entram em cena.

As expressões lambda ou apenas "lambdas" para abreviar, foram introduzidas pela primeira vez no C# 3.0 como um dos principais elementos de construção da LINQ (Consulta integrada à linguagem). Elas são apenas uma sintaxe mais conveniente para usar delegados. Elas declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam atribuídas a um delegado. Diferente dos delegados, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos Linq.

Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.

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

Se observar as linhas realçadas, você pode ver qual é a aparência de uma expressão lambda. Mais uma vez, trata-se apenas de uma sintaxe **muito** conveniente para usar delegados, de modo que o que acontece nos bastidores é semelhante ao que acontece com o delegado anônimo.

Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o trecho de código a seguir ilustra.

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

## <a name="further-reading-and-resources"></a>Recursos e leituras adicionais

*   [Delegados](https://msdn.microsoft.com/library/ms173171.aspx)
*   [Funções Anônimas](https://msdn.microsoft.com/library/bb882516.aspx)
*   [Expressões lambda](https://msdn.microsoft.com/library/bb397687.aspx)

