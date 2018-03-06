---
title: "Tutorial sobre cadeias de caracteres interpoladas – guias de início rápido de C#"
description: "Neste guia de início rápido sobre cadeias de caracteres interpoladas, você escreve código em C# para incluir o resultado de uma expressão em uma cadeia de caracteres maior."
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: b6089b69eb350fce29f86f19f5abeb44acb4b6b4
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="interpolated-strings"></a>Cadeias de caracteres interpoladas

Este guia de início rápido ensina como usar cadeias de caracteres interpoladas em C# para inserir valores em uma única cadeia de caracteres de saída. Escreva o código em C# e veja os resultados da compilação e da execução. O início rápido contém uma série de lições que inserem valores em cadeias de caracteres e formatam esses valores de diferentes maneiras.

Este início rápido espera que você tenha um computador que possa usar para desenvolvimento. O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux. Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes. 

## <a name="create-an-interpolated-string"></a>Criar uma cadeia de caracteres interpolada

Crie um diretório chamado **interpolated-quickstart**. Faça com que esse seja o diretório atual e execute o seguinte comando em uma janela do console:

```console
dotnet new console -n interpolated -o .
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

Vamos experimentar mais alguns exemplos de cadeia de caracteres interpolados com outros tipos de dados.
    
## <a name="include-different-data-types"></a>Incluir diferentes tipos de dados

Na seção anterior, você usou uma cadeia de caracteres interpolada para inserir uma cadeia de caracteres dentro de outra. No entanto, uma expressão de cadeia de caracteres interpolada pode ser de qualquer tipo de dados. Vamos experimentar uma cadeia de caracteres interpolada com valores de vários tipos de dados. 
    
O exemplo a seguir inclui expressões interpoladas com um objeto `Vegetable`, um membro da enumeração `Unit`, um valor <xref:System.DateTime> e um valor <xref:System.Decimal>. Substitua todo o código C# em seu editor pelo seguinte código e, depois, use o comando `console run` para executá-lo:

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
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
    
Observe que a segunda expressão interpolada inclui o objeto `item` na cadeia de caracteres de resultado que é exibida no console e, nesse caso, a cadeia de caracteres "eggplant" é inserida na cadeia de caracteres de resultado. Isso ocorre porque, quando o tipo de uma expressão interpolada não é uma cadeia de caracteres, o compilador do C# faz o seguinte:

- Se a expressão interpolada é `null`, a expressão interpolada retorna uma cadeia de caracteres vazia ("" ou <xref:System.String.Empty?displayProperty=nameWithType>).

- Se a expressão interpolada não é `null`, o método `ToString` do tipo da expressão interpolada é chamado. Você pode testar isso comentando a definição do método `Vegetable.ToString` no exemplo, colocando um símbolo de comentário (`//`) na frente dele. Na saída, a cadeia de caracteres "eggplant" é substituída pelo nome do tipo, "Vegetable", que é o comportamento padrão do método <xref:System.Object.ToString?displayProperty=nameWithType>.   

Na saída deste exemplo, a data é muito precisa (o preço de eggplant não varia por segundo) e o valor do preço não indica uma unidade monetária. Na próxima seção, você aprenderá como corrigir esses problemas controlando o formato das cadeias de caracteres retornadas pelas expressões interpoladas.

## <a name="control-the-formatting-of-interpolated-expressions"></a>Controlar a formatação de expressões interpoladas

Na seção anterior, duas cadeias de caracteres formatadas de maneira inadequada foram inseridas na cadeia de caracteres de resultado. Uma era um valor de data e hora para a qual apenas a data era adequada. A segunda era um preço que não indicava a unidade monetária. Os dois problemas são fáceis de se resolver. As expressões interpoladas podem incluir *cadeias de caracteres de formato* que controlam a formatação de tipos específicos. Modifique a chamada a `Console.WriteLine` no exemplo anterior para incluir o especificador de formato para os campos de data e de preço, conforme mostrado na linha a seguir:

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
Você especifica uma cadeia de caracteres de formato colocando dois-pontos e a cadeia de caracteres de formato após a expressão interpolada. "d" é uma [cadeia de caracteres de formato de data e hora padrão](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) que representa o formato de data abreviada. "C2" é um [cadeia de caracteres de formato numérico padrão](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) que representa um número como um valor de moeda com dois dígitos após o ponto decimal.

