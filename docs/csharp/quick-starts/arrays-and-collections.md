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
ms.custom: mvc
ms.openlocfilehash: 6f559c7a3290e7db2266e10ec792c283394fb904
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="8f00e-104">Início Rápido de C# – Coleções</span><span class="sxs-lookup"><span data-stu-id="8f00e-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="8f00e-105">Este início rápido fornece uma introdução à linguagem C# e os conceitos básicos da classe <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="8f00e-105">This quick start provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="8f00e-106">Este início rápido espera que você tenha uma máquina que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8f00e-106">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="8f00e-107">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="8f00e-107">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="8f00e-108">Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="8f00e-108">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="8f00e-109">Um exemplo de lista básica.</span><span class="sxs-lookup"><span data-stu-id="8f00e-109">A basic list example.</span></span>

<span data-ttu-id="8f00e-110">Crie um diretório denominado **list-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="8f00e-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="8f00e-111">Torne-o o diretório atual e execute `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="8f00e-111">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="8f00e-112">Se você acabou de concluir [Introdução ao .NET em 10 minutos](https://www.microsoft.com/net), continue usando o aplicativo myApp que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="8f00e-112">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>
 
<span data-ttu-id="8f00e-113">Abra **Program.cs** em seu editor favorito e substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="8f00e-113">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="8f00e-114">Substitua `<name>` pelo seu nome.</span><span class="sxs-lookup"><span data-stu-id="8f00e-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="8f00e-115">Salve **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="8f00e-115">Save **Program.cs**.</span></span> <span data-ttu-id="8f00e-116">Digite `dotnet run` na janela de console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="8f00e-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="8f00e-117">Você criou uma lista de cadeias de caracteres, adicionou três nomes a essa lista e imprimiu os nomes em MAIÚSCULAS.</span><span class="sxs-lookup"><span data-stu-id="8f00e-117">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="8f00e-118">Você está usando conceitos que aprendeu em inícios rápidos anteriores para executar um loop pela lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-118">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="8f00e-119">O código para exibir nomes usa **cadeias de caracteres interpoladas**.</span><span class="sxs-lookup"><span data-stu-id="8f00e-119">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="8f00e-120">Quando você precede um `string` com o caractere `$`, pode inserir o código C# na declaração da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8f00e-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="8f00e-121">A cadeia de caracteres real substitui esse código C# pelo valor gerado.</span><span class="sxs-lookup"><span data-stu-id="8f00e-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="8f00e-122">Neste exemplo, ela substitui o `{name.ToUpper()}` por cada nome, convertido em letras maiúsculas, pois você chamou o método <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f00e-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="8f00e-123">Vamos continuar explorando.</span><span class="sxs-lookup"><span data-stu-id="8f00e-123">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="8f00e-124">Modificar conteúdo da lista</span><span class="sxs-lookup"><span data-stu-id="8f00e-124">Modify list contents</span></span>

