---
title: Interpolação de cadeia de caracteres – tutorial de C#
description: Este tutorial mostra como usar o recurso de interpolação de cadeias de caracteres em C# para incluir resultados de expressão formatada em uma cadeia de caracteres maior.
author: rpetrusha
ms.author: ronpet
ms.date: 10/23/2018
ms.openlocfilehash: 7308254ec691df6ec2d5b54d3770afb825886e29
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198560"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="b38be-103">Usar interpolação de cadeia de caracteres para construir cadeia de caracteres formatadas</span><span class="sxs-lookup"><span data-stu-id="b38be-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="b38be-104">Este tutorial ensina como usar a [interpolação de cadeias de caracteres](../../language-reference/tokens/interpolated.md) em C# para inserir valores em uma única cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="b38be-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="b38be-105">Escreva o código em C# e veja os resultados da compilação e da execução.</span><span class="sxs-lookup"><span data-stu-id="b38be-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="b38be-106">O tutorial contém uma série de lições que mostram como inserir valores em uma cadeia de caracteres e formatar esses valores de diferentes maneiras.</span><span class="sxs-lookup"><span data-stu-id="b38be-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="b38be-107">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b38be-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="b38be-108">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="b38be-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="b38be-109">Uma breve visão geral dos comandos que você usará pode ser encontrada [introdução aos tutoriais locais](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="b38be-109">A quick overview of the commands you'll use is in [introduction to the local tutorials](local-environment.md), with links to more details.</span></span> <span data-ttu-id="b38be-110">Você também pode concluir a [versão interativa](interpolated-strings.yml) deste tutorial em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="b38be-110">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="b38be-111">Criar uma cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="b38be-111">Create an interpolated string</span></span>

