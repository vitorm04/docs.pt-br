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
ms.openlocfilehash: 3cd9fc23dba104f92255b031eef32f80cca915b0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="76800-103">Cadeias de caracteres interpoladas</span><span class="sxs-lookup"><span data-stu-id="76800-103">Interpolated strings</span></span>

<span data-ttu-id="76800-104">Este guia de início rápido ensina como usar cadeias de caracteres interpoladas em C# para inserir valores em uma única cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="76800-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="76800-105">Escreva o código em C# e veja os resultados da compilação e da execução.</span><span class="sxs-lookup"><span data-stu-id="76800-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="76800-106">O início rápido contém uma série de lições que inserem valores em cadeias de caracteres e formatam esses valores de diferentes maneiras.</span><span class="sxs-lookup"><span data-stu-id="76800-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="76800-107">Este início rápido espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="76800-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="76800-108">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="76800-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="76800-109">Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="76800-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="76800-110">Criar uma cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="76800-110">Create an interpolated string</span></span>

<span data-ttu-id="76800-111">Crie um diretório chamado **interpolated-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="76800-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="76800-112">Faça com que esse seja o diretório atual e execute o seguinte comando em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="76800-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="76800-113">Esse comando cria um novo aplicativo de console .NET Core no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="76800-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="76800-114">Abra **Program.cs** em seu editor favorito e substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código, em que você substitui `<name>` pelo seu nome:</span><span class="sxs-lookup"><span data-stu-id="76800-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="76800-115">Experimente este código digitando `dotnet run` na sua janela do console.</span><span class="sxs-lookup"><span data-stu-id="76800-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="76800-116">Ao executar o programa, ele exibe uma única cadeia de caracteres que inclui seu nome na saudação.</span><span class="sxs-lookup"><span data-stu-id="76800-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="76800-117">A cadeia de caracteres incluída na chamada de método <xref:System.Console.WriteLine%2A> é uma *cadeia de caracteres interpolada*.</span><span class="sxs-lookup"><span data-stu-id="76800-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="76800-118">Ela é um tipo de modelo que permite que você construa uma única cadeia de caracteres (chamado de *cadeia de caracteres de resultado*) com base em uma cadeia de caracteres que inclui o código inserido.</span><span class="sxs-lookup"><span data-stu-id="76800-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="76800-119">As cadeias de caracteres interpoladas são particularmente úteis para inserir valores em uma cadeia de caracteres ou para concatenar (unir) cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="76800-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="76800-120">Esse exemplo simples contém os dois elementos que toda cadeia de caracteres interpolada deve ter:</span><span class="sxs-lookup"><span data-stu-id="76800-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="76800-121">Um literal de cadeia de caracteres que começa com o caractere `$` antes do caractere de aspas de abertura.</span><span class="sxs-lookup"><span data-stu-id="76800-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="76800-122">Não pode haver nenhum espaço entre o símbolo `$` e o caractere de aspas.</span><span class="sxs-lookup"><span data-stu-id="76800-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="76800-123">(Se você quiser ver o que acontece ao incluir um espaço, insira um após o caractere `$`, salve o arquivo e execute novamente o programa, digitando `dotnet run` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="76800-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="76800-124">O compilador do C# exibirá uma mensagem de erro "Erro CS1056: caractere '$' inesperado".)</span><span class="sxs-lookup"><span data-stu-id="76800-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="76800-125">Uma ou mais *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="76800-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="76800-126">Uma expressão interpolada é indicada por chaves de abertura e fechamento (`{` e `}`).</span><span class="sxs-lookup"><span data-stu-id="76800-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="76800-127">Você pode colocar qualquer expressão de C# que retorne um valor (incluindo `null`) dentro das chaves.</span><span class="sxs-lookup"><span data-stu-id="76800-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="76800-128">Vamos experimentar mais alguns exemplos de cadeia de caracteres interpolados com outros tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="76800-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="76800-129">Incluir diferentes tipos de dados</span><span class="sxs-lookup"><span data-stu-id="76800-129">Include different data types</span></span>

<span data-ttu-id="76800-130">Na seção anterior, você usou uma cadeia de caracteres interpolada para inserir uma cadeia de caracteres dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="76800-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="76800-131">No entanto, uma expressão de cadeia de caracteres interpolada pode ser de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="76800-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="76800-132">Vamos experimentar uma cadeia de caracteres interpolada com valores de vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="76800-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="76800-133">O exemplo a seguir inclui expressões interpoladas com um objeto `Vegetable`, um membro da enumeração `Unit`, um valor <xref:System.DateTime> e um valor <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="76800-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="76800-134">Substitua todo o código C# em seu editor pelo seguinte código e, depois, use o comando `console run` para executá-lo:</span><span class="sxs-lookup"><span data-stu-id="76800-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

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
    
<span data-ttu-id="76800-135">Observe que a segunda expressão interpolada inclui o objeto `item` na cadeia de caracteres de resultado que é exibida no console e, nesse caso, a cadeia de caracteres "eggplant" é inserida na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="76800-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="76800-136">Isso ocorre porque, quando o tipo de uma expressão interpolada não é uma cadeia de caracteres, o compilador do C# faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="76800-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="76800-137">Se a expressão interpolada é `null`, a expressão interpolada retorna uma cadeia de caracteres vazia ("" ou <xref:System.String.Empty?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="76800-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="76800-138">Se a expressão interpolada não é `null`, o método `ToString` do tipo da expressão interpolada é chamado.</span><span class="sxs-lookup"><span data-stu-id="76800-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="76800-139">Você pode testar isso comentando a definição do método `Vegetable.ToString` no exemplo, colocando um símbolo de comentário (`//`) na frente dele.</span><span class="sxs-lookup"><span data-stu-id="76800-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="76800-140">Na saída, a cadeia de caracteres "eggplant" é substituída pelo nome do tipo, "Vegetable", que é o comportamento padrão do método <xref:System.Object.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76800-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="76800-141">Na saída deste exemplo, a data é muito precisa (o preço de eggplant não varia por segundo) e o valor do preço não indica uma unidade monetária.</span><span class="sxs-lookup"><span data-stu-id="76800-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="76800-142">Na próxima seção, você aprenderá como corrigir esses problemas controlando o formato das cadeias de caracteres retornadas pelas expressões interpoladas.</span><span class="sxs-lookup"><span data-stu-id="76800-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="76800-143">Controlar a formatação de expressões interpoladas</span><span class="sxs-lookup"><span data-stu-id="76800-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="76800-144">Na seção anterior, duas cadeias de caracteres formatadas de maneira inadequada foram inseridas na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="76800-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="76800-145">Uma era um valor de data e hora para a qual apenas a data era adequada.</span><span class="sxs-lookup"><span data-stu-id="76800-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="76800-146">A segunda era um preço que não indicava a unidade monetária.</span><span class="sxs-lookup"><span data-stu-id="76800-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="76800-147">Os dois problemas são fáceis de se resolver.</span><span class="sxs-lookup"><span data-stu-id="76800-147">Both issues are easy to address.</span></span> <span data-ttu-id="76800-148">As expressões interpoladas podem incluir *cadeias de caracteres de formato* que controlam a formatação de tipos específicos.</span><span class="sxs-lookup"><span data-stu-id="76800-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="76800-149">Modifique a chamada a `Console.WriteLine` no exemplo anterior para incluir o especificador de formato para os campos de data e de preço, conforme mostrado na linha a seguir:</span><span class="sxs-lookup"><span data-stu-id="76800-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="76800-150">Você especifica uma cadeia de caracteres de formato colocando dois-pontos e a cadeia de caracteres de formato após a expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="76800-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="76800-151">"d" é uma [cadeia de caracteres de formato de data e hora padrão](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) que representa o formato de data abreviada.</span><span class="sxs-lookup"><span data-stu-id="76800-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="76800-152">"C2" é um [cadeia de caracteres de formato numérico padrão](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) que representa um número como um valor de moeda com dois dígitos após o ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="76800-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="76800-153">Diversos tipos nas bibliotecas do .NET Standard são compatíveis com um conjunto predefinido de cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="76800-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="76800-154">Isso inclui todos os tipos numéricos e os tipos de data e hora.</span><span class="sxs-lookup"><span data-stu-id="76800-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="76800-155">Para obter uma lista completa dos tipos que são compatíveis com as cadeias de caracteres de formato, consulte [Cadeias de caracteres de formato e tipos da biblioteca de classes do .NET](../../standard/base-types/formatting-types.md#stringRef) no artigo [Tipos de formatação no .NET](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="76800-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="76800-156">Qualquer tipo pode ser compatível com um conjunto de cadeias de caracteres de formato, e você também pode desenvolver extensões de formatação personalizadas que fornecem formatação personalizada para os tipos existentes.</span><span class="sxs-lookup"><span data-stu-id="76800-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="76800-157">Para obter informações sobre formatação personalizada com o fornecimento de uma implementação de <xref:System.ICustomFormatter>, consulte [Formatação personalizada com ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) no artigo [Tipos de formatação no .NET](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="76800-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="76800-158">Tente modificar as cadeias de caracteres de formato em seu editor de texto e, sempre que fizer uma alteração, execute novamente o programa para ver como as alterações afetam a formatação da data e a hora e do valor numérico.</span><span class="sxs-lookup"><span data-stu-id="76800-158">Try modifying the the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="76800-159">Altere o "d" em `{date:d}` para "t" (para exibir o formato de hora abreviada), para "y" (para exibir o ano e o mês) e para "yyyy" (para exibir o ano como um número de quatro dígitos).</span><span class="sxs-lookup"><span data-stu-id="76800-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="76800-160">Altere o "C2" em `{price:C2}` para "e" (para obter notação exponencial) e para "F3" (para um valor numérico com três dígitos após o ponto decimal).</span><span class="sxs-lookup"><span data-stu-id="76800-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="76800-161">Além de controlar a formatação, você também pode controlar a largura do campo e o alinhamento das cadeias de caracteres retornadas por uma expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="76800-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="76800-162">Na próxima seção, você aprenderá como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="76800-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="76800-163">Controlar a largura do campo e o alinhamento de expressões interpoladas</span><span class="sxs-lookup"><span data-stu-id="76800-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="76800-164">Normalmente, quando a cadeia de caracteres retornada por uma expressão interpolada é incluída em uma cadeia de caracteres de resultado, ela não tem espaços à esquerda nem à direita.</span><span class="sxs-lookup"><span data-stu-id="76800-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="76800-165">Especialmente para casos em que você esteja trabalhando com um conjunto de dados, as expressões interpoladas permitem que você especifique uma largura de campo e seu alinhamento.</span><span class="sxs-lookup"><span data-stu-id="76800-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="76800-166">Para ver isso, substitua todo o código em seu editor de texto pelo código a seguir e, em seguida, digite `console run` para executar o programa:</span><span class="sxs-lookup"><span data-stu-id="76800-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
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
    
<span data-ttu-id="76800-167">Os nomes de autores são alinhados à esquerda e os títulos que eles escreveram são alinhados à direita.</span><span class="sxs-lookup"><span data-stu-id="76800-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="76800-168">Você especifica o alinhamento adicionando uma vírgula (",") após a expressão e designando a largura do campo.</span><span class="sxs-lookup"><span data-stu-id="76800-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="76800-169">Se a largura do campo for um número positivo, o campo será alinhado à direita:</span><span class="sxs-lookup"><span data-stu-id="76800-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="76800-170">Se a largura do campo for um número negativo, o campo será alinhado à esquerda:</span><span class="sxs-lookup"><span data-stu-id="76800-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="76800-171">Tente remover os sinais negativos das expressões interpoladas `{"Author",-25}` e `{title.Key,-25}` e execute o exemplo novamente, como feito no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="76800-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

<span data-ttu-id="76800-172">Desta vez, as informações sobre o autor são alinhadas à direita.</span><span class="sxs-lookup"><span data-stu-id="76800-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="76800-173">Você pode combinar uma largura de campo e uma cadeia de caracteres de formato em uma única expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="76800-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="76800-174">A largura do campo vem primeiro, seguida por dois-pontos e a cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="76800-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="76800-175">Substitua todo o código dentro do método `Main` pelo código a seguir, que exibe três cadeias de caracteres formatadas com larguras de campo definidas.</span><span class="sxs-lookup"><span data-stu-id="76800-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="76800-176">Em seguida, execute o programa inserindo o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="76800-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="76800-177">A saída é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="76800-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="76800-178">Você concluiu o guia de início rápido de cadeias de caracteres interpoladas.</span><span class="sxs-lookup"><span data-stu-id="76800-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="76800-179">Continue com o início rápido [Matrizes e coleções](arrays-and-collections.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="76800-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="76800-180">Você pode aprender mais sobre como trabalhar com cadeias de caracteres interpoladas no tópico [Cadeias de caracteres interpoladas](../language-reference/keywords/interpolated-strings.md) na referência do C#.</span><span class="sxs-lookup"><span data-stu-id="76800-180">You can learn more about working with interpolated strings in the [Interpolated Strings](../language-reference/keywords/interpolated-strings.md) topic in the C# Reference.</span></span>

