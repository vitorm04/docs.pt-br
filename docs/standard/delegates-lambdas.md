---
title: Delegados e lambdas
description: Saiba como delegados definem um tipo, que especifica a assinatura de um método específico, que pode ser chamado diretamente ou passado para outro método e, em seguida, chamado.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 3fb926683de90516bcf67d99026a0134d82cb683
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296939"
---
# <a name="delegates-and-lambdas"></a>Delegados e lambdas

Os delegados definem um tipo, que especifica uma assinatura de método específica. Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada. O exemplo a seguir demonstra o uso de um delegado.

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

* A linha `public delegate string Reverse(string s);` cria um tipo de delegado de determinada assinatura, nesse caso, um método que usa um parâmetro de cadeia de caracteres e, em seguida, retorna um parâmetro de cadeia de caracteres.
* O método `static string ReverseString(string s)`, que tem exatamente a mesma assinatura do tipo de delegado definido, implementa o delegado.
* A linha `Reverse rev = ReverseString;` mostra que você pode atribuir um método a uma variável do tipo de delegado correspondente.
* A linha `Console.WriteLine(rev("a string"));` demonstra como usar uma variável de um tipo de delegado para invocar o delegado.

Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos. Eles são `Func<>`, `Action<>` e `Predicate<>`, e podem ser usados em vários locais das APIs .NET sem a necessidade de definir novos tipos de delegado. Obviamente, há algumas diferenças entre os três, que você verá em suas assinaturas e que geralmente têm a ver com a maneira como eles deveriam ser usados:

*   `Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado.
*   `Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente. As projeções são um excelente exemplo disso.
*   `Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado. Ele também pode ser escrito como um `Func<T, bool>`.

Agora, podemos pegar nosso exemplo acima e reescrevê-lo usando o delegado `Func<>` em vez de um tipo personalizado. O programa continuará sendo executado exatamente da mesma forma.

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

Para este exemplo simples, ter um método definido fora do método `Main` parece um pouco supérfluo. É por isso que o .NET Framework 2.0 introduziu o conceito de **delegados anônimos**. Com suporte deles, você pode criar delegados "embutidos" sem precisar especificar tipos ou métodos adicionais. Você simplesmente embute a definição do delegado onde precisar dela.

Para dar um exemplo, vamos trocá-lo e usar nosso delegado anônimo para filtrar uma lista com apenas os números pares e, em seguida, imprimi-los no console.

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

Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado. Mas em vez de ele ser uma definição separada, nós o introduzimos _ad hoc_ em nossa chamada ao método <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.

No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar. É aí que as **expressões lambda** entram em cena.

As expressões lambda ou apenas "lambdas" para abreviar, foram introduzidas pela primeira vez no C# 3.0 como um dos principais elementos de construção da LINQ (Consulta integrada à linguagem). Elas são apenas uma sintaxe mais conveniente para usar delegados. Elas declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam atribuídas a um delegado. Ao contrário dos representantes, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos LINQ.

Como uma expressão lambda é apenas outra maneira de especificar um delegado, nós podemos reescrever o exemplo acima para usar uma expressão lambda em vez de um delegado anônimo.

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

No exemplo anterior, a expressão lambda usada é `i => i % 2 == 0`. Mais uma vez, trata-se apenas de uma sintaxe **muito** conveniente para usar delegados, de modo que o que acontece nos bastidores é semelhante ao que acontece com o delegado anônimo.

Novamente, as lambdas são apenas delegados, o que significa que podem ser usadas como um manipulador de eventos sem problemas, como o snippet de código a seguir ilustra.

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

*   [Delegados](../../docs/csharp/programming-guide/delegates/index.md)
*   [Funções Anônimas](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Expressões lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
