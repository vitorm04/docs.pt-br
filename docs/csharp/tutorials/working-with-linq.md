---
title: Trabalhando com LINQ
description: Este tutorial ensina a gerar sequências com LINQ, escrever métodos para uso em consultas LINQ e diferenciar entre avaliação lenta e detalhada.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e5f9baab13cddfb9e294de1e1a6ce967ccbe0813
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="fd890-103">Trabalhando com LINQ</span><span class="sxs-lookup"><span data-stu-id="fd890-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="fd890-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="fd890-104">Introduction</span></span>

<span data-ttu-id="fd890-105">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="fd890-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="fd890-106">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="fd890-106">You’ll learn:</span></span>

*   <span data-ttu-id="fd890-107">Como gerar sequências com LINQ</span><span class="sxs-lookup"><span data-stu-id="fd890-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="fd890-108">Como escrever métodos que podem ser facilmente usados em consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd890-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="fd890-109">Como distinguir entre uma avaliação lenta e uma detalhada.</span><span class="sxs-lookup"><span data-stu-id="fd890-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="fd890-110">Você aprenderá essas técnicas ao compilar um aplicativo que demonstra uma das habilidades básicas de qualquer mágico: o [embaralhamento faro](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="fd890-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="fd890-111">Em resumo, um embaralhamento faro é uma técnica em que você divide um baralho de cartas exatamente na metade, então as cartas de cada metade são colocadas em ordem aleatória até recriar o conjunto original.</span><span class="sxs-lookup"><span data-stu-id="fd890-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="fd890-112">Os mágicos usam essa técnica porque cada carta é fica em um local conhecido após o embaralhamento e a ordem é um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="fd890-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="fd890-113">Para nossos propósitos, vamos examinar rapidamente as sequências de manipulação de dados.</span><span class="sxs-lookup"><span data-stu-id="fd890-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="fd890-114">O aplicativo que você criará construirá um baralho de cartas e, em seguida, executará uma sequência de embaralhamento, sempre gravando a sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="fd890-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="fd890-115">Você também comparará a ordem atualizada com a ordem original.</span><span class="sxs-lookup"><span data-stu-id="fd890-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="fd890-116">Este tutorial tem várias etapas.</span><span class="sxs-lookup"><span data-stu-id="fd890-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="fd890-117">Após cada etapa, você poderá executar o aplicativo e ver o progresso.</span><span class="sxs-lookup"><span data-stu-id="fd890-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="fd890-118">Você também poderá ver o [exemplo concluído](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) no repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd890-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="fd890-119">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="fd890-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd890-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fd890-120">Prerequisites</span></span>

<span data-ttu-id="fd890-121">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd890-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="fd890-122">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="fd890-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="fd890-123">Você pode executar esse aplicativo no Windows, Ubuntu Linux, OS X ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="fd890-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="fd890-124">Você precisará instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="fd890-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="fd890-125">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="fd890-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="fd890-126">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="fd890-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="fd890-127">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="fd890-127">Create the Application</span></span>

<span data-ttu-id="fd890-128">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fd890-128">The first step is to create a new application.</span></span> <span data-ttu-id="fd890-129">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fd890-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="fd890-130">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fd890-130">Make that the current directory.</span></span> <span data-ttu-id="fd890-131">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="fd890-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="fd890-132">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="fd890-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="fd890-133">Se você nunca usou C# antes, [este tutorial](console-teleprompter.md) explicará a estrutura de um programa C#.</span><span class="sxs-lookup"><span data-stu-id="fd890-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="fd890-134">Você pode ler e, em seguida, voltar aqui para saber mais sobre o LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd890-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="fd890-135">Criando o arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="fd890-135">Creating the Data Set</span></span>

<span data-ttu-id="fd890-136">Vamos começar criando um baralho.</span><span class="sxs-lookup"><span data-stu-id="fd890-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="fd890-137">Você fará isso usando uma consulta LINQ com duas fontes (uma para os quatro naipes, uma para os treze valores).</span><span class="sxs-lookup"><span data-stu-id="fd890-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="fd890-138">Você combinará essas fontes em um baralho com 52 cartas.</span><span class="sxs-lookup"><span data-stu-id="fd890-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="fd890-139">Uma instrução `Console.WriteLine` dentro de um loop `foreach` exibe as cartas.</span><span class="sxs-lookup"><span data-stu-id="fd890-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="fd890-140">Aqui está a consulta:</span><span class="sxs-lookup"><span data-stu-id="fd890-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="fd890-141">As várias cláusulas `from` produzem um `SelectMany`, que cria uma única sequência da combinação entre cada elemento na primeira sequência com cada elemento na segunda sequência.</span><span class="sxs-lookup"><span data-stu-id="fd890-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="fd890-142">A ordem é importante para nossos objetivos.</span><span class="sxs-lookup"><span data-stu-id="fd890-142">The order is important for our purposes.</span></span> <span data-ttu-id="fd890-143">O primeiro elemento na primeira sequência de fonte (naipes) é combinado com cada elemento na segunda sequência (valores).</span><span class="sxs-lookup"><span data-stu-id="fd890-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="fd890-144">Isso produz todas as treze cartas do primeiro naipe.</span><span class="sxs-lookup"><span data-stu-id="fd890-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="fd890-145">Esse processo é repetido com cada elemento na primeira sequência (naipes).</span><span class="sxs-lookup"><span data-stu-id="fd890-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="fd890-146">O resultado final é um baralho ordenado por naipes, seguido pelos valores.</span><span class="sxs-lookup"><span data-stu-id="fd890-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="fd890-147">Em seguida, você precisará compilar os métodos Suits() e Ranks().</span><span class="sxs-lookup"><span data-stu-id="fd890-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="fd890-148">Vamos começar com um conjunto muito simples de *métodos de iterador* que gera a sequência como um enumerável de cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="fd890-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
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

<span data-ttu-id="fd890-149">Esses dois métodos utilizam a sintaxe `yield return` para produzir uma sequência à medida que eles são executados.</span><span class="sxs-lookup"><span data-stu-id="fd890-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="fd890-150">O compilador compila um objeto que implementa `IEnumerable<T>` e gera a sequência de cadeias de caracteres conforme solicitado.</span><span class="sxs-lookup"><span data-stu-id="fd890-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="fd890-151">Vá em frente e execute o exemplo que você criou neste momento.</span><span class="sxs-lookup"><span data-stu-id="fd890-151">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="fd890-152">Ele exibirá todas as 52 cartas do baralho.</span><span class="sxs-lookup"><span data-stu-id="fd890-152">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="fd890-153">Talvez seja muito útil executar esse exemplo em um depurador para observar como os métodos `Suits()` e `Values()` são executados.</span><span class="sxs-lookup"><span data-stu-id="fd890-153">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="fd890-154">Você pode ver claramente que cada cadeia de caracteres em cada sequência é gerada apenas conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="fd890-154">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Janela de console mostrando o aplicativo gravando 52 cartas](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="fd890-156">Manipulando a ordem</span><span class="sxs-lookup"><span data-stu-id="fd890-156">Manipulating the Order</span></span>

<span data-ttu-id="fd890-157">Em seguida, vamos criar um método de utilitário que pode executar o embaralhamento.</span><span class="sxs-lookup"><span data-stu-id="fd890-157">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="fd890-158">A primeira etapa é dividir o baralho em dois.</span><span class="sxs-lookup"><span data-stu-id="fd890-158">The first step is to split the deck in two.</span></span> <span data-ttu-id="fd890-159">Os métodos `Take()` e `Skip()` que fazem parte das APIs do LINQ fornecem esse recurso para nós:</span><span class="sxs-lookup"><span data-stu-id="fd890-159">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="fd890-160">O método de embaralhamento não existe na biblioteca padrão, portanto você precisará escrever o seu.</span><span class="sxs-lookup"><span data-stu-id="fd890-160">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="fd890-161">Esse novo método ilustra várias técnicas que você usará com programas baseados em LINQ. Vamos explicar cada parte do método em etapas.</span><span class="sxs-lookup"><span data-stu-id="fd890-161">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="fd890-162">A assinatura do método cria um *método de extensão*:</span><span class="sxs-lookup"><span data-stu-id="fd890-162">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="fd890-163">Um método de extensão é um *método estático* de objetivo especial.</span><span class="sxs-lookup"><span data-stu-id="fd890-163">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="fd890-164">Você pode ver a adição do modificador `this` no primeiro argumento para o método.</span><span class="sxs-lookup"><span data-stu-id="fd890-164">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="fd890-165">Isso significa que você chama o método como se fosse um método de membro do tipo do primeiro argumento.</span><span class="sxs-lookup"><span data-stu-id="fd890-165">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="fd890-166">Os métodos de extensão podem ser declarados somente dentro de classes `static`, então vamos criar uma nova classe estática chamada `extensions` para essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="fd890-166">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="fd890-167">É necessário adicionar mais métodos de extensão nesse tutorial, e eles serão colocados na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="fd890-167">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="fd890-168">Esta declaração de método também segue um idioma padrão no qual os tipos de entrada e saídas são `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="fd890-168">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="fd890-169">Essa prática permite que os métodos LINQ sejam encadeados para executar consultas mais complexas.</span><span class="sxs-lookup"><span data-stu-id="fd890-169">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="fd890-170">Você enumerará as duas sequências de uma vez, intercalando os elementos e criando um objeto.</span><span class="sxs-lookup"><span data-stu-id="fd890-170">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="fd890-171">Escrever um método LINQ que funciona com duas sequências exige que você compreenda como `IEnumerable` funciona.</span><span class="sxs-lookup"><span data-stu-id="fd890-171">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="fd890-172">A interface `IEnumerable` tem um método: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="fd890-172">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="fd890-173">O objeto retornado por `GetEnumerator()` tem um método para mover para o próximo elemento e uma propriedade que recupera o elemento atual na sequência.</span><span class="sxs-lookup"><span data-stu-id="fd890-173">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="fd890-174">Você usará esses dois membros para enumerar a coleção e retornar os elementos.</span><span class="sxs-lookup"><span data-stu-id="fd890-174">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="fd890-175">Esse método de Intercalação será um método iterador, portanto, em vez de criar uma coleção e retornar a coleção, você usará a sintaxe `yield return` mostrada acima.</span><span class="sxs-lookup"><span data-stu-id="fd890-175">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="fd890-176">Aqui está a implementação desse método:</span><span class="sxs-lookup"><span data-stu-id="fd890-176">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="fd890-177">Agora que você escreveu esse método, vá até o método `Main` e embaralhe uma vez:</span><span class="sxs-lookup"><span data-stu-id="fd890-177">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
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

## <a name="comparisons"></a><span data-ttu-id="fd890-178">Comparações</span><span class="sxs-lookup"><span data-stu-id="fd890-178">Comparisons</span></span>

<span data-ttu-id="fd890-179">Vamos ver quantos embaralhamentos são necessários para colocar o baralho em sua ordem original.</span><span class="sxs-lookup"><span data-stu-id="fd890-179">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="fd890-180">Você precisará escrever um método que determina se duas sequências são iguais.</span><span class="sxs-lookup"><span data-stu-id="fd890-180">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="fd890-181">Depois de ter esse método, você precisará colocar o código de embaralhamento em um loop e verificar quando a apresentação estiver na ordem.</span><span class="sxs-lookup"><span data-stu-id="fd890-181">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="fd890-182">Escrever um método para determinar se as duas sequências são iguais deve ser simples.</span><span class="sxs-lookup"><span data-stu-id="fd890-182">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="fd890-183">É uma estrutura semelhante para o método que você escreveu para embaralhar as cartas.</span><span class="sxs-lookup"><span data-stu-id="fd890-183">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="fd890-184">Somente desta vez, em vez de o rendimento retornar cada elemento, você comparará os elementos correspondentes de cada sequência.</span><span class="sxs-lookup"><span data-stu-id="fd890-184">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="fd890-185">Quando toda a sequência tiver sido enumerada, se os elementos corresponderem, as sequências serão as mesmas:</span><span class="sxs-lookup"><span data-stu-id="fd890-185">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="fd890-186">Isso mostra uma segunda linguagem LINQ: métodos de terminal.</span><span class="sxs-lookup"><span data-stu-id="fd890-186">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="fd890-187">Eles consideram uma sequência como entrada (ou, neste caso, duas sequências) e retornam um único valor escalar.</span><span class="sxs-lookup"><span data-stu-id="fd890-187">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="fd890-188">Esses métodos, quando são usados, sempre são o método final de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="fd890-188">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="fd890-189">(Portanto, o nome).</span><span class="sxs-lookup"><span data-stu-id="fd890-189">(Hence the name).</span></span> 

<span data-ttu-id="fd890-190">Você pode ver isso em ação ao usá-lo para determinar quando o baralho está em sua ordem original.</span><span class="sxs-lookup"><span data-stu-id="fd890-190">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="fd890-191">Coloque o código de embaralhamento dentro de um loop e pare quando a sequência estiver em sua ordem original, aplicando o método `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="fd890-191">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="fd890-192">Você pode ver que esse sempre será o método final em qualquer consulta, porque ele retorna um valor único em vez de uma sequência:</span><span class="sxs-lookup"><span data-stu-id="fd890-192">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="fd890-193">Execute o exemplo e veja como o baralho é reorganizado em cada embaralhamento até que ele retorne à sua configuração original após 8 iterações.</span><span class="sxs-lookup"><span data-stu-id="fd890-193">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="fd890-194">Otimizações</span><span class="sxs-lookup"><span data-stu-id="fd890-194">Optimizations</span></span>

<span data-ttu-id="fd890-195">O exemplo que você compilou até agora executa um *embaralhamento externo*, no qual as cartas superiores e inferiores permanecem as mesmas em cada execução.</span><span class="sxs-lookup"><span data-stu-id="fd890-195">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="fd890-196">Vamos fazer uma alteração e executar um *embaralhamento interno*, no qual todas as 52 cartas trocam de posição.</span><span class="sxs-lookup"><span data-stu-id="fd890-196">Let's make one change, and run an *in shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="fd890-197">Para um embaralhamento interno, intercale o baralho para que a primeira carta da metade inferior torne-se a primeira carta do baralho.</span><span class="sxs-lookup"><span data-stu-id="fd890-197">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="fd890-198">Isso significa que a última carta na metade superior torna-se a carta inferior.</span><span class="sxs-lookup"><span data-stu-id="fd890-198">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="fd890-199">Isso é apenas uma alteração de uma linha.</span><span class="sxs-lookup"><span data-stu-id="fd890-199">That's just a one line change.</span></span> <span data-ttu-id="fd890-200">Atualize a chamada de embaralhamento para alterar a ordem das metades superior e inferior do baralho:</span><span class="sxs-lookup"><span data-stu-id="fd890-200">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="fd890-201">Execute o programa novamente e você verá que leva 52 iterações para o baralho ser reordenado.</span><span class="sxs-lookup"><span data-stu-id="fd890-201">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="fd890-202">Você também começará a observar algumas degradações de desempenho graves à medida que o programa continuar a ser executado.</span><span class="sxs-lookup"><span data-stu-id="fd890-202">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="fd890-203">Existem muitas razões para isso.</span><span class="sxs-lookup"><span data-stu-id="fd890-203">There are a number of reasons for this.</span></span> <span data-ttu-id="fd890-204">Vamos analisar uma das principais causas: uso ineficiente de *avaliação lenta*.</span><span class="sxs-lookup"><span data-stu-id="fd890-204">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="fd890-205">Consultas LINQ são avaliadas lentamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-205">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="fd890-206">As sequências são geradas somente quando os elementos são solicitados.</span><span class="sxs-lookup"><span data-stu-id="fd890-206">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="fd890-207">Geralmente, esse é o principal benefício do LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd890-207">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="fd890-208">No entanto, em uso como esse programa, isso causa um crescimento exponencial no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fd890-208">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="fd890-209">O baralho original foi gerado usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd890-209">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="fd890-210">Cada embaralhamento é gerado executando três consultas LINQ no baralho anterior.</span><span class="sxs-lookup"><span data-stu-id="fd890-210">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="fd890-211">Todos eles são executados lentamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-211">All these are performed lazily.</span></span> <span data-ttu-id="fd890-212">Isso também significa que eles são executados novamente sempre que a sequência é solicitada.</span><span class="sxs-lookup"><span data-stu-id="fd890-212">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="fd890-213">Ao obter a 52ª iteração, você estará regenerando o baralho original muitas e muitas vezes.</span><span class="sxs-lookup"><span data-stu-id="fd890-213">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="fd890-214">Vamos escrever um log para demonstrar esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="fd890-214">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="fd890-215">Em seguida, você poderá corrigir isso.</span><span class="sxs-lookup"><span data-stu-id="fd890-215">Then, you'll fix it.</span></span>

<span data-ttu-id="fd890-216">Este é um método de log que pode ser anexado a qualquer consulta para marcar a consulta executada.</span><span class="sxs-lookup"><span data-stu-id="fd890-216">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="fd890-217">Em seguida, instrumente a definição de cada consulta com uma mensagem de log:</span><span class="sxs-lookup"><span data-stu-id="fd890-217">Next, instrument the definition of each query with a log message:</span></span>

```csharp
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
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
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

<span data-ttu-id="fd890-218">Observe que você não precisa fazer o registro sempre que acessar uma consulta.</span><span class="sxs-lookup"><span data-stu-id="fd890-218">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="fd890-219">Você faz o registro ao criar a consulta original.</span><span class="sxs-lookup"><span data-stu-id="fd890-219">You log only when you create the original query.</span></span> <span data-ttu-id="fd890-220">O programa ainda leva muito tempo para ser executado, mas agora você pode ver o motivo.</span><span class="sxs-lookup"><span data-stu-id="fd890-220">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="fd890-221">Se você não tiver paciência para executar o embaralhamento interno com o registro em log ativado, volte para o embaralhamento externo.</span><span class="sxs-lookup"><span data-stu-id="fd890-221">If you run out of patience running the inner shuffle with logging turned on, switch back to the outer shuffle.</span></span> <span data-ttu-id="fd890-222">Você ainda verá os efeitos da avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="fd890-222">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="fd890-223">Em uma execução, ele faz 2592 consultas, incluindo a geração de todos os valores e naipes.</span><span class="sxs-lookup"><span data-stu-id="fd890-223">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="fd890-224">Há uma maneira fácil de atualizar este programa para evitar todas essas execuções.</span><span class="sxs-lookup"><span data-stu-id="fd890-224">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="fd890-225">Há métodos LINQ `ToArray()` e `ToList()` que causam a execução da consulta e armazenam os resultados em uma matriz ou lista, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-225">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="fd890-226">Você pode usar estes métodos para armazenar em cache os resultados de dados de uma consulta em vez de executar a consulta de origem novamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-226">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="fd890-227">Acrescente as consultas que geram os baralhos com uma chamada para `ToArray()` e execute a consulta novamente:</span><span class="sxs-lookup"><span data-stu-id="fd890-227">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="fd890-228">Execute novamente, e o embaralhamento externo será de até 30 consultas.</span><span class="sxs-lookup"><span data-stu-id="fd890-228">Run again, and the outer shuffle is down to 30 queries.</span></span> <span data-ttu-id="fd890-229">Execute novamente com o embaralhamento interno e você verá melhorias semelhantes.</span><span class="sxs-lookup"><span data-stu-id="fd890-229">Run again with the inner shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="fd890-230">(Ele agora executa 162 consultas).</span><span class="sxs-lookup"><span data-stu-id="fd890-230">(It now executes 162 queries).</span></span>

<span data-ttu-id="fd890-231">Não interprete incorretamente esse exemplo pensando que todas as consultas devem ser executadas cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-231">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="fd890-232">Este exemplo é projetado para realçar os casos de uso em que a avaliação lenta pode causar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="fd890-232">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="fd890-233">Isso ocorre porque cada nova disposição do baralho de cartas é criada com base na disposição anterior.</span><span class="sxs-lookup"><span data-stu-id="fd890-233">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="fd890-234">Usar a avaliação lenta significa que cada nova disposição do baralho é criada do baralho original, até mesmo a execução do código que criou o `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="fd890-234">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="fd890-235">Isso causa uma grande quantidade de trabalho extra.</span><span class="sxs-lookup"><span data-stu-id="fd890-235">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="fd890-236">Na prática, alguns algoritmos são muito melhores executados usando a avaliação rápida e outros executam muito melhor usando a avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="fd890-236">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="fd890-237">(Em geral, a avaliação lenta é uma opção muito melhor quando a fonte de dados é um processo separado, como um mecanismo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fd890-237">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="fd890-238">Nesses casos, a avaliação lenta permite que consultas mais complexas executem apenas uma viagem de ida e volta e para o processo de banco de dados.) O LINQ permite uma avaliação lenta e rápida.</span><span class="sxs-lookup"><span data-stu-id="fd890-238">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="fd890-239">Meça e escolha a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="fd890-239">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="fd890-240">Preparação para novos recursos</span><span class="sxs-lookup"><span data-stu-id="fd890-240">Preparing for New Features</span></span>

<span data-ttu-id="fd890-241">O código que você escreveu para este exemplo é um exemplo de como criar um protótipo simples que faz o trabalho.</span><span class="sxs-lookup"><span data-stu-id="fd890-241">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="fd890-242">Isso é uma ótima maneira de explorar um espaço problemático e, para muitos recursos, pode ser a melhor solução permanente.</span><span class="sxs-lookup"><span data-stu-id="fd890-242">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="fd890-243">Você terá aproveitado *tipos anônimos* para as cartas e cada carta será representada por cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fd890-243">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="fd890-244">Os *tipos anônimos* têm muitas vantagens de produtividade.</span><span class="sxs-lookup"><span data-stu-id="fd890-244">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="fd890-245">Você não precisa definir uma classe para representar o armazenamento.</span><span class="sxs-lookup"><span data-stu-id="fd890-245">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="fd890-246">O compilador gera o tipo para você.</span><span class="sxs-lookup"><span data-stu-id="fd890-246">The compiler generates the type for you.</span></span> <span data-ttu-id="fd890-247">O tipo gerado pelo compilador utiliza várias das melhores práticas para objetos de dados simples.</span><span class="sxs-lookup"><span data-stu-id="fd890-247">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="fd890-248">Ele é *imutável*, o que significa que nenhuma de suas propriedades pode ser alterada depois que ele for construído.</span><span class="sxs-lookup"><span data-stu-id="fd890-248">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="fd890-249">Os tipos anônimos são internos para um assembly, então eles não são vistos como parte da API pública para esse assembly.</span><span class="sxs-lookup"><span data-stu-id="fd890-249">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="fd890-250">Os tipos anônimos também contêm uma substituição do método `ToString()` que retorna uma cadeia de caracteres formatada com cada um dos valores.</span><span class="sxs-lookup"><span data-stu-id="fd890-250">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="fd890-251">Os tipos anônimos também têm desvantagens.</span><span class="sxs-lookup"><span data-stu-id="fd890-251">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="fd890-252">Eles não têm nomes acessíveis, portanto você não pode usá-los como argumentos ou valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="fd890-252">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="fd890-253">Você notará que todos os métodos acima que usaram esses tipos anônimos são métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="fd890-253">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="fd890-254">A substituição de `ToString()` pode não ser o que você deseja à medida que o aplicativo cria mais recursos.</span><span class="sxs-lookup"><span data-stu-id="fd890-254">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="fd890-255">O exemplo também usa cadeias de caracteres para o naipe e a classificação de cada carta.</span><span class="sxs-lookup"><span data-stu-id="fd890-255">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="fd890-256">Isso é bastante ilimitado.</span><span class="sxs-lookup"><span data-stu-id="fd890-256">That's quite open ended.</span></span> <span data-ttu-id="fd890-257">O sistema de tipo C# pode nos ajudar a tornar o código melhor, aproveitando tipos `enum` para esses valores.</span><span class="sxs-lookup"><span data-stu-id="fd890-257">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="fd890-258">Comece com os naipes.</span><span class="sxs-lookup"><span data-stu-id="fd890-258">Start with the suits.</span></span> <span data-ttu-id="fd890-259">Este é o momento perfeito para usar um `enum`:</span><span class="sxs-lookup"><span data-stu-id="fd890-259">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="fd890-260">O método `Suits()` também altera o tipo e a implementação:</span><span class="sxs-lookup"><span data-stu-id="fd890-260">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="fd890-261">Em seguida, faça a mesma alteração com a classificação das cartas:</span><span class="sxs-lookup"><span data-stu-id="fd890-261">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="fd890-262">E o método que gera as cartas:</span><span class="sxs-lookup"><span data-stu-id="fd890-262">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="fd890-263">Como limpeza final, vamos criar um tipo para representar a carta, em vez de depender de um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="fd890-263">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="fd890-264">Os tipos anônimos são ótimos para tipos simples e locais, mas, neste exemplo, a carta do jogo é um dos principais conceitos.</span><span class="sxs-lookup"><span data-stu-id="fd890-264">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="fd890-265">Ela deve ser de um tipo concreto.</span><span class="sxs-lookup"><span data-stu-id="fd890-265">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="fd890-266">Esse tipo usa *propriedades somente leitura autoimplementadas* que são definidas no construtor e não podem ser modificadas.</span><span class="sxs-lookup"><span data-stu-id="fd890-266">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="fd890-267">Ele também usa o recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) que facilita a formatação da saída da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fd890-267">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="fd890-268">Atualize a consulta que gera o baralho inicial para usar o novo tipo:</span><span class="sxs-lookup"><span data-stu-id="fd890-268">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="fd890-269">Compile e execute novamente.</span><span class="sxs-lookup"><span data-stu-id="fd890-269">Compile and run again.</span></span> <span data-ttu-id="fd890-270">A saída é um pouco mais limpa e o código é um pouco mais claro e pode ser estendido mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="fd890-270">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="fd890-271">Conclusão</span><span class="sxs-lookup"><span data-stu-id="fd890-271">Conclusion</span></span>

<span data-ttu-id="fd890-272">Esta amostra mostrou alguns dos métodos usados em LINQ e como criar seus próprios métodos que serão usados com facilidade com o código habilitado para LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd890-272">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="fd890-273">Ele também mostrou as diferenças entre a avaliação lenta e a rápida e o impacto que a decisão pode ter no desempenho.</span><span class="sxs-lookup"><span data-stu-id="fd890-273">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="fd890-274">Você aprendeu um pouco sobre uma técnica dos mágicos.</span><span class="sxs-lookup"><span data-stu-id="fd890-274">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="fd890-275">Os mágicos usam o embaralhamento porque eles podem controlar onde cada carta fica no baralho.</span><span class="sxs-lookup"><span data-stu-id="fd890-275">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="fd890-276">Em alguns truques, o mágico escolha uma pessoa para colocar a carta no topo do baralho e embaralha as cartas algumas vezes, sabendo onde a carta escolhida está.</span><span class="sxs-lookup"><span data-stu-id="fd890-276">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="fd890-277">Outras ilusões exigem que o baralho esteja disposto de uma determinada maneira.</span><span class="sxs-lookup"><span data-stu-id="fd890-277">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="fd890-278">Um mágico fará a disposição do baralho antes de realizar o truque.</span><span class="sxs-lookup"><span data-stu-id="fd890-278">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="fd890-279">Em seguida, ela embaralhará as cartas 5 vezes usando o embaralhamento externo.</span><span class="sxs-lookup"><span data-stu-id="fd890-279">Then she will shuffle the deck 5 times using an outer shuffle.</span></span> <span data-ttu-id="fd890-280">No palco, ele pode mostrar como é o embaralhamento e embaralhar mais três vezes e ter o baralho definido exatamente como deseja.</span><span class="sxs-lookup"><span data-stu-id="fd890-280">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
