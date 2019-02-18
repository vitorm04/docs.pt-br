---
title: Trabalhar com coleções – Introdução ao tutorial do C#
description: Aprenda C# explorando a Coleção de lista neste tutorial.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 9a910ccd6265011fc0e5540b461ba089dbd3e7ba
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261265"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="9e497-103">Saiba como gerenciar coleções de dados usando o tipo de lista genérico</span><span class="sxs-lookup"><span data-stu-id="9e497-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="9e497-104">Este tutorial de introdução fornece uma introdução à linguagem C# e os conceitos básicos da classe <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="9e497-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="9e497-105">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9e497-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9e497-106">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="9e497-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="9e497-107">Uma visão geral de comandos que você usará está em [Familiarizar-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="9e497-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="9e497-108">Um exemplo de lista básica</span><span class="sxs-lookup"><span data-stu-id="9e497-108">A basic list example</span></span>

<span data-ttu-id="9e497-109">Crie um diretório chamado **list-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="9e497-109">Create a directory named **list-tutorial**.</span></span> <span data-ttu-id="9e497-110">Torne-o o diretório atual e execute `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="9e497-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="9e497-111">Abra **Program.cs** em seu editor favorito e substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e497-111">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

<span data-ttu-id="9e497-112">Substitua `<name>` pelo seu nome.</span><span class="sxs-lookup"><span data-stu-id="9e497-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="9e497-113">Salve **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="9e497-113">Save **Program.cs**.</span></span> <span data-ttu-id="9e497-114">Digite `dotnet run` na janela de console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="9e497-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="9e497-115">Você criou uma lista de cadeias de caracteres, adicionou três nomes a essa lista e imprimiu os nomes em MAIÚSCULAS.</span><span class="sxs-lookup"><span data-stu-id="9e497-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="9e497-116">Você está usando conceitos que aprendeu em tutoriais anteriores para executar um loop pela lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="9e497-117">O código para exibir nomes utiliza o recurso de [interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="9e497-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="9e497-118">Quando você precede um `string` com o caractere `$`, pode inserir o código C# na declaração da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e497-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="9e497-119">A cadeia de caracteres real substitui esse código C# pelo valor gerado.</span><span class="sxs-lookup"><span data-stu-id="9e497-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="9e497-120">Neste exemplo, ela substitui o `{name.ToUpper()}` por cada nome, convertido em letras maiúsculas, pois você chamou o método <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e497-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="9e497-121">Vamos continuar explorando.</span><span class="sxs-lookup"><span data-stu-id="9e497-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="9e497-122">Modificar conteúdo da lista</span><span class="sxs-lookup"><span data-stu-id="9e497-122">Modify list contents</span></span>

<span data-ttu-id="9e497-123">A coleção que você criou usa o tipo <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="9e497-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="9e497-124">Esse tipo armazena sequências de elementos.</span><span class="sxs-lookup"><span data-stu-id="9e497-124">This type stores sequences of elements.</span></span> <span data-ttu-id="9e497-125">Especifique o tipo dos elementos entre os colchetes.</span><span class="sxs-lookup"><span data-stu-id="9e497-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="9e497-126">Um aspecto importante desse tipo <xref:System.Collections.Generic.List%601> é que ele pode aumentar ou diminuir, permitindo que você adicione ou remova elementos.</span><span class="sxs-lookup"><span data-stu-id="9e497-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="9e497-127">Adicione este código antes do `}` de fechamento no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9e497-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="9e497-128">Você adicionou mais dois nomes ao final da lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="9e497-129">Também removeu um.</span><span class="sxs-lookup"><span data-stu-id="9e497-129">You've also removed one as well.</span></span> <span data-ttu-id="9e497-130">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="9e497-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="9e497-131">O <xref:System.Collections.Generic.List%601> também permite fazer referência a itens individuais por **índice**.</span><span class="sxs-lookup"><span data-stu-id="9e497-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="9e497-132">Coloque o índice entre os tokens `[` e `]` após o nome da lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="9e497-133">C# usa 0 para o primeiro índice.</span><span class="sxs-lookup"><span data-stu-id="9e497-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="9e497-134">Adicione este código diretamente abaixo do código que você acabou de adicionar e teste-o:</span><span class="sxs-lookup"><span data-stu-id="9e497-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="9e497-135">Você não pode acessar um índice além do fim da lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="9e497-136">Lembre-se de que os índices começam com 0, portanto, o maior índice válido é uma unidade a menos do que o número de itens na lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="9e497-137">Você pode verificar há quanto tempo a lista está usando a propriedade <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e497-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="9e497-138">Adicione o código a seguir ao final do método Main:</span><span class="sxs-lookup"><span data-stu-id="9e497-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="9e497-139">Salve o arquivo e digite `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="9e497-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="9e497-140">Pesquisar e classificar listas</span><span class="sxs-lookup"><span data-stu-id="9e497-140">Search and sort lists</span></span>

