---
title: Trabalhando com LINQ
description: Este tutorial ensina a gerar sequências com LINQ, escrever métodos para uso em consultas LINQ e diferenciar entre avaliação lenta e detalhada.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: f80567510509ba0c7f205ccbd5e587f9ad31f531
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785872"
---
# <a name="working-with-linq"></a><span data-ttu-id="79eb7-103">Trabalhando com LINQ</span><span class="sxs-lookup"><span data-stu-id="79eb7-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="79eb7-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="79eb7-104">Introduction</span></span>

<span data-ttu-id="79eb7-105">Este tutorial ensina os recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="79eb7-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="79eb7-106">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="79eb7-106">You’ll learn:</span></span>

- <span data-ttu-id="79eb7-107">Como gerar sequências com LINQ.</span><span class="sxs-lookup"><span data-stu-id="79eb7-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="79eb7-108">Como escrever métodos que podem ser facilmente usados em consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="79eb7-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="79eb7-109">Como distinguir entre uma avaliação lenta e uma detalhada.</span><span class="sxs-lookup"><span data-stu-id="79eb7-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="79eb7-110">Você aprenderá essas técnicas ao compilar um aplicativo que demonstra uma das habilidades básicas de qualquer mágico: o [embaralhamento faro](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="79eb7-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="79eb7-111">Em resumo, um embaralhamento faro é uma técnica em que você divide um baralho de cartas exatamente na metade, então as cartas de cada metade são colocadas em ordem aleatória até recriar o conjunto original.</span><span class="sxs-lookup"><span data-stu-id="79eb7-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="79eb7-112">Os mágicos usam essa técnica porque cada carta é fica em um local conhecido após o embaralhamento e a ordem é um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="79eb7-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="79eb7-113">Para os seus propósitos, vamos examinar rapidamente as sequências de manipulação de dados.</span><span class="sxs-lookup"><span data-stu-id="79eb7-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="79eb7-114">O aplicativo que você criará construirá um baralho de cartas e, em seguida, executará uma sequência de embaralhamento, sempre gravando a sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="79eb7-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="79eb7-115">Você também comparará a ordem atualizada com a ordem original.</span><span class="sxs-lookup"><span data-stu-id="79eb7-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="79eb7-116">Este tutorial tem várias etapas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="79eb7-117">Após cada etapa, você poderá executar o aplicativo e ver o progresso.</span><span class="sxs-lookup"><span data-stu-id="79eb7-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="79eb7-118">Você também poderá ver o [exemplo concluído](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) no repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="79eb7-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="79eb7-119">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="79eb7-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79eb7-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="79eb7-120">Prerequisites</span></span>