<span data-ttu-id="b38be-112">Crie um diretório chamado **interpolated**.</span><span class="sxs-lookup"><span data-stu-id="b38be-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="b38be-113">Faça com que esse seja o diretório atual e execute o seguinte comando em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="b38be-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="b38be-114">Esse comando cria um novo aplicativo de console .NET Core no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b38be-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="b38be-115">Abra **Program.cs** em seu editor favorito e substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código, em que você substitui `<name>` pelo seu nome:</span><span class="sxs-lookup"><span data-stu-id="b38be-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="b38be-116">Experimente este código digitando `dotnet run` na sua janela do console.</span><span class="sxs-lookup"><span data-stu-id="b38be-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="b38be-117">Ao executar o programa, ele exibe uma única cadeia de caracteres que inclui seu nome na saudação.</span><span class="sxs-lookup"><span data-stu-id="b38be-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="b38be-118">A cadeia de caracteres incluída na chamada de método <xref:System.Console.WriteLine%2A> é uma *cadeia de caracteres interpolada*.</span><span class="sxs-lookup"><span data-stu-id="b38be-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="b38be-119">Ela é um tipo de modelo que permite que você construa uma única cadeia de caracteres (chamado de *cadeia de caracteres de resultado*) com base em uma cadeia de caracteres que inclui o código inserido.</span><span class="sxs-lookup"><span data-stu-id="b38be-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="b38be-120">As cadeias de caracteres interpoladas são particularmente úteis para inserir valores em uma cadeia de caracteres ou para concatenar (unir) cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b38be-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="b38be-121">Esse exemplo simples contém os dois elementos que toda cadeia de caracteres interpolada deve ter:</span><span class="sxs-lookup"><span data-stu-id="b38be-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="b38be-122">Um literal de cadeia de caracteres que começa com o caractere `$` antes do caractere de aspas de abertura.</span><span class="sxs-lookup"><span data-stu-id="b38be-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="b38be-123">Não pode haver nenhum espaço entre o símbolo `$` e o caractere de aspas.</span><span class="sxs-lookup"><span data-stu-id="b38be-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="b38be-124">(Se você quiser ver o que acontece ao incluir um espaço, insira um após o caractere `$`, salve o arquivo e execute novamente o programa, digitando `dotnet run` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="b38be-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="b38be-125">O compilador do C# exibirá uma mensagem de erro "Erro CS1056: caractere '$' inesperado".)</span><span class="sxs-lookup"><span data-stu-id="b38be-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="b38be-126">Uma ou mais *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="b38be-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="b38be-127">Uma expressão interpolada é indicada por chaves de abertura e fechamento (`{` e `}`).</span><span class="sxs-lookup"><span data-stu-id="b38be-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="b38be-128">Você pode colocar qualquer expressão de C# que retorne um valor (incluindo `null`) dentro das chaves.</span><span class="sxs-lookup"><span data-stu-id="b38be-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="b38be-129">Vamos testar mais alguns exemplos de interpolação de cadeias de caracteres com outros tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="b38be-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="b38be-130">Incluir diferentes tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b38be-130">Include different data types</span></span>

<span data-ttu-id="b38be-131">Na seção anterior, você usou a interpolação de cadeias de caracteres para inserir uma cadeia de caracteres dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="b38be-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="b38be-132">Entretanto, o resultado de uma expressão interpolada pode ser de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b38be-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="b38be-133">Vamos incluir valores de vários tipos de dados em uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="b38be-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="b38be-134">No exemplo a seguir, primeiramente definimos um tipo de dados de [classe](../../programming-guide/classes-and-structs/classes.md) `Vegetable` que tem uma [propriedade](../../properties.md) `Name` e um [método](../../methods.md) `ToString`, que [substitui](../../language-reference/keywords/override.md) o comportamento do método <xref:System.Object.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b38be-134">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b38be-135">O [modificador de acesso `public`](../../language-reference/keywords/public.md) disponibiliza esse método para qualquer código de cliente para obter a representação de cadeia de caracteres de uma instância de `Vegetable`.</span><span class="sxs-lookup"><span data-stu-id="b38be-135">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="b38be-136">No exemplo, o método `Vegetable.ToString` retorna o valor da propriedade `Name` que é inicializada no [construtor](../../programming-guide/classes-and-structs/constructors.md) `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="b38be-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="b38be-137">Em seguida, criamos uma instância da classe `Vegetable` chamada `item` usando a [palavra-chave `new`](../../language-reference/keywords/new-operator.md) e fornecendo um nome para o construtor `Vegetable`:</span><span class="sxs-lookup"><span data-stu-id="b38be-137">Then we create an instance of the `Vegetable` class named `item` by using the [`new` keyword](../../language-reference/keywords/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="b38be-138">Por fim, incluímos a variável `item` em uma cadeia de caracteres interpolada que também contém um valor <xref:System.DateTime>, um valor <xref:System.Decimal> e um valor de [enumeração](../../programming-guide/enumeration-types.md) `Unit` valor.</span><span class="sxs-lookup"><span data-stu-id="b38be-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="b38be-139">Substitua todo o código C# em seu editor pelo seguinte código e, depois, use o comando `dotnet run` para executá-lo:</span><span class="sxs-lookup"><span data-stu-id="b38be-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

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

<span data-ttu-id="b38be-140">Observe que a expressão interpolada `item` na cadeia de caracteres interpolada é resolvida como o texto "eggplant" na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="b38be-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="b38be-141">Isso ocorre porque, quando o tipo do resultado da expressão não é uma cadeia de caracteres, o resultado é resolvido como uma cadeia de caracteres da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b38be-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="b38be-142">Se a expressão interpolada for avaliada como `null`, uma cadeia de caracteres vazia ("" ou <xref:System.String.Empty?displayProperty=nameWithType>) será usada.</span><span class="sxs-lookup"><span data-stu-id="b38be-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="b38be-143">Se a expressão interpolada não foi avaliada como `null`, normalmente o método `ToString` do tipo de resultado será chamado.</span><span class="sxs-lookup"><span data-stu-id="b38be-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="b38be-144">Você pode testar isso atualizando a implementação do método `Vegetable.ToString`.</span><span class="sxs-lookup"><span data-stu-id="b38be-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="b38be-145">Talvez nem seja necessário implementar o método `ToString`, pois cada tipo tem algum modo de implementação desse método.</span><span class="sxs-lookup"><span data-stu-id="b38be-145">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="b38be-146">Para testar isso, comente a definição do método `Vegetable.ToString` no exemplo (para isso, coloque o símbolo de comentário `//` na frente dele).</span><span class="sxs-lookup"><span data-stu-id="b38be-146">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="b38be-147">Na saída, a cadeia de caracteres "eggplant" é substituída pelo nome do tipo totalmente qualificado, ("Vegetable" neste exemplo), que é o comportamento padrão do método <xref:System.Object.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b38be-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b38be-148">O comportamento padrão do método `ToString` para um valor de enumeração é retornar a representação de cadeia de caracteres do valor.</span><span class="sxs-lookup"><span data-stu-id="b38be-148">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="b38be-149">Na saída deste exemplo, a data é muito precisa (o preço de "eggplant" não muda a cada segundo) e o valor do preço não indica uma unidade monetária.</span><span class="sxs-lookup"><span data-stu-id="b38be-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="b38be-150">Na próxima seção, você aprenderá como corrigir esses problemas controlando o formato das representações das cadeias de caracteres dos resultados de expressão.</span><span class="sxs-lookup"><span data-stu-id="b38be-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="b38be-151">Controlar a formatação de expressões interpoladas</span><span class="sxs-lookup"><span data-stu-id="b38be-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="b38be-152">Na seção anterior, duas cadeias de caracteres formatadas de maneira inadequada foram inseridas na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="b38be-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="b38be-153">Uma era um valor de data e hora para a qual apenas a data era adequada.</span><span class="sxs-lookup"><span data-stu-id="b38be-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="b38be-154">A segunda era um preço que não indicava a unidade monetária.</span><span class="sxs-lookup"><span data-stu-id="b38be-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="b38be-155">Os dois problemas são fáceis de se resolver.</span><span class="sxs-lookup"><span data-stu-id="b38be-155">Both issues are easy to address.</span></span> <span data-ttu-id="b38be-156">A interpolação de cadeias de caracteres permite especificar *cadeias de caracteres de formato* que controlam a formatação de tipos específicos.</span><span class="sxs-lookup"><span data-stu-id="b38be-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="b38be-157">Modifique a chamada a `Console.WriteLine` no exemplo anterior para incluir as cadeias de caracteres de formato para as expressões de data e de preço, conforme mostrado na linha a seguir:</span><span class="sxs-lookup"><span data-stu-id="b38be-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="b38be-158">Você especifica uma cadeia de caracteres de formato colocando dois-pontos (":") e a cadeia de caracteres de formato após a expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="b38be-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="b38be-159">"d" é uma [cadeia de caracteres de formato de data e hora padrão](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) que representa o formato de data abreviada.</span><span class="sxs-lookup"><span data-stu-id="b38be-159">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="b38be-160">"C2" é um [cadeia de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) que representa um número como um valor de moeda com dois dígitos após o ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="b38be-160">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="b38be-161">Diversos tipos nas bibliotecas do .NET são compatíveis com um conjunto predefinido de cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="b38be-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="b38be-162">Isso inclui todos os tipos numéricos e os tipos de data e hora.</span><span class="sxs-lookup"><span data-stu-id="b38be-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="b38be-163">Para obter uma lista completa dos tipos que são compatíveis com as cadeias de caracteres de formato, consulte [Cadeias de caracteres de formato e tipos da biblioteca de classes do .NET](../../../standard/base-types/formatting-types.md#stringRef) no artigo [Tipos de formatação no .NET](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b38be-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="b38be-164">Tente modificar as cadeias de caracteres de formato em seu editor de texto e, sempre que fizer uma alteração, execute novamente o programa para ver como as alterações afetam a formatação da data e hora e do valor numérico.</span><span class="sxs-lookup"><span data-stu-id="b38be-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="b38be-165">Altere o "d" em `{date:d}` para "t" (para exibir o formato de hora abreviada), para "y" (para exibir o ano e o mês) e para "yyyy" (para exibir o ano como um número de quatro dígitos).</span><span class="sxs-lookup"><span data-stu-id="b38be-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="b38be-166">Altere o "C2" em `{price:C2}` para "e" (para obter notação exponencial) e para "F3" (para um valor numérico com três dígitos após o ponto decimal).</span><span class="sxs-lookup"><span data-stu-id="b38be-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="b38be-167">Além de controlar a formatação, você também pode controlar a largura do campo e o alinhamento das cadeias de caracteres formatadas incluídas na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="b38be-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="b38be-168">Na próxima seção, você aprenderá como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b38be-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="b38be-169">Controlar a largura do campo e o alinhamento de expressões interpoladas</span><span class="sxs-lookup"><span data-stu-id="b38be-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="b38be-170">Normalmente, quando o resultado de uma expressão interpolada é formatado em uma cadeia de caracteres, essa cadeia de caracteres é incluída em uma cadeia de caracteres sem espaços à esquerda nem à direita.</span><span class="sxs-lookup"><span data-stu-id="b38be-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="b38be-171">Especialmente quando você trabalha com um conjunto de dados, poder controlar a largura do campo e o alinhamento do texto ajuda a produzir uma saída mais legível.</span><span class="sxs-lookup"><span data-stu-id="b38be-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="b38be-172">Para ver isso, substitua todo o código em seu editor de texto pelo código a seguir e, em seguida, digite `dotnet run` para executar o programa:</span><span class="sxs-lookup"><span data-stu-id="b38be-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

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

<span data-ttu-id="b38be-173">Os nomes de autores são alinhados à esquerda e os títulos que eles escreveram são alinhados à direita.</span><span class="sxs-lookup"><span data-stu-id="b38be-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="b38be-174">Você especifica o alinhamento adicionando uma vírgula (",") após a expressão interpolada e designando a largura *mínima* do campo.</span><span class="sxs-lookup"><span data-stu-id="b38be-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="b38be-175">Se o valor especificado for um número positivo, o campo será alinhado à direita.</span><span class="sxs-lookup"><span data-stu-id="b38be-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="b38be-176">Se for um número negativo, o campo será alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b38be-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="b38be-177">Tente remover os sinais negativos do código `{"Author",-25}` e `{title.Key,-25}` e execute o exemplo novamente, como feito no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b38be-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="b38be-178">Desta vez, as informações sobre o autor são alinhadas à direita.</span><span class="sxs-lookup"><span data-stu-id="b38be-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="b38be-179">Você pode combinar um especificador de alinhamento e uma cadeia de caracteres de formato em uma única expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="b38be-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="b38be-180">Para fazer isso, especifique o alinhamento primeiro, seguido por dois-pontos e pela cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="b38be-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="b38be-181">Substitua todo o código dentro do método `Main` pelo código a seguir, que exibe três cadeias de caracteres formatadas com larguras de campo definidas.</span><span class="sxs-lookup"><span data-stu-id="b38be-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="b38be-182">Em seguida, execute o programa inserindo o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="b38be-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="b38be-183">A saída é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b38be-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="b38be-184">Você concluiu o tutorial de interpolação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b38be-184">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="b38be-185">Continue com o tutorial [Coleção de listas](arrays-and-collections.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b38be-185">You can continue with the [List collection](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="b38be-186">Para obter mais informações, confira o tópico [Interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md) e o tutorial [Interpolação de cadeia de caracteres no C#](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="b38be-186">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