<span data-ttu-id="9e497-141">Nossos exemplos usam listas relativamente pequenas, mas seus aplicativos podem criar listas com muitos outros elementos, chegando, às vezes, a milhares.</span><span class="sxs-lookup"><span data-stu-id="9e497-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="9e497-142">Para localizar elementos nessas coleções maiores, pesquise por itens diferentes na lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="9e497-143">O método <xref:System.Collections.Generic.List%601.IndexOf%2A> procura um item e retorna o índice do item.</span><span class="sxs-lookup"><span data-stu-id="9e497-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="9e497-144">Adicione este código à parte inferior de seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9e497-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="9e497-145">Os itens em sua lista também podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="9e497-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="9e497-146">O método <xref:System.Collections.Generic.List%601.Sort%2A> classifica todos os itens na lista na ordem normal (em ordem alfabética, no caso de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="9e497-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="9e497-147">Adicione este código à parte inferior de nosso método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9e497-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="9e497-148">Salve o arquivo e digite `dotnet run` para experimentar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="9e497-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="9e497-149">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="9e497-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="9e497-150">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="9e497-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="9e497-151">Renomeie seu método `Main` como `WorkingWithStrings` e escreva um novo método `Main` que chama `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="9e497-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="9e497-152">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="9e497-152">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

## <a name="lists-of-other-types"></a><span data-ttu-id="9e497-153">Listas de outros tipos</span><span class="sxs-lookup"><span data-stu-id="9e497-153">Lists of other types</span></span>

<span data-ttu-id="9e497-154">Você usou o tipo `string` nas listas até o momento.</span><span class="sxs-lookup"><span data-stu-id="9e497-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="9e497-155">Vamos fazer <xref:System.Collections.Generic.List%601> usar um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="9e497-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="9e497-156">Vamos compilar um conjunto de números.</span><span class="sxs-lookup"><span data-stu-id="9e497-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="9e497-157">Adicione o seguinte à parte inferior do novo método `Main`:</span><span class="sxs-lookup"><span data-stu-id="9e497-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="9e497-158">Isso cria uma lista de números inteiros e define os primeiros dois inteiros como o valor 1.</span><span class="sxs-lookup"><span data-stu-id="9e497-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="9e497-159">Estes são os dois primeiros valores de uma *sequência Fibonacci*, uma sequência de números.</span><span class="sxs-lookup"><span data-stu-id="9e497-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="9e497-160">Cada número Fibonacci seguinte é encontrado considerando a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="9e497-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="9e497-161">Adicione este código:</span><span class="sxs-lookup"><span data-stu-id="9e497-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="9e497-162">Salve o arquivo e digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="9e497-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="9e497-163">Para se concentrar apenas nesta seção, comente o código que chama `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="9e497-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="9e497-164">Coloque apenas dois caracteres `/` na frente da chamada, desta forma: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="9e497-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="9e497-165">Desafio</span><span class="sxs-lookup"><span data-stu-id="9e497-165">Challenge</span></span>

<span data-ttu-id="9e497-166">Veja se você consegue combinar alguns dos conceitos desta lição e de lições anteriores.</span><span class="sxs-lookup"><span data-stu-id="9e497-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="9e497-167">Expanda o que você compilou até o momento com números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="9e497-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="9e497-168">Tente escrever o código para gerar os 20 primeiros números na sequência.</span><span class="sxs-lookup"><span data-stu-id="9e497-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="9e497-169">(Como uma dica, o vigésimo número Fibonacci é 6765.)</span><span class="sxs-lookup"><span data-stu-id="9e497-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="9e497-170">Desafio concluído</span><span class="sxs-lookup"><span data-stu-id="9e497-170">Complete challenge</span></span>

<span data-ttu-id="9e497-171">Veja um exemplo de solução [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="9e497-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="9e497-172">Com cada iteração do loop, você está pegando os últimos dois inteiros na lista, somando-os e adicionando esse valor à lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="9e497-173">O loop será repetido até que você tenha adicionado 20 itens à lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="9e497-174">Parabéns, você concluiu o tutorial de lista.</span><span class="sxs-lookup"><span data-stu-id="9e497-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="9e497-175">Continue com o tutorial [Introdução às classes](introduction-to-classes.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9e497-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="9e497-176">Saiba mais sobre como trabalhar com o tipo `List` no tópico [Guia de .NET](../../../standard/index.md) em [coleções](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e497-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="9e497-177">Você também aprenderá muitos outros tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="9e497-177">You'll also learn about many other collection types.</span></span>