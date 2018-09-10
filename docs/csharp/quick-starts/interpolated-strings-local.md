---
title: Tutorial sobre interpolação de cadeias de caracteres – guias de início rápido de C#
description: Este guia de início rápido mostra como usar o recurso de interpolação de cadeias de caracteres em C# para incluir resultados de expressão formatada em uma cadeia de caracteres maior.
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: da111790ebbc299df16297650347045b9395a90f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44206296"
---
# <a name="string-interpolation"></a>Interpolação de cadeias de caracteres

Este guia de início rápido ensina como usar a [interpolação de cadeias de caracteres](../language-reference/tokens/interpolated.md) em C# para inserir valores em uma única cadeia de caracteres de resultado. Escreva o código em C# e veja os resultados da compilação e da execução. O início rápido contém uma série de lições que mostram como inserir valores em cadeias de caracteres e formatar esses valores de diferentes maneiras.

Este início rápido espera que você tenha um computador que possa usar para desenvolvimento. O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux. Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes. Você também pode concluir a [versão interativa](interpolated-strings.yml) deste guia de início rápido em seu navegador.

## <a name="create-an-interpolated-string"></a>Criar uma cadeia de caracteres interpolada

Crie um diretório chamado **interpolated**. Faça com que esse seja o diretório atual e execute o seguinte comando em uma janela do console:

```console
dotnet new console
```

Esse comando cria um novo aplicativo de console .NET Core no diretório atual.

Abra **Program.cs** em seu editor favorito e substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código, em que você substitui `<name>` pelo seu nome:

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Experimente este código digitando `dotnet run` na sua janela do console. Ao executar o programa, ele exibe uma única cadeia de caracteres que inclui seu nome na saudação. A cadeia de caracteres incluída na chamada de método <xref:System.Console.WriteLine%2A> é uma *cadeia de caracteres interpolada*. Ela é um tipo de modelo que permite que você construa uma única cadeia de caracteres (chamado de *cadeia de caracteres de resultado*) com base em uma cadeia de caracteres que inclui o código inserido. As cadeias de caracteres interpoladas são particularmente úteis para inserir valores em uma cadeia de caracteres ou para concatenar (unir) cadeias de caracteres.

Esse exemplo simples contém os dois elementos que toda cadeia de caracteres interpolada deve ter:

- Um literal de cadeia de caracteres que começa com o caractere `$` antes do caractere de aspas de abertura. Não pode haver nenhum espaço entre o símbolo `$` e o caractere de aspas. (Se você quiser ver o que acontece ao incluir um espaço, insira um após o caractere `$`, salve o arquivo e execute novamente o programa, digitando `dotnet run` na janela do console. O compilador do C# exibirá uma mensagem de erro "Erro CS1056: caractere '$' inesperado".)

- Uma ou mais *expressões interpoladas*. Uma expressão interpolada é indicada por chaves de abertura e fechamento (`{` e `}`). Você pode colocar qualquer expressão de C# que retorne um valor (incluindo `null`) dentro das chaves.

Vamos testar mais alguns exemplos de interpolação de cadeias de caracteres com outros tipos de dados.

## <a name="include-different-data-types"></a>Incluir diferentes tipos de dados

Na seção anterior, você usou a interpolação de cadeias de caracteres para inserir uma cadeia de caracteres dentro de outra. Entretanto, o resultado de uma expressão interpolada pode ser de qualquer tipo de dados. Vamos incluir valores de vários tipos de dados em uma cadeia de caracteres interpolada.

No exemplo a seguir, primeiro, definimos um tipo de dados de [classe](../programming-guide/classes-and-structs/classes.md) `Vegetable` que tem a [propriedade](../properties.md) `Name` e o [método](../methods.md) `ToString`, que [substitui](../language-reference/keywords/override.md) o comportamento do método <xref:System.Object.ToString?displayProperty=nameWithType>. O [modificador de acesso `public`](../language-reference/keywords/public.md) disponibiliza esse método para qualquer código de cliente para obter a representação de cadeia de caracteres de uma instância de `Vegetable`. No exemplo, o método `Vegetable.ToString` retorna o valor da propriedade `Name` que é inicializada no [construtor](../programming-guide/classes-and-structs/constructors.md) `Vegetable`:

```csharp
public Vegetable(string name) => Name = name;
```

Em seguida, criamos uma instância da classe `Vegetable` usando a [palavra-chave `new`](../language-reference/keywords/new-operator.md) e fornecendo um parâmetro de nome para o construtor `Vegetable`:

```csharp
var item = new Vegetable("eggplant");
```

Por fim, incluímos a variável `item` em uma cadeia de caracteres interpolada que também contém um valor <xref:System.DateTime>, um valor <xref:System.Decimal> e um valor de [enumeração](../programming-guide/enumeration-types.md) `Unit` valor. Substitua todo o código C# em seu editor pelo seguinte código e, depois, use o comando `dotnet run` para executá-lo:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

Observe que a expressão interpolada `item` na cadeia de caracteres interpolada é resolvida como o texto "eggplant" na cadeia de caracteres de resultado. Isso ocorre porque, quando o tipo do resultado da expressão não é uma cadeia de caracteres, o resultado é resolvido como uma cadeia de caracteres da seguinte maneira:

- Se a expressão interpolada for avaliada como `null`, uma cadeia de caracteres vazia ("" ou <xref:System.String.Empty?displayProperty=nameWithType>) será usada.

- Se a expressão interpolada não foi avaliada como `null`, normalmente o método `ToString` do tipo de resultado será chamado. Você pode testar isso atualizando a implementação do método `Vegetable.ToString`. Talvez nem seja necessário implementar o método `ToString`, pois cada tipo tem algum modo de implementação desse método. Para testar isso, comente a definição do método `Vegetable.ToString` no exemplo (para isso, coloque o símbolo de comentário `//` na frente dele). Na saída, a cadeia de caracteres "eggplant" é substituída pelo nome do tipo totalmente qualificado, ("Vegetable" neste exemplo), que é o comportamento padrão do método <xref:System.Object.ToString?displayProperty=nameWithType>. O comportamento padrão do método `ToString` para um valor de enumeração é retornar a representação de cadeia de caracteres do valor.

Na saída deste exemplo, a data é muito precisa (o preço de "eggplant" não muda a cada segundo) e o valor do preço não indica uma unidade monetária. Na próxima seção, você aprenderá como corrigir esses problemas controlando o formato das representações das cadeias de caracteres dos resultados de expressão.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Controlar a formatação de expressões interpoladas

Na seção anterior, duas cadeias de caracteres formatadas de maneira inadequada foram inseridas na cadeia de caracteres de resultado. Uma era um valor de data e hora para a qual apenas a data era adequada. A segunda era um preço que não indicava a unidade monetária. Os dois problemas são fáceis de se resolver. A interpolação de cadeias de caracteres permite especificar *cadeias de caracteres de formato* que controlam a formatação de tipos específicos. Modifique a chamada a `Console.WriteLine` no exemplo anterior para incluir as cadeias de caracteres de formato para as expressões de data e de preço, conforme mostrado na linha a seguir:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Você especifica uma cadeia de caracteres de formato colocando dois-pontos (":") e a cadeia de caracteres de formato após a expressão interpolada. "d" é uma [cadeia de caracteres de formato de data e hora padrão](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) que representa o formato de data abreviada. "C2" é um [cadeia de caracteres de formato numérico padrão](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) que representa um número como um valor de moeda com dois dígitos após o ponto decimal.

Diversos tipos nas bibliotecas do .NET são compatíveis com um conjunto predefinido de cadeias de caracteres de formato. Isso inclui todos os tipos numéricos e os tipos de data e hora. Para obter uma lista completa dos tipos que são compatíveis com as cadeias de caracteres de formato, consulte [Cadeias de caracteres de formato e tipos da biblioteca de classes do .NET](../../standard/base-types/formatting-types.md#stringRef) no artigo [Tipos de formatação no .NET](../../standard/base-types/formatting-types.md).

Tente modificar as cadeias de caracteres de formato em seu editor de texto e, sempre que fizer uma alteração, execute novamente o programa para ver como as alterações afetam a formatação da data e hora e do valor numérico. Altere o "d" em `{date:d}` para "t" (para exibir o formato de hora abreviada), para "y" (para exibir o ano e o mês) e para "yyyy" (para exibir o ano como um número de quatro dígitos). Altere o "C2" em `{price:C2}` para "e" (para obter notação exponencial) e para "F3" (para um valor numérico com três dígitos após o ponto decimal).

Além de controlar a formatação, você também pode controlar a largura do campo e o alinhamento das cadeias de caracteres formatadas incluídas na cadeia de caracteres de resultado. Na próxima seção, você aprenderá como fazer isso.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Controlar a largura do campo e o alinhamento de expressões interpoladas

Normalmente, quando o resultado de uma expressão interpolada é formatado em uma cadeia de caracteres, essa cadeia de caracteres é incluída em uma cadeia de caracteres sem espaços à esquerda nem à direita. Especialmente quando você trabalha com um conjunto de dados, poder controlar a largura do campo e o alinhamento do texto ajuda a produzir uma saída mais legível. Para ver isso, substitua todo o código em seu editor de texto pelo código a seguir e, em seguida, digite `dotnet run` para executar o programa:

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

Os nomes de autores são alinhados à esquerda e os títulos que eles escreveram são alinhados à direita. Você especifica o alinhamento adicionando uma vírgula (",") após a expressão interpolada e designando a largura *mínima* do campo. Se o valor especificado for um número positivo, o campo será alinhado à direita. Se for um número negativo, o campo será alinhado à esquerda.

Tente remover os sinais negativos do código `{"Author",-25}` e `{title.Key,-25}` e execute o exemplo novamente, como feito no código a seguir:

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Desta vez, as informações sobre o autor são alinhadas à direita.

Você pode combinar um especificador de alinhamento e uma cadeia de caracteres de formato em uma única expressão interpolada. Para fazer isso, especifique o alinhamento primeiro, seguido por dois-pontos e pela cadeia de caracteres de formato. Substitua todo o código dentro do método `Main` pelo código a seguir, que exibe três cadeias de caracteres formatadas com larguras de campo definidas. Em seguida, execute o programa inserindo o comando `dotnet run`.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

A saída é semelhante ao seguinte:

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Você concluiu o guia de início rápido de interpolação de cadeias de caracteres.

Continue com o início rápido [Coleção de lista](arrays-and-collections.md) em seu próprio ambiente de desenvolvimento.

Para obter mais informações, confira o tópico [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) e o tutorial [Interpolação de cadeia de caracteres no C#](../tutorials/string-interpolation.md).