<span data-ttu-id="8f00e-125">A coleção que você criou usa o tipo <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="8f00e-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="8f00e-126">Esse tipo armazena sequências de elementos.</span><span class="sxs-lookup"><span data-stu-id="8f00e-126">This type stores sequences of elements.</span></span> <span data-ttu-id="8f00e-127">Especifique o tipo dos elementos entre os colchetes.</span><span class="sxs-lookup"><span data-stu-id="8f00e-127">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="8f00e-128">Um aspecto importante desse tipo <xref:System.Collections.Generic.List%601> é que ele pode aumentar ou diminuir, permitindo que você adicione ou remova elementos.</span><span class="sxs-lookup"><span data-stu-id="8f00e-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="8f00e-129">Adicione este código antes do `}` de fechamento no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="8f00e-129">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="8f00e-130">Você adicionou mais dois nomes ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="8f00e-131">Também removeu um.</span><span class="sxs-lookup"><span data-stu-id="8f00e-131">You've also removed one as well.</span></span> <span data-ttu-id="8f00e-132">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="8f00e-132">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="8f00e-133">O <xref:System.Collections.Generic.List%601> também permite fazer referência a itens individuais por **índice**.</span><span class="sxs-lookup"><span data-stu-id="8f00e-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="8f00e-134">Coloque o índice entre os tokens `[` e `]` após o nome da lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="8f00e-135">C# usa 0 para o primeiro índice.</span><span class="sxs-lookup"><span data-stu-id="8f00e-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="8f00e-136">Adicione este código diretamente abaixo do código que você acabou de adicionar e teste-o:</span><span class="sxs-lookup"><span data-stu-id="8f00e-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="8f00e-137">Você não pode acessar um índice além do fim da lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-137">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="8f00e-138">Lembre-se de que os índices começam com 0, portanto, o maior índice válido é uma unidade a menos do que o número de itens na lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="8f00e-139">Você pode verificar há quanto tempo a lista está usando a propriedade <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f00e-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="8f00e-140">Adicione o código a seguir ao final do método Main:</span><span class="sxs-lookup"><span data-stu-id="8f00e-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="8f00e-141">Salve o arquivo e digite `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="8f00e-141">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="8f00e-142">Pesquisar e classificar listas</span><span class="sxs-lookup"><span data-stu-id="8f00e-142">Search and sort lists</span></span>
<span data-ttu-id="8f00e-143">Nossos exemplos usam listas relativamente pequenas, mas seus aplicativos podem criar listas com muitos outros elementos, chegando, às vezes, a milhares.</span><span class="sxs-lookup"><span data-stu-id="8f00e-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="8f00e-144">Para localizar elementos nessas coleções maiores, pesquise por itens diferentes na lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="8f00e-145">O método <xref:System.Collections.Generic.List%601.IndexOf%2A> procura um item e retorna o índice do item.</span><span class="sxs-lookup"><span data-stu-id="8f00e-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="8f00e-146">Adicione este código à parte inferior de seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="8f00e-146">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="8f00e-147">Os itens em sua lista também podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="8f00e-147">The items in your list can be sorted as well.</span></span> <span data-ttu-id="8f00e-148">O método <xref:System.Collections.Generic.List%601.Sort%2A> classifica todos os itens na lista na ordem normal (em ordem alfabética, no caso de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="8f00e-148">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="8f00e-149">Adicione este código à parte inferior de nosso método `Main`:</span><span class="sxs-lookup"><span data-stu-id="8f00e-149">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="8f00e-150">Salve o arquivo e digite `dotnet run` para experimentar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="8f00e-150">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="8f00e-151">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="8f00e-151">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="8f00e-152">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="8f00e-152">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="8f00e-153">Renomeie seu método `Main` como `WorkingWithStrings` e escreva um novo método `Main` que chama `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="8f00e-153">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="8f00e-154">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="8f00e-154">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="8f00e-155">Listas de outros tipos</span><span class="sxs-lookup"><span data-stu-id="8f00e-155">Lists of other types</span></span>

<span data-ttu-id="8f00e-156">Você usou o tipo `string` nas listas até o momento.</span><span class="sxs-lookup"><span data-stu-id="8f00e-156">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="8f00e-157">Vamos fazer <xref:System.Collections.Generic.List%601> usar um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="8f00e-157">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="8f00e-158">Vamos compilar um conjunto de números.</span><span class="sxs-lookup"><span data-stu-id="8f00e-158">Let's build a set of numbers.</span></span> 

<span data-ttu-id="8f00e-159">Adicione o seguinte à parte inferior do novo método `Main`:</span><span class="sxs-lookup"><span data-stu-id="8f00e-159">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="8f00e-160">Isso cria uma lista de números inteiros e define os primeiros dois inteiros como o valor 1.</span><span class="sxs-lookup"><span data-stu-id="8f00e-160">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="8f00e-161">Estes são os dois primeiros valores de uma *sequência Fibonacci*, uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="8f00e-161">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="8f00e-162">Cada número Fibonacci seguinte é encontrado considerando a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="8f00e-162">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="8f00e-163">Adicione este código:</span><span class="sxs-lookup"><span data-stu-id="8f00e-163">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="8f00e-164">Salve o arquivo e digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="8f00e-164">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="8f00e-165">Para se concentrar apenas nesta seção, comente o código que chama `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="8f00e-165">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="8f00e-166">Coloque apenas dois caracteres `/` na frente da chamada, desta forma: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="8f00e-166">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="8f00e-167">Desafio</span><span class="sxs-lookup"><span data-stu-id="8f00e-167">Challenge</span></span>
<span data-ttu-id="8f00e-168">Veja se você consegue combinar alguns dos conceitos desta lição e de lições anteriores.</span><span class="sxs-lookup"><span data-stu-id="8f00e-168">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="8f00e-169">Expanda o que você compilou até o momento com números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="8f00e-169">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="8f00e-170">Tente escrever o código para gerar os 20 primeiros números na sequência.</span><span class="sxs-lookup"><span data-stu-id="8f00e-170">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="8f00e-171">(Como uma dica, o vigésimo número Fibonacci é 6765.)</span><span class="sxs-lookup"><span data-stu-id="8f00e-171">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="8f00e-172">Desafio concluído</span><span class="sxs-lookup"><span data-stu-id="8f00e-172">Complete challenge</span></span>

<span data-ttu-id="8f00e-173">Veja um exemplo de solução [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="8f00e-173">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="8f00e-174">Com cada iteração do loop, você está pegando os últimos dois inteiros na lista, somando-os e adicionando esse valor à lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-174">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="8f00e-175">O loop será repetido até que você tenha adicionado 20 itens à lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-175">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="8f00e-176">Parabéns, você concluiu o início rápido de lista.</span><span class="sxs-lookup"><span data-stu-id="8f00e-176">Congratulations, you've completed the list quick start.</span></span> <span data-ttu-id="8f00e-177">Continue com o início rápido [Introdução às classes](introduction-to-classes.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8f00e-177">You can continue with the [Introduction to classes](introduction-to-classes.md) quick start in your own development environment.</span></span>

<span data-ttu-id="8f00e-178">Saiba mais sobre como trabalhar com o tipo `List` no tópico [Guia de .NET](../../standard/index.md) em [coleções](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f00e-178">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="8f00e-179">Você também aprenderá muitos outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="8f00e-179">You'll also learn about many other collection types.</span></span>