Diversos tipos nas bibliotecas do .NET Standard são compatíveis com um conjunto predefinido de cadeias de caracteres de formato. Isso inclui todos os tipos numéricos e os tipos de data e hora. Para obter uma lista completa dos tipos que são compatíveis com as cadeias de caracteres de formato, consulte [Cadeias de caracteres de formato e tipos da biblioteca de classes do .NET](../../standard/base-types/formatting-types.md#stringRef) no artigo [Tipos de formatação no .NET](../../standard/base-types/formatting-types.md). Qualquer tipo pode ser compatível com um conjunto de cadeias de caracteres de formato, e você também pode desenvolver extensões de formatação personalizadas que fornecem formatação personalizada para os tipos existentes. Para obter informações sobre formatação personalizada com o fornecimento de uma implementação de <xref:System.ICustomFormatter>, consulte [Formatação personalizada com ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) no artigo [Tipos de formatação no .NET](../../standard/base-types/formatting-types.md).

Tente modificar as cadeias de caracteres de formato em seu editor de texto e, sempre que fizer uma alteração, execute novamente o programa para ver como as alterações afetam a formatação da data e hora e do valor numérico. Altere o "d" em `{date:d}` para "t" (para exibir o formato de hora abreviada), para "y" (para exibir o ano e o mês) e para "yyyy" (para exibir o ano como um número de quatro dígitos). Altere o "C2" em `{price:C2}` para "e" (para obter notação exponencial) e para "F3" (para um valor numérico com três dígitos após o ponto decimal).

Além de controlar a formatação, você também pode controlar a largura do campo e o alinhamento das cadeias de caracteres retornadas por uma expressão interpolada. Na próxima seção, você aprenderá como fazer isso.

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>Controlar a largura do campo e o alinhamento de expressões interpoladas

Normalmente, quando a cadeia de caracteres retornada por uma expressão interpolada é incluída em uma cadeia de caracteres de resultado, ela não tem espaços à esquerda nem à direita. Especialmente para casos em que você esteja trabalhando com um conjunto de dados, as expressões interpoladas permitem que você especifique uma largura de campo e seu alinhamento. Para ver isso, substitua todo o código em seu editor de texto pelo código a seguir e, em seguida, digite `console run` para executar o programa:
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
Os nomes de autores são alinhados à esquerda e os títulos que eles escreveram são alinhados à direita. Você especifica o alinhamento adicionando uma vírgula (",") após a expressão e designando a largura do campo. Se a largura do campo for um número positivo, o campo será alinhado à direita:

```text
{expression, width}
```

Se a largura do campo for um número negativo, o campo será alinhado à esquerda:

```text
{expression, -width}
```

Tente remover os sinais negativos das expressões interpoladas `{"Author",-25}` e `{title.Key,-25}` e execute o exemplo novamente, como feito no código a seguir:

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

Desta vez, as informações sobre o autor são alinhadas à direita.

Você pode combinar uma largura de campo e uma cadeia de caracteres de formato em uma única expressão interpolada. A largura do campo vem primeiro, seguida por dois-pontos e a cadeia de caracteres de formato. Substitua todo o código dentro do método `Main` pelo código a seguir, que exibe três cadeias de caracteres formatadas com larguras de campo definidas. Em seguida, execute o programa inserindo o comando `dotnet run`.

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
A saída é semelhante ao seguinte:

```console
1/11/2018            Hour 09                1,063.34 feet
```

Você concluiu o guia de início rápido de cadeias de caracteres interpoladas. 
    
Continue com o início rápido [Matrizes e coleções](arrays-and-collections.md) em seu próprio ambiente de desenvolvimento.

Você pode aprender mais sobre como trabalhar com cadeias de caracteres interpoladas no tópico [Cadeias de caracteres interpoladas](../language-reference/keywords/interpolated-strings.md) na referência do C#.

