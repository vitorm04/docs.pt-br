---
title: Tutorial de coleções ‒ guias de início rápido locais de C#
description: Aprenda C# explorando a Coleção de lista neste tutorial.
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 88471c5fc60178c058f121ba5e5703999ad61030
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="c-quickstart-collections"></a>Início rápido do C#: coleções

Este início rápido fornece uma introdução à linguagem C# e aos conceitos básicos da classe <xref:System.Collections.Generic.List%601>.

Este início rápido espera que você tenha um computador que possa usar para desenvolvimento. O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux. Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes.

## <a name="a-basic-list-example"></a>Um exemplo de lista básica

Crie um diretório denominado **list-quickstart**. Torne-o o diretório atual e execute `dotnet new console`.

> [!NOTE]
> Se você acabou de concluir [Introdução ao .NET em 10 minutos](https://www.microsoft.com/net), continue usando o aplicativo myApp que você acabou de criar.

Abra **Program.cs** em seu editor favorito e substitua o código existente pelo seguinte:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

Substitua `<name>` pelo seu nome. Salve **Program.cs**. Digite `dotnet run` na janela de console para testá-lo.

Você criou uma lista de cadeias de caracteres, adicionou três nomes a essa lista e imprimiu os nomes em MAIÚSCULAS. Você está usando conceitos que aprendeu em inícios rápidos anteriores para executar um loop pela lista.

O código para exibir nomes utiliza o recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md).  Quando você precede um `string` com o caractere `$`, pode inserir o código C# na declaração da cadeia de caracteres. A cadeia de caracteres real substitui esse código C# pelo valor gerado. Neste exemplo, ela substitui o `{name.ToUpper()}` por cada nome, convertido em letras maiúsculas, pois você chamou o método <xref:System.String.ToUpper%2A>.

Vamos continuar explorando.

## <a name="modify-list-contents"></a>Modificar conteúdo da lista

A coleção que você criou usa o tipo <xref:System.Collections.Generic.List%601>. Esse tipo armazena sequências de elementos. Especifique o tipo dos elementos entre os colchetes.

Um aspecto importante desse tipo <xref:System.Collections.Generic.List%601> é que ele pode aumentar ou diminuir, permitindo que você adicione ou remova elementos. Adicione este código antes do `}` de fechamento no método `Main`:

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Você adicionou mais dois nomes ao final da lista. Também removeu um. Salve o arquivo e digite `dotnet run` para testá-lo.

O <xref:System.Collections.Generic.List%601> também permite fazer referência a itens individuais por **índice**. Coloque o índice entre os tokens `[` e `]` após o nome da lista. C# usa 0 para o primeiro índice. Adicione este código diretamente abaixo do código que você acabou de adicionar e teste-o:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Você não pode acessar um índice além do fim da lista. Lembre-se de que os índices começam com 0, portanto, o maior índice válido é uma unidade a menos do que o número de itens na lista. Você pode verificar há quanto tempo a lista está usando a propriedade <xref:System.Collections.Generic.List%601.Count%2A>. Adicione o código a seguir ao final do método Main:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Salve o arquivo e digite `dotnet run` novamente para ver os resultados.

## <a name="search-and-sort-lists"></a>Pesquisar e classificar listas

Nossos exemplos usam listas relativamente pequenas, mas seus aplicativos podem criar listas com muitos outros elementos, chegando, às vezes, a milhares. Para localizar elementos nessas coleções maiores, pesquise por itens diferentes na lista. O método <xref:System.Collections.Generic.List%601.IndexOf%2A> procura um item e retorna o índice do item. Adicione este código à parte inferior de seu método `Main`:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Os itens em sua lista também podem ser classificados. O método <xref:System.Collections.Generic.List%601.Sort%2A> classifica todos os itens na lista na ordem normal (em ordem alfabética, no caso de cadeias de caracteres). Adicione este código à parte inferior de nosso método `Main`:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Salve o arquivo e digite `dotnet run` para experimentar a versão mais recente.

Antes de iniciar a próxima seção, vamos passar o código atual para um método separado. Isso facilita o começo do trabalho com um exemplo novo. Renomeie seu método `Main` como `WorkingWithStrings` e escreva um novo método `Main` que chama `WorkingWithStrings`. Quando você terminar, seu código deverá parecer com isto:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>Listas de outros tipos

Você usou o tipo `string` nas listas até o momento. Vamos fazer <xref:System.Collections.Generic.List%601> usar um tipo diferente. Vamos compilar um conjunto de números.

Adicione o seguinte à parte inferior do novo método `Main`:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Isso cria uma lista de números inteiros e define os primeiros dois inteiros como o valor 1. Estes são os dois primeiros valores de uma *sequência Fibonacci*, uma sequência de números. Cada número Fibonacci seguinte é encontrado considerando a soma dos dois números anteriores. Adicione este código:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Salve o arquivo e digite `dotnet run` para ver os resultados.

> [!TIP]
> Para se concentrar apenas nesta seção, comente o código que chama `WorkingWithStrings();`. Coloque apenas dois caracteres `/` na frente da chamada, desta forma: `// WorkingWithStrings();`.

## <a name="challenge"></a>Desafio

Veja se você consegue combinar alguns dos conceitos desta lição e de lições anteriores. Expanda o que você compilou até o momento com números Fibonacci. Tente escrever o código para gerar os 20 primeiros números na sequência. (Como uma dica, o vigésimo número Fibonacci é 6765.)

## <a name="complete-challenge"></a>Desafio concluído

Veja um exemplo de solução [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)

Com cada iteração do loop, você está pegando os últimos dois inteiros na lista, somando-os e adicionando esse valor à lista. O loop será repetido até que você tenha adicionado 20 itens à lista.

Parabéns, você concluiu o início rápido de lista. Continue com o início rápido [Introdução às classes](introduction-to-classes.md) em seu próprio ambiente de desenvolvimento.

Saiba mais sobre como trabalhar com o tipo `List` no tópico [Guia de .NET](../../standard/index.md) em [coleções](../../standard/collections/index.md). Você também aprenderá muitos outros tipos de coleção.