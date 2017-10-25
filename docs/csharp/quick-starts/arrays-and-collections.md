---
title: "Início Rápido – Coleções – Guia de C#"
description: "Aprenda C# explorando a Coleção de lista neste início rápido."
keywords: "C#, Introdução, tutorial, coleções, Lista"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 51b190fba32186cb4c52ccd773274d9ae22c8efb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="0a7a4-104">Início Rápido de C# – Coleções</span><span class="sxs-lookup"><span data-stu-id="0a7a4-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="0a7a4-105">Este tutorial fornece uma introdução à linguagem C# e os conceitos básicos da classe <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-105">This tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="a-simple-list-example"></a><span data-ttu-id="0a7a4-106">Um exemplo de lista simples.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-106">A simple list example.</span></span>

> [!NOTE]
> <span data-ttu-id="0a7a4-107">Se estiver começando a partir do código que você escreveu em [dot.net](https://dot.net/), você já terá o código escrito nesta seção.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-107">If you're starting from the code you wrote in [dot.net](https://dot.net/), you already have the code written in this section.</span></span> <span data-ttu-id="0a7a4-108">Vá para [Modificar conteúdo da lista](#modify-list-contents).</span><span class="sxs-lookup"><span data-stu-id="0a7a4-108">Jump to [Modify list contents](#modify-list-contents).</span></span>

<span data-ttu-id="0a7a4-109">Esta lição exige que você tenha terminado os inícios rápidos online e instalado o [SDK do .NET Core](http://dot.net/core) e o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="0a7a4-109">This lesson assumes you've finished the online quick starts, and you've installed the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span> 

<span data-ttu-id="0a7a4-110">Crie um diretório denominado **list-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="0a7a4-111">Torne-o o diretório atual e execute `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-111">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="0a7a4-112">Abra **Program.cs** em seu editor favorito e substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="0a7a4-113">Substitua `<name>` pelo seu nome.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="0a7a4-114">Salve **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-114">Save **Program.cs**.</span></span> <span data-ttu-id="0a7a4-115">Digite `dotnet run` na janela de console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="0a7a4-116">Você criou uma lista de cadeias de caracteres, adicionou três nomes a essa lista e imprimiu os nomes em MAIÚSCULAS.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="0a7a4-117">Você está usando conceitos que aprendeu em inícios rápidos anteriores para executar um loop pela lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-117">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="0a7a4-118">O código para exibir nomes usa **cadeias de caracteres interpoladas**.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-118">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="0a7a4-119">Quando você precede um `string` com o caractere `$`, pode inserir o código C# na declaração da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="0a7a4-120">A cadeia de caracteres real substitui esse código C# pelo valor gerado.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="0a7a4-121">Neste exemplo, ela substitui o `{name.ToUpper()}` por cada nome, convertido em letras maiúsculas, pois você chamou o método <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="0a7a4-122">Vamos continuar explorando.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-122">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="0a7a4-123">Modificar conteúdo da lista</span><span class="sxs-lookup"><span data-stu-id="0a7a4-123">Modify list contents</span></span>

<span data-ttu-id="0a7a4-124">A coleção que você criou usa o tipo <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="0a7a4-125">Esse tipo armazena sequências de elementos.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-125">This type stores sequences of elements.</span></span> <span data-ttu-id="0a7a4-126">Especifique o tipo dos elementos entre os colchetes.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-126">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="0a7a4-127">Um aspecto importante desse tipo <xref:System.Collections.Generic.List%601> é que ele pode aumentar ou diminuir, permitindo que você adicione ou remova elementos.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="0a7a4-128">Adicione este código antes do `}` de fechamento no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-128">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="0a7a4-129">Você adicionou mais dois nomes ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="0a7a4-130">Também removeu um.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-130">You've also removed one as well.</span></span> <span data-ttu-id="0a7a4-131">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-131">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="0a7a4-132">O <xref:System.Collections.Generic.List%601> também permite fazer referência a itens individuais por **índice**.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="0a7a4-133">Coloque o índice entre os tokens `[` e `]` após o nome da lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="0a7a4-134">C# usa 0 para o primeiro índice.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="0a7a4-135">Adicione este código diretamente abaixo do código que você acabou de adicionar e teste-o:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="0a7a4-136">Você não pode acessar um índice além do fim da lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="0a7a4-137">Lembre-se de que os índices começam com 0, portanto, o maior índice válido é uma unidade a menos do que o número de itens na lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="0a7a4-138">Você pode verificar há quanto tempo a lista está usando a propriedade <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="0a7a4-139">Adicione o código a seguir ao final do método Main:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="0a7a4-140">Salve o arquivo e digite `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-140">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="0a7a4-141">Pesquisar e classificar listas</span><span class="sxs-lookup"><span data-stu-id="0a7a4-141">Search and sort lists</span></span>
<span data-ttu-id="0a7a4-142">Nossos exemplos usam listas relativamente pequenas, mas seus aplicativos podem criar listas com muitos outros elementos, chegando, às vezes, a milhares.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="0a7a4-143">Para localizar elementos nessas coleções maiores, pesquise por itens diferentes na lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="0a7a4-144">O método <xref:System.Collections.Generic.List%601.IndexOf%2A> procura um item e retorna o índice do item.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="0a7a4-145">Adicione este código à parte inferior de seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="0a7a4-146">Os itens em sua lista também podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="0a7a4-147">O método <xref:System.Collections.Generic.List%601.Sort%2A> classifica todos os itens na lista na ordem normal (em ordem alfabética, no caso de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="0a7a4-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="0a7a4-148">Adicione este código à parte inferior de nosso método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="0a7a4-149">Salve o arquivo e digite `dotnet run` para experimentar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="0a7a4-150">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="0a7a4-151">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="0a7a4-152">Renomeie seu método `Main` como `WorkingWithStrings` e escreva um novo método `Main` que chama `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="0a7a4-153">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-153">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="0a7a4-154">Listas de outros tipos</span><span class="sxs-lookup"><span data-stu-id="0a7a4-154">Lists of other types</span></span>

<span data-ttu-id="0a7a4-155">Você usou o tipo `string` nas listas até o momento.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="0a7a4-156">Vamos fazer <xref:System.Collections.Generic.List%601> usar um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="0a7a4-157">Vamos compilar um conjunto de números.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-157">Let's build a set of numbers.</span></span> 

<span data-ttu-id="0a7a4-158">Adicione o seguinte à parte inferior do novo método `Main`:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="0a7a4-159">Isso cria uma lista de números inteiros e define os primeiros dois inteiros como o valor 1.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="0a7a4-160">Estes são os dois primeiros valores de uma *sequência Fibonacci*, uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="0a7a4-161">Cada número Fibonacci seguinte é encontrado considerando a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="0a7a4-162">Adicione este código:</span><span class="sxs-lookup"><span data-stu-id="0a7a4-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="0a7a4-163">Salve o arquivo e digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-163">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="0a7a4-164">Para se concentrar apenas nesta seção, comente o código que chama `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="0a7a4-165">Coloque apenas dois caracteres `/` na frente da chamada, desta forma: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="0a7a4-166">Desafio</span><span class="sxs-lookup"><span data-stu-id="0a7a4-166">Challenge</span></span>
<span data-ttu-id="0a7a4-167">Veja se você consegue combinar algumas das lições desta versão e de versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-167">See if you can put together some of the lessons from this and earlier lessons.</span></span> <span data-ttu-id="0a7a4-168">Expanda o que você compilou até o momento com números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="0a7a4-169">Tente escrever o código para gerar os 20 primeiros números na sequência.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-169">Try and write the code to generate the first 20 numbers in the sequence.</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="0a7a4-170">Desafio concluído</span><span class="sxs-lookup"><span data-stu-id="0a7a4-170">Complete challenge</span></span>

<span data-ttu-id="0a7a4-171">Veja um exemplo de solução [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="0a7a4-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span></span>

<span data-ttu-id="0a7a4-172">Com cada iteração do loop, você está pegando os últimos dois inteiros na lista, somando-os e adicionando esse valor à lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="0a7a4-173">O loop será repetido até que você tenha adicionado 20 itens à lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="0a7a4-174">Parabéns, você concluiu o tutorial de lista.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-174">Congratulations, you've completed the list tutorial.</span></span>

<span data-ttu-id="0a7a4-175">Saiba mais sobre como trabalhar com o tipo `List` no tópico [Guia de .NET](../../standard/index.md) em [coleções](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="0a7a4-175">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="0a7a4-176">Você também aprenderá muitos outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="0a7a4-176">You'll also learn about many other collection types.</span></span>
