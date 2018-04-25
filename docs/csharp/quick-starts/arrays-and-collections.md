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
ms.openlocfilehash: ace19ea8b8a1986466cdc851a1e8bb1c55f9709f
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="c-quickstart-collections"></a><span data-ttu-id="2cbe3-103">Início rápido do C#: coleções</span><span class="sxs-lookup"><span data-stu-id="2cbe3-103">C# Quickstart: Collections</span></span>

<span data-ttu-id="2cbe3-104">Este início rápido fornece uma introdução à linguagem C# e aos conceitos básicos da classe <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-104">This quickstart provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="2cbe3-105">Este início rápido espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-105">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="2cbe3-106">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="2cbe3-107">Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-107">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="2cbe3-108">Um exemplo de lista básica</span><span class="sxs-lookup"><span data-stu-id="2cbe3-108">A basic list example</span></span>

<span data-ttu-id="2cbe3-109">Crie um diretório denominado **list-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-109">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="2cbe3-110">Torne-o o diretório atual e execute `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-110">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="2cbe3-111">Se você acabou de concluir [Introdução ao .NET em 10 minutos](https://www.microsoft.com/net), continue usando o aplicativo myApp que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-111">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>

<span data-ttu-id="2cbe3-112">Abra **Program.cs** em seu editor favorito e substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="2cbe3-113">Substitua `<name>` pelo seu nome.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="2cbe3-114">Salve **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-114">Save **Program.cs**.</span></span> <span data-ttu-id="2cbe3-115">Digite `dotnet run` na janela de console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="2cbe3-116">Você criou uma lista de cadeias de caracteres, adicionou três nomes a essa lista e imprimiu os nomes em MAIÚSCULAS.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="2cbe3-117">Você está usando conceitos que aprendeu em inícios rápidos anteriores para executar um loop pela lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-117">You're using concepts that you've learned in earlier quickstarts to loop through the list.</span></span>

<span data-ttu-id="2cbe3-118">O código para exibir nomes utiliza o recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="2cbe3-118">The code to display names makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="2cbe3-119">Quando você precede um `string` com o caractere `$`, pode inserir o código C# na declaração da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="2cbe3-120">A cadeia de caracteres real substitui esse código C# pelo valor gerado.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="2cbe3-121">Neste exemplo, ela substitui o `{name.ToUpper()}` por cada nome, convertido em letras maiúsculas, pois você chamou o método <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="2cbe3-122">Vamos continuar explorando.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-122">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="2cbe3-123">Modificar conteúdo da lista</span><span class="sxs-lookup"><span data-stu-id="2cbe3-123">Modify list contents</span></span>

<span data-ttu-id="2cbe3-124">A coleção que você criou usa o tipo <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="2cbe3-125">Esse tipo armazena sequências de elementos.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-125">This type stores sequences of elements.</span></span> <span data-ttu-id="2cbe3-126">Especifique o tipo dos elementos entre os colchetes.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-126">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="2cbe3-127">Um aspecto importante desse tipo <xref:System.Collections.Generic.List%601> é que ele pode aumentar ou diminuir, permitindo que você adicione ou remova elementos.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="2cbe3-128">Adicione este código antes do `}` de fechamento no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-128">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="2cbe3-129">Você adicionou mais dois nomes ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="2cbe3-130">Também removeu um.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-130">You've also removed one as well.</span></span> <span data-ttu-id="2cbe3-131">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-131">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="2cbe3-132">O <xref:System.Collections.Generic.List%601> também permite fazer referência a itens individuais por **índice**.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="2cbe3-133">Coloque o índice entre os tokens `[` e `]` após o nome da lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="2cbe3-134">C# usa 0 para o primeiro índice.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="2cbe3-135">Adicione este código diretamente abaixo do código que você acabou de adicionar e teste-o:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="2cbe3-136">Você não pode acessar um índice além do fim da lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="2cbe3-137">Lembre-se de que os índices começam com 0, portanto, o maior índice válido é uma unidade a menos do que o número de itens na lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="2cbe3-138">Você pode verificar há quanto tempo a lista está usando a propriedade <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="2cbe3-139">Adicione o código a seguir ao final do método Main:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="2cbe3-140">Salve o arquivo e digite `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-140">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="2cbe3-141">Pesquisar e classificar listas</span><span class="sxs-lookup"><span data-stu-id="2cbe3-141">Search and sort lists</span></span>

<span data-ttu-id="2cbe3-142">Nossos exemplos usam listas relativamente pequenas, mas seus aplicativos podem criar listas com muitos outros elementos, chegando, às vezes, a milhares.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="2cbe3-143">Para localizar elementos nessas coleções maiores, pesquise por itens diferentes na lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="2cbe3-144">O método <xref:System.Collections.Generic.List%601.IndexOf%2A> procura um item e retorna o índice do item.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="2cbe3-145">Adicione este código à parte inferior de seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="2cbe3-146">Os itens em sua lista também podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="2cbe3-147">O método <xref:System.Collections.Generic.List%601.Sort%2A> classifica todos os itens na lista na ordem normal (em ordem alfabética, no caso de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="2cbe3-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="2cbe3-148">Adicione este código à parte inferior de nosso método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="2cbe3-149">Salve o arquivo e digite `dotnet run` para experimentar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="2cbe3-150">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="2cbe3-151">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="2cbe3-152">Renomeie seu método `Main` como `WorkingWithStrings` e escreva um novo método `Main` que chama `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="2cbe3-153">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-153">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="2cbe3-154">Listas de outros tipos</span><span class="sxs-lookup"><span data-stu-id="2cbe3-154">Lists of other types</span></span>

<span data-ttu-id="2cbe3-155">Você usou o tipo `string` nas listas até o momento.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="2cbe3-156">Vamos fazer <xref:System.Collections.Generic.List%601> usar um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="2cbe3-157">Vamos compilar um conjunto de números.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="2cbe3-158">Adicione o seguinte à parte inferior do novo método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="2cbe3-159">Isso cria uma lista de números inteiros e define os primeiros dois inteiros como o valor 1.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="2cbe3-160">Estes são os dois primeiros valores de uma *sequência Fibonacci*, uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="2cbe3-161">Cada número Fibonacci seguinte é encontrado considerando a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="2cbe3-162">Adicione este código:</span><span class="sxs-lookup"><span data-stu-id="2cbe3-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="2cbe3-163">Salve o arquivo e digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="2cbe3-164">Para se concentrar apenas nesta seção, comente o código que chama `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="2cbe3-165">Coloque apenas dois caracteres `/` na frente da chamada, desta forma: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="2cbe3-166">Desafio</span><span class="sxs-lookup"><span data-stu-id="2cbe3-166">Challenge</span></span>

<span data-ttu-id="2cbe3-167">Veja se você consegue combinar alguns dos conceitos desta lição e de lições anteriores.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="2cbe3-168">Expanda o que você compilou até o momento com números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="2cbe3-169">Tente escrever o código para gerar os 20 primeiros números na sequência.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="2cbe3-170">(Como uma dica, o vigésimo número Fibonacci é 6765.)</span><span class="sxs-lookup"><span data-stu-id="2cbe3-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="2cbe3-171">Desafio concluído</span><span class="sxs-lookup"><span data-stu-id="2cbe3-171">Complete challenge</span></span>

<span data-ttu-id="2cbe3-172">Veja um exemplo de solução [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="2cbe3-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="2cbe3-173">Com cada iteração do loop, você está pegando os últimos dois inteiros na lista, somando-os e adicionando esse valor à lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="2cbe3-174">O loop será repetido até que você tenha adicionado 20 itens à lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="2cbe3-175">Parabéns, você concluiu o início rápido de lista.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-175">Congratulations, you've completed the list quickstart.</span></span> <span data-ttu-id="2cbe3-176">Continue com o início rápido [Introdução às classes](introduction-to-classes.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-176">You can continue with the [Introduction to classes](introduction-to-classes.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="2cbe3-177">Saiba mais sobre como trabalhar com o tipo `List` no tópico [Guia de .NET](../../standard/index.md) em [coleções](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="2cbe3-177">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="2cbe3-178">Você também aprenderá muitos outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="2cbe3-178">You'll also learn about many other collection types.</span></span>