<span data-ttu-id="79eb7-121">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79eb7-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="79eb7-122">Você pode encontrar as instruções de instalação na página de [download do .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="79eb7-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="79eb7-123">Você pode executar esse aplicativo no Windows, Ubuntu Linux, OS X ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="79eb7-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="79eb7-124">Você precisará instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="79eb7-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="79eb7-125">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="79eb7-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="79eb7-126">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="79eb7-127">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="79eb7-127">Create the Application</span></span>

<span data-ttu-id="79eb7-128">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79eb7-128">The first step is to create a new application.</span></span> <span data-ttu-id="79eb7-129">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79eb7-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="79eb7-130">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="79eb7-130">Make that the current directory.</span></span> <span data-ttu-id="79eb7-131">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="79eb7-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="79eb7-132">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="79eb7-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="79eb7-133">Se você nunca usou C# antes, [este tutorial](console-teleprompter.md) explicará a estrutura de um programa C#.</span><span class="sxs-lookup"><span data-stu-id="79eb7-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="79eb7-134">Você pode ler e, em seguida, voltar aqui para saber mais sobre o LINQ.</span><span class="sxs-lookup"><span data-stu-id="79eb7-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="79eb7-135">Criando o arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="79eb7-135">Creating the Data Set</span></span>

<span data-ttu-id="79eb7-136">Antes de começar, verifique se as linhas a seguir estão na parte superior do arquivo `Program.cs` gerado pelo `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="79eb7-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="79eb7-137">Se essas três linhas (instruções `using`) não estiverem na parte superior do arquivo, nosso programa não será compilado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="79eb7-138">Agora que você tem todas as referências necessárias, considere o que forma um baralho de cartas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="79eb7-139">Um baralho de cartas costuma ter quatro naipes, e cada naipe tem treze valores.</span><span class="sxs-lookup"><span data-stu-id="79eb7-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="79eb7-140">Normalmente, talvez você pense em criar uma classe `Card` logo de cara e preencher uma coleção de objetos `Card` manualmente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="79eb7-141">Com o LINQ, dá para ser mais conciso do que a forma comum de criação de um baralho de cartas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="79eb7-142">Em vez de criar uma classe `Card`, você pode criar duas sequências para representar naipes e valores, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="79eb7-143">Você vai criar um par muito simples de [*métodos iteradores*](../iterators.md#enumeration-sources-with-iterator-methods) que gerará as valores e naipes como <xref:System.Collections.Generic.IEnumerable%601>s de cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="79eb7-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="79eb7-144">Coloque-as sob o método `Main` em seu arquivo `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="79eb7-145">Esses dois métodos utilizam a sintaxe `yield return` para produzir uma sequência à medida que eles são executados.</span><span class="sxs-lookup"><span data-stu-id="79eb7-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="79eb7-146">O compilador compila um objeto que implementa <xref:System.Collections.Generic.IEnumerable%601> e gera a sequência de cadeias de caracteres conforme solicitado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="79eb7-147">Agora, use esses métodos iteradores para criar o baralho de cartas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="79eb7-148">Você colocará a consulta do LINQ em nosso método `Main`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="79eb7-149">Dê uma olhada:</span><span class="sxs-lookup"><span data-stu-id="79eb7-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="79eb7-150">As várias cláusulas `from` produzem um <xref:System.Linq.Enumerable.SelectMany%2A>, que cria uma única sequência da combinação entre cada elemento na primeira sequência com cada elemento na segunda sequência.</span><span class="sxs-lookup"><span data-stu-id="79eb7-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="79eb7-151">A ordem é importante para nossos objetivos.</span><span class="sxs-lookup"><span data-stu-id="79eb7-151">The order is important for our purposes.</span></span> <span data-ttu-id="79eb7-152">O primeiro elemento na primeira sequência de fonte (Naipes) é combinado com cada elemento na segunda sequência (Valores).</span><span class="sxs-lookup"><span data-stu-id="79eb7-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="79eb7-153">Isso produz todas as treze cartas do primeiro naipe.</span><span class="sxs-lookup"><span data-stu-id="79eb7-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="79eb7-154">Esse processo é repetido com cada elemento na primeira sequência (naipes).</span><span class="sxs-lookup"><span data-stu-id="79eb7-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="79eb7-155">O resultado final é um baralho ordenado por naipes, seguido pelos valores.</span><span class="sxs-lookup"><span data-stu-id="79eb7-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="79eb7-156">É importante lembrar que se você optar por escrever seu LINQ na sintaxe de consulta usada acima, ou se decidir usar a sintaxe de método, sempre será possível alternar entre as formas de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="79eb7-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="79eb7-157">A consulta acima escrita em sintaxe de consulta pode ser escrita na sintaxe de método como:</span><span class="sxs-lookup"><span data-stu-id="79eb7-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="79eb7-158">O compilador traduz instruções LINQ escritas com a sintaxe de consulta na sintaxe de chamada do método equivalente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="79eb7-159">Portanto, independentemente de sua escolha de sintaxe, as duas versões da consulta produzem o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="79eb7-160">Escolha qual sintaxe funciona melhor para a sua situação: por exemplo, se você estiver trabalhando em uma equipe em que alguns dos membros têm dificuldade com a sintaxe de método, prefira usar a sintaxe de consulta.</span><span class="sxs-lookup"><span data-stu-id="79eb7-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="79eb7-161">Vá em frente e execute o exemplo que você criou neste momento.</span><span class="sxs-lookup"><span data-stu-id="79eb7-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="79eb7-162">Ele exibirá todas as 52 cartas do baralho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="79eb7-163">Talvez seja muito útil executar esse exemplo em um depurador para observar como os métodos `Suits()` e `Ranks()` são executados.</span><span class="sxs-lookup"><span data-stu-id="79eb7-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="79eb7-164">Você pode ver claramente que cada cadeia de caracteres em cada sequência é gerada apenas conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="79eb7-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Uma janela de console mostrando o aplicativo gravando 52 cartas.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="79eb7-166">Manipulando a ordem</span><span class="sxs-lookup"><span data-stu-id="79eb7-166">Manipulating the Order</span></span>

<span data-ttu-id="79eb7-167">Em seguida, concentre-se em como você vai embaralhar as cartas no baralho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="79eb7-168">A primeira etapa de qualquer embaralhada é dividir o baralho em dois.</span><span class="sxs-lookup"><span data-stu-id="79eb7-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="79eb7-169">Os métodos <xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> que fazem parte das APIs do LINQ fornecem esse recurso para você.</span><span class="sxs-lookup"><span data-stu-id="79eb7-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="79eb7-170">Coloque-os sob o loop `foreach`:</span><span class="sxs-lookup"><span data-stu-id="79eb7-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="79eb7-171">No entanto, não há método de embaralhamento na biblioteca padrão, portanto, você precisará escrever o seu.</span><span class="sxs-lookup"><span data-stu-id="79eb7-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="79eb7-172">O método de embaralhamento que você criará ilustra várias técnicas que você usará com programas baseados em LINQ. Portanto, cada parte desse processo será explicado nas etapas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="79eb7-173">Para adicionar funcionalidade ao seu modo de interação com o <xref:System.Collections.Generic.IEnumerable%601> recebido de volta das consultas do LINQ, precisará escrever alguns tipos especiais de métodos chamados [métodos de extensão](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="79eb7-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="79eb7-174">Em resumo, um método de extensão é um *método estático* de objetivo especial que adiciona novas funcionalidades a um tipo já existentes, sem ter que modificar o tipo original ao qual você deseja adicionar funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="79eb7-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="79eb7-175">Dê aos seus métodos de extensão uma nova casa adicionando um novo arquivo de classe *estático* ao seu programa chamado `Extensions.cs`, depois, comece a criar o primeiro método de extensão:</span><span class="sxs-lookup"><span data-stu-id="79eb7-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="79eb7-176">Examine a assinatura do método por um momento, principalmente os parâmetros:</span><span class="sxs-lookup"><span data-stu-id="79eb7-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="79eb7-177">Você pode ver a adição do modificador `this` no primeiro argumento para o método.</span><span class="sxs-lookup"><span data-stu-id="79eb7-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="79eb7-178">Isso significa que você chama o método como se fosse um método de membro do tipo do primeiro argumento.</span><span class="sxs-lookup"><span data-stu-id="79eb7-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="79eb7-179">Esta declaração de método também segue um idioma padrão no qual os tipos de entrada e saídas são `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="79eb7-180">Essa prática permite que os métodos LINQ sejam encadeados para executar consultas mais complexas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="79eb7-181">Naturalmente, como você dividiu o baralho em metades, precisará unir essas metades.</span><span class="sxs-lookup"><span data-stu-id="79eb7-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="79eb7-182">No código, isso significa que você vai enumerar as duas sequências adquiridas por meio de <xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> ao mesmo tempo, *`interleaving`* os elementos e criará uma sequência: seu baralho não embaralhado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="79eb7-183">Escrever um método LINQ que funciona com duas sequências exige que você compreenda como <xref:System.Collections.Generic.IEnumerable%601> funciona.</span><span class="sxs-lookup"><span data-stu-id="79eb7-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="79eb7-184">A interface <xref:System.Collections.Generic.IEnumerable%601> tem um método: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="79eb7-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="79eb7-185">O objeto retornado por <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> tem um método para mover para o próximo elemento e uma propriedade que recupera o elemento atual na sequência.</span><span class="sxs-lookup"><span data-stu-id="79eb7-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="79eb7-186">Você usará esses dois membros para enumerar a coleção e retornar os elementos.</span><span class="sxs-lookup"><span data-stu-id="79eb7-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="79eb7-187">Esse método de Intercalação será um método iterador, portanto, em vez de criar uma coleção e retornar a coleção, você usará a sintaxe `yield return` mostrada acima.</span><span class="sxs-lookup"><span data-stu-id="79eb7-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="79eb7-188">Aqui está a implementação desse método:</span><span class="sxs-lookup"><span data-stu-id="79eb7-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="79eb7-189">Agora que você escreveu esse método, vá até o método `Main` e embaralhe uma vez:</span><span class="sxs-lookup"><span data-stu-id="79eb7-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="79eb7-190">Comparações</span><span class="sxs-lookup"><span data-stu-id="79eb7-190">Comparisons</span></span>

<span data-ttu-id="79eb7-191">Quantos embaralhamentos são necessários para colocar o baralho em sua ordem original?</span><span class="sxs-lookup"><span data-stu-id="79eb7-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="79eb7-192">Para descobrir, você precisará escrever um método que determina se duas sequências são iguais.</span><span class="sxs-lookup"><span data-stu-id="79eb7-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="79eb7-193">Depois de ter esse método, você precisará colocar o código de embaralhamento em um loop e verificar quando a apresentação estiver na ordem.</span><span class="sxs-lookup"><span data-stu-id="79eb7-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="79eb7-194">Escrever um método para determinar se as duas sequências são iguais deve ser simples.</span><span class="sxs-lookup"><span data-stu-id="79eb7-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="79eb7-195">É uma estrutura semelhante para o método que você escreveu para embaralhar as cartas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="79eb7-196">Somente desta vez, em vez de o `yield return`rendimento retornar cada elemento, você comparará os elementos correspondentes de cada sequência.</span><span class="sxs-lookup"><span data-stu-id="79eb7-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="79eb7-197">Quando toda a sequência tiver sido enumerada, se os elementos corresponderem, as sequências serão as mesmas:</span><span class="sxs-lookup"><span data-stu-id="79eb7-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="79eb7-198">Isso mostra uma segunda linguagem LINQ: métodos de terminal.</span><span class="sxs-lookup"><span data-stu-id="79eb7-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="79eb7-199">Eles consideram uma sequência como entrada (ou, neste caso, duas sequências) e retornam um único valor escalar.</span><span class="sxs-lookup"><span data-stu-id="79eb7-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="79eb7-200">Ao usar métodos de terminal, eles são sempre o método final em uma cadeia de métodos para uma consulta LINQ, por isso, o nome "terminal".</span><span class="sxs-lookup"><span data-stu-id="79eb7-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="79eb7-201">Você pode ver isso em ação ao usá-lo para determinar quando o baralho está em sua ordem original.</span><span class="sxs-lookup"><span data-stu-id="79eb7-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="79eb7-202">Coloque o código de embaralhamento dentro de um loop e pare quando a sequência estiver em sua ordem original, aplicando o método `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="79eb7-203">Você pode ver que esse sempre será o método final em qualquer consulta, porque ele retorna um valor único em vez de uma sequência:</span><span class="sxs-lookup"><span data-stu-id="79eb7-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="79eb7-204">Execute o código que obtivemos até agora e observe como o baralho é reorganizado em cada embaralhamento.</span><span class="sxs-lookup"><span data-stu-id="79eb7-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="79eb7-205">Após 8 embaralhamentos (iterações do loop do-while), o baralho retorna à configuração original que estava quando você o criou pela primeira vez a partir da consulta LINQ inicial.</span><span class="sxs-lookup"><span data-stu-id="79eb7-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="79eb7-206">Otimizações</span><span class="sxs-lookup"><span data-stu-id="79eb7-206">Optimizations</span></span>

<span data-ttu-id="79eb7-207">O exemplo que você compilou até agora executa um *embaralhamento externo*, no qual as cartas superiores e inferiores permanecem as mesmas em cada execução.</span><span class="sxs-lookup"><span data-stu-id="79eb7-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="79eb7-208">Vamos fazer uma alteração: em vez disso, usaremos um *embaralhamento interno*, em que todas as 52 cartas trocam de posição.</span><span class="sxs-lookup"><span data-stu-id="79eb7-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="79eb7-209">Para um embaralhamento interno, intercale o baralho para que a primeira carta da metade inferior torne-se a primeira carta do baralho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="79eb7-210">Isso significa que a última carta na metade superior torna-se a carta inferior.</span><span class="sxs-lookup"><span data-stu-id="79eb7-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="79eb7-211">Essa é uma alteração simples em uma única linha de código.</span><span class="sxs-lookup"><span data-stu-id="79eb7-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="79eb7-212">Atualize a consulta atual de embaralhamento, alternando as posições de <xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="79eb7-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="79eb7-213">Isso alterará a ordem das metades superior e inferior do baralho:</span><span class="sxs-lookup"><span data-stu-id="79eb7-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="79eb7-214">Execute o programa novamente e você verá que leva 52 iterações para o baralho ser reordenado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="79eb7-215">Você também começará a observar algumas degradações de desempenho graves à medida que o programa continuar a ser executado.</span><span class="sxs-lookup"><span data-stu-id="79eb7-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="79eb7-216">Existem muitas razões para isso.</span><span class="sxs-lookup"><span data-stu-id="79eb7-216">There are a number of reasons for this.</span></span> <span data-ttu-id="79eb7-217">Você pode abordar uma das principais causas dessa queda de desempenho: uso ineficiente da [*avaliação lenta*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="79eb7-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="79eb7-218">Em resumo, a avaliação lenta informa que a avaliação de uma instrução não será executada até que seu valor seja necessário.</span><span class="sxs-lookup"><span data-stu-id="79eb7-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="79eb7-219">Consultas LINQ são instruções avaliadas lentamente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="79eb7-220">As sequências são geradas somente quando os elementos são solicitados.</span><span class="sxs-lookup"><span data-stu-id="79eb7-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="79eb7-221">Geralmente, esse é o principal benefício do LINQ.</span><span class="sxs-lookup"><span data-stu-id="79eb7-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="79eb7-222">No entanto, em uso como esse programa, isso causa um crescimento exponencial no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="79eb7-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="79eb7-223">Lembre-se de que geramos o baralho original usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="79eb7-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="79eb7-224">Cada embaralhamento é gerado executando três consultas LINQ no baralho anterior.</span><span class="sxs-lookup"><span data-stu-id="79eb7-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="79eb7-225">Todos eles são executados lentamente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-225">All these are performed lazily.</span></span> <span data-ttu-id="79eb7-226">Isso também significa que eles são executados novamente sempre que a sequência é solicitada.</span><span class="sxs-lookup"><span data-stu-id="79eb7-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="79eb7-227">Ao obter a 52ª iteração, você estará regenerando o baralho original muitas e muitas vezes.</span><span class="sxs-lookup"><span data-stu-id="79eb7-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="79eb7-228">Vamos escrever um log para demonstrar esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="79eb7-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="79eb7-229">Em seguida, você poderá corrigir isso.</span><span class="sxs-lookup"><span data-stu-id="79eb7-229">Then, you'll fix it.</span></span>

<span data-ttu-id="79eb7-230">Em seu arquivo `Extensions.cs`, digite ou copie o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="79eb7-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="79eb7-231">Esse método de extensão cria um novo arquivo chamado `debug.log` em seu diretório do projeto, e registra qual consulta está sendo executada atualmente para o arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="79eb7-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="79eb7-232">Este método de extensão pode ser anexado a qualquer consulta para marcar que a consulta foi executada.</span><span class="sxs-lookup"><span data-stu-id="79eb7-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="79eb7-233">Você verá um rabisco vermelho sob `File`, que significa que ele não existe.</span><span class="sxs-lookup"><span data-stu-id="79eb7-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="79eb7-234">Ele não será compilado, pois o compilador não sabe o que é `File`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="79eb7-235">Para resolver esse problema, é preciso que você adicione a linha de código a seguir abaixo da primeira linha em `Extensions.cs`:</span><span class="sxs-lookup"><span data-stu-id="79eb7-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="79eb7-236">Isso deve resolver o problema e o erro vermelho desaparece.</span><span class="sxs-lookup"><span data-stu-id="79eb7-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="79eb7-237">Em seguida, instrumente a definição de cada consulta com uma mensagem de log:</span><span class="sxs-lookup"><span data-stu-id="79eb7-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="79eb7-238">Observe que você não precisa fazer o registro sempre que acessar uma consulta.</span><span class="sxs-lookup"><span data-stu-id="79eb7-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="79eb7-239">Você faz o registro ao criar a consulta original.</span><span class="sxs-lookup"><span data-stu-id="79eb7-239">You log only when you create the original query.</span></span> <span data-ttu-id="79eb7-240">O programa ainda leva muito tempo para ser executado, mas agora você pode ver o motivo.</span><span class="sxs-lookup"><span data-stu-id="79eb7-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="79eb7-241">Se você não tiver paciência para executar o embaralhamento interno com o registro em log ativado, volte para o embaralhamento externo.</span><span class="sxs-lookup"><span data-stu-id="79eb7-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="79eb7-242">Você ainda verá os efeitos da avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="79eb7-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="79eb7-243">Em uma execução, ele faz 2592 consultas, incluindo a geração de todos os valores e naipes.</span><span class="sxs-lookup"><span data-stu-id="79eb7-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="79eb7-244">Aqui, você pode melhorar o desempenho do código para reduzir o número de execuções feitas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="79eb7-245">Uma correção simples possível é *armazenar em cache* os resultados da consulta do LINQ original que constrói o baralho de cartas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="79eb7-246">Atualmente, você executa as consultas novamente sempre que o loop do-while passa por uma iteração, construindo novamente o baralho de cartas e o embaralhamento de novo todas as vezes.</span><span class="sxs-lookup"><span data-stu-id="79eb7-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="79eb7-247">Para armazenar em cache o baralho de cartas, aproveite os métodos LINQ <xref:System.Linq.Enumerable.ToArray%2A> e <xref:System.Linq.Enumerable.ToList%2A>; ao anexá-los às consultas, eles executarão as mesmas ações paras quais foram instruídos, mas agora armazenarão os resultados em uma matriz ou lista, dependendo de qual método você optar por chamar.</span><span class="sxs-lookup"><span data-stu-id="79eb7-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="79eb7-248">Anexe o método LINQ <xref:System.Linq.Enumerable.ToArray%2A> às duas consultas e execute o programa novamente:</span><span class="sxs-lookup"><span data-stu-id="79eb7-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="79eb7-249">Agora, o embaralhamento externo contém 30 consultas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="79eb7-250">Execute novamente com o embaralhamento interno e você verá melhorias semelhantes: agora, executa 162 consultas.</span><span class="sxs-lookup"><span data-stu-id="79eb7-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="79eb7-251">Observe que esse exemplo é **projetado** para realçar os casos de uso em que a avaliação lenta pode causar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="79eb7-252">Embora seja importante ver onde a avaliação lenta pode afetar o desempenho do código, é igualmente importante entender que nem todas as consultas devem ser executadas avidamente.</span><span class="sxs-lookup"><span data-stu-id="79eb7-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="79eb7-253">O desempenho incorrido sem usar <xref:System.Linq.Enumerable.ToArray%2A> ocorre porque cada nova disposição do baralho de cartas é criada com base na disposição anterior.</span><span class="sxs-lookup"><span data-stu-id="79eb7-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="79eb7-254">Usar a avaliação lenta significa que cada nova disposição do baralho é criada do baralho original, até mesmo a execução do código que criou o `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="79eb7-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="79eb7-255">Isso causa uma grande quantidade de trabalho extra.</span><span class="sxs-lookup"><span data-stu-id="79eb7-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="79eb7-256">Na prática, alguns algoritmos funcionam bem usando a avaliação detalhada, e outros executam funcionam melhor usando a avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="79eb7-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="79eb7-257">Para o uso diário, a avaliação lenta é uma opção melhor quando a fonte de dados é um processo separado, como um mecanismo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79eb7-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="79eb7-258">Para os bancos de dados, a avaliação lenta permite que as consultas mais complexas executem apenas uma viagem de ida e volta para o processo de banco de dados e de volta para o restante do seu código.</span><span class="sxs-lookup"><span data-stu-id="79eb7-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="79eb7-259">O LINQ é flexível, não importa se você optar por utilizar a avaliação lenta ou detalhada, portanto, meça seus processos e escolha o tipo de avaliação que ofereça o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="79eb7-260">Conclusão</span><span class="sxs-lookup"><span data-stu-id="79eb7-260">Conclusion</span></span>

<span data-ttu-id="79eb7-261">Neste projeto, abordamos:</span><span class="sxs-lookup"><span data-stu-id="79eb7-261">In this project, you covered:</span></span>
- <span data-ttu-id="79eb7-262">o uso de consultas LINQ para agregar dados em uma sequência significativa</span><span class="sxs-lookup"><span data-stu-id="79eb7-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="79eb7-263">a produção de métodos de Extensão para adicionar nossa própria funcionalidade personalizada a consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="79eb7-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="79eb7-264">a localização de áreas em nosso código nas quais nossas consultas LINQ podem enfrentar problemas de desempenho, como diminuição da velocidade</span><span class="sxs-lookup"><span data-stu-id="79eb7-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="79eb7-265">avaliação lenta e detalhada com relação às consultas LINQ, e as implicações que elas podem ter no desempenho da consulta</span><span class="sxs-lookup"><span data-stu-id="79eb7-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="79eb7-266">Além do LINQ, você aprendeu um pouco sobre uma técnica usada por mágicos para truques de carta.</span><span class="sxs-lookup"><span data-stu-id="79eb7-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="79eb7-267">Os mágicos usam o embaralhamento Faro porque podem controlar onde cada carta fica no baralho.</span><span class="sxs-lookup"><span data-stu-id="79eb7-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="79eb7-268">Agora que você sabe, não conte para os outros!</span><span class="sxs-lookup"><span data-stu-id="79eb7-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="79eb7-269">Para saber mais sobre o LINQ, consulte:</span><span class="sxs-lookup"><span data-stu-id="79eb7-269">For more information on LINQ, see:</span></span>
- [<span data-ttu-id="79eb7-270">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="79eb7-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="79eb7-271">Introdução ao LINQ</span><span class="sxs-lookup"><span data-stu-id="79eb7-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="79eb7-272">Operações de consulta LINQ básica (C#)</span><span class="sxs-lookup"><span data-stu-id="79eb7-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [<span data-ttu-id="79eb7-273">Transformações de dados com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="79eb7-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [<span data-ttu-id="79eb7-274">Sintaxe de consulta e sintaxe de método em LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="79eb7-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [<span data-ttu-id="79eb7-275">Recursos do C# que dão suporte a LINQ</span><span class="sxs-lookup"><span data-stu-id="79eb7-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
