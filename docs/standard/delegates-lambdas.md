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
# <a name="delegates-and-lambdas"></a>Delegados e lambdas

Os delegados definem um tipo que especifica uma assinatura de método específica. Um método (estático ou instância) que satisfaz essa assinatura pode ser atribuído a uma variável desse tipo, que então é chamada diretamente (com os argumentos apropriados) ou passada como um argumento para outro método e, então, chamada. O exemplo a seguir demonstra o uso de um delegado.

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

Para simplificar o processo de desenvolvimento, o .NET inclui um conjunto de tipos de delegados que os programadores podem reutilizar, sem precisar criar novos tipos. Esses tipos `Func<>` `Action<>` são `Predicate<>`, e , e podem ser usados sem ter que definir novos tipos de delegados. Existem algumas diferenças entre os três tipos que têm a ver com a forma como foram destinados a serem usados:

* `Action<>` é usado quando é necessário executar uma ação usando os argumentos do delegado. O método que encapsula não retorna um valor.
* `Func<>` é normalmente é usado quando você tem uma transformação à mão, ou seja, quando é necessário transformar os argumentos do delegado em um resultado diferente. Projeções são um bom exemplo. O método que encapsula retorna um valor especificado.
* `Predicate<>` é usado quando você precisa determinar se o argumento satisfaz a condição do delegado. Também pode ser escrito `Func<T, bool>`como um , o que significa que o método retorna um valor booleano.

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

Para este exemplo simples, ter um método definido fora do método `Main` parece um pouco supérfluo. .NET Framework 2.0 introduziu o conceito de *delegados anônimos,* que permitem criar delegados "inline" sem ter que especificar qualquer tipo ou método adicional.

No exemplo a seguir, um delegado anônimo filtra uma lista apenas para os números pares e, em seguida, imprime-os para o console.

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

Como você pode ver, o corpo do delegado é apenas um conjunto de expressões, como aconteceria com qualquer outro delegado. Mas em vez de ser uma definição separada, nós introduzimos _ad hoc_ em nossa chamada para o <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> método.

No entanto, mesmo com essa abordagem, ainda há muito código que podemos descartar. É aí que as *expressões lambda* entram em cena. Expressões lambda, ou apenas "lambdas" para abreviar, foram introduzidas em C# 3.0 como um dos principais blocos de construção da Linguagem Integrada Query (LINQ). Elas são apenas uma sintaxe mais conveniente para usar delegados. Eles declaram uma assinatura e um corpo de método, mas não têm uma identidade formal própria, a menos que sejam designados para um delegado. Ao contrário dos representantes, elas podem ser atribuídas diretamente como o lado esquerdo do registro de eventos ou em várias cláusulas e métodos LINQ.

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

No exemplo anterior, a expressão lambda usada é `i => i % 2 == 0`. Novamente, é apenas uma sintaxe conveniente para o uso de delegados. O que acontece sob as cobertas é semelhante ao que acontece com o delegado anônimo.

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

O operador `+=` nesse contexto é usado para assinar um [evento](../../docs/csharp/language-reference/keywords/event.md). Para obter mais informações, consulte [Como se inscrever e cancelar a inscrição de eventos](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Recursos e leituras adicionais

* [Delegados](../../docs/csharp/programming-guide/delegates/index.md)
* [Funções Anônimas](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Expressões lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
