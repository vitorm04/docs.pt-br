---
title: Instruções de nível superior – tutorial em C#
description: Este tutorial mostra como você pode usar as instruções de nível superior para testar e provar os conceitos enquanto explora suas ideias
ms.date: 10/28/2020
ms.openlocfilehash: 210fbd83bf4677061cab303089d0b27f1a4a7d01
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189386"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="16d2a-103">Tutorial: explorar ideias usando instruções de nível superior para criar código conforme você aprende</span><span class="sxs-lookup"><span data-stu-id="16d2a-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="16d2a-104">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="16d2a-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="16d2a-105">Conheça as regras que regem o uso de instruções de nível superior.</span><span class="sxs-lookup"><span data-stu-id="16d2a-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="16d2a-106">Use as instruções de nível superior para explorar os algoritmos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="16d2a-107">Refatorar explorações em componentes reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="16d2a-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16d2a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="16d2a-108">Prerequisites</span></span>

<span data-ttu-id="16d2a-109">Você precisará configurar seu computador para executar o .NET 5, que inclui o compilador C# 9.</span><span class="sxs-lookup"><span data-stu-id="16d2a-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="16d2a-110">O compilador do C# 9 está disponível a partir do [Visual Studio 2019 versão 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) ou do [SDK do .NET 5,0](https://dot.net/get-dotnet5).</span><span class="sxs-lookup"><span data-stu-id="16d2a-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="16d2a-111">Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16d2a-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="16d2a-112">Comece a explorar</span><span class="sxs-lookup"><span data-stu-id="16d2a-112">Start exploring</span></span>

<span data-ttu-id="16d2a-113">As instruções de nível superior permitem evitar a cerimônia extra necessária colocando o ponto de entrada do programa em um método estático em uma classe.</span><span class="sxs-lookup"><span data-stu-id="16d2a-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="16d2a-114">O ponto de partida típico para um novo aplicativo de console é semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="16d2a-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="16d2a-115">O código anterior é o resultado da execução do `dotnet new console` comando e da criação de um novo aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="16d2a-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="16d2a-116">Essas 11 linhas contêm apenas uma linha de código executável.</span><span class="sxs-lookup"><span data-stu-id="16d2a-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="16d2a-117">Você pode simplificar esse programa com o novo recurso de instruções de nível superior.</span><span class="sxs-lookup"><span data-stu-id="16d2a-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="16d2a-118">Isso permite remover tudo, exceto duas das linhas deste programa:</span><span class="sxs-lookup"><span data-stu-id="16d2a-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="16d2a-119">Essa ação simplifica o que é necessário para começar a explorar novas ideias.</span><span class="sxs-lookup"><span data-stu-id="16d2a-119">This action simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="16d2a-120">Você pode usar instruções de nível superior para cenários de script ou para explorar.</span><span class="sxs-lookup"><span data-stu-id="16d2a-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="16d2a-121">Depois de trabalhar com as noções básicas, você pode começar a refatorar o código e criar métodos, classes ou outros assemblies para componentes reutilizáveis que você criou.</span><span class="sxs-lookup"><span data-stu-id="16d2a-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="16d2a-122">As instruções de nível superior permitem a rápida experimentação e tutoriais iniciantes.</span><span class="sxs-lookup"><span data-stu-id="16d2a-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="16d2a-123">Eles também fornecem um caminho suave de experimentação para programas completos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="16d2a-124">As instruções de nível superior são executadas na ordem em que aparecem no arquivo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="16d2a-125">Instruções de nível superior só podem ser usadas em um arquivo de origem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="16d2a-126">O compilador gerará um erro se você usá-los em mais de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="16d2a-127">Criar uma máquina de resposta do .NET mágico</span><span class="sxs-lookup"><span data-stu-id="16d2a-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="16d2a-128">Para este tutorial, vamos criar um aplicativo de console que responde a uma pergunta "Sim" ou "não" com uma resposta aleatória.</span><span class="sxs-lookup"><span data-stu-id="16d2a-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="16d2a-129">Você criará a funcionalidade passo a passo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="16d2a-130">Você pode se concentrar em sua tarefa em vez de na cerimônia necessária para a estrutura de um programa típico.</span><span class="sxs-lookup"><span data-stu-id="16d2a-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="16d2a-131">Em seguida, quando estiver satisfeito com a funcionalidade, você poderá refatorar o aplicativo como desejar.</span><span class="sxs-lookup"><span data-stu-id="16d2a-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="16d2a-132">Um bom ponto de partida é escrever a pergunta de volta ao console.</span><span class="sxs-lookup"><span data-stu-id="16d2a-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="16d2a-133">Você pode começar escrevendo o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="16d2a-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="16d2a-134">Você não declara uma `args` variável.</span><span class="sxs-lookup"><span data-stu-id="16d2a-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="16d2a-135">Para o arquivo de origem único que contém as instruções de nível superior, o compilador reconhece `args` para significar os argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="16d2a-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="16d2a-136">O tipo de args é a `string[]` , como em todos os programas em C#.</span><span class="sxs-lookup"><span data-stu-id="16d2a-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="16d2a-137">Você pode testar seu código executando o seguinte `dotnet run` comando:</span><span class="sxs-lookup"><span data-stu-id="16d2a-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="16d2a-138">Os argumentos após o `--` na linha de comando são passados para o programa.</span><span class="sxs-lookup"><span data-stu-id="16d2a-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="16d2a-139">Você pode ver o tipo da `args` variável, pois isso é o que é impresso no console:</span><span class="sxs-lookup"><span data-stu-id="16d2a-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="16d2a-140">Para gravar a pergunta no console, você precisará enumerar os argumentos e separá-los com um espaço.</span><span class="sxs-lookup"><span data-stu-id="16d2a-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="16d2a-141">Substitua a `WriteLine` chamada pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="16d2a-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

<span data-ttu-id="16d2a-142">Agora, quando você executar o programa, ele exibirá corretamente a pergunta como uma cadeia de caracteres de argumentos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="16d2a-143">Responder com uma resposta aleatória</span><span class="sxs-lookup"><span data-stu-id="16d2a-143">Respond with a random answer</span></span>

<span data-ttu-id="16d2a-144">Depois de ecoar a pergunta, você pode adicionar o código para gerar a resposta aleatória.</span><span class="sxs-lookup"><span data-stu-id="16d2a-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="16d2a-145">Comece adicionando uma matriz de possíveis respostas:</span><span class="sxs-lookup"><span data-stu-id="16d2a-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

<span data-ttu-id="16d2a-146">Essa matriz tem 12 respostas que são afirmativo, seis que não são confirmadas e seis que são negativas.</span><span class="sxs-lookup"><span data-stu-id="16d2a-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="16d2a-147">Em seguida, adicione o seguinte código para gerar e exibir uma resposta aleatória da matriz:</span><span class="sxs-lookup"><span data-stu-id="16d2a-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

<span data-ttu-id="16d2a-148">Você pode executar o aplicativo novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="16d2a-148">You can run the application again to see the results.</span></span> <span data-ttu-id="16d2a-149">Você deverá ver algo semelhante à seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="16d2a-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="16d2a-150">Esse código responde às perguntas, mas vamos adicionar mais um recurso.</span><span class="sxs-lookup"><span data-stu-id="16d2a-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="16d2a-151">Você gostaria que seu aplicativo de pergunta simulasse pensar sobre a resposta.</span><span class="sxs-lookup"><span data-stu-id="16d2a-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="16d2a-152">Você pode fazer isso adicionando um pouco de animação ASCII e pausando enquanto trabalha.</span><span class="sxs-lookup"><span data-stu-id="16d2a-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="16d2a-153">Adicione o seguinte código após a linha que ecoa a pergunta:</span><span class="sxs-lookup"><span data-stu-id="16d2a-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="16d2a-154">Você também precisará adicionar uma `using` instrução à parte superior do arquivo de origem:</span><span class="sxs-lookup"><span data-stu-id="16d2a-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="16d2a-155">As `using` instruções devem ser anteriores a qualquer outra instrução no arquivo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="16d2a-156">Caso contrário, é um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="16d2a-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="16d2a-157">Você pode executar o programa novamente e ver a animação.</span><span class="sxs-lookup"><span data-stu-id="16d2a-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="16d2a-158">Isso faz uma melhor experiência.</span><span class="sxs-lookup"><span data-stu-id="16d2a-158">That makes a better experience.</span></span> <span data-ttu-id="16d2a-159">Experimente o comprimento do atraso para corresponder ao seu gosto.</span><span class="sxs-lookup"><span data-stu-id="16d2a-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="16d2a-160">O código anterior cria um conjunto de linhas giratórias separadas por um espaço.</span><span class="sxs-lookup"><span data-stu-id="16d2a-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="16d2a-161">A adição da `await` palavra-chave instrui o compilador a gerar o ponto de entrada do programa como um método que tem o `async` modificador e retorna um <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="16d2a-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16d2a-162">Este programa não retorna um valor, portanto, o ponto de entrada do programa retorna um `Task` .</span><span class="sxs-lookup"><span data-stu-id="16d2a-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="16d2a-163">Se o seu programa retornar um valor inteiro, você adicionaria uma instrução return ao final de suas instruções de nível superior.</span><span class="sxs-lookup"><span data-stu-id="16d2a-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="16d2a-164">Essa instrução de retorno especificaria o valor inteiro a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="16d2a-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="16d2a-165">Se as instruções de nível superior incluírem uma `await` expressão, o tipo de retorno se tornará <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="16d2a-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="16d2a-166">Refatoração para o futuro</span><span class="sxs-lookup"><span data-stu-id="16d2a-166">Refactoring for the future</span></span>

<span data-ttu-id="16d2a-167">Seu programa deve ser semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="16d2a-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="16d2a-168">O código anterior é razoável.</span><span class="sxs-lookup"><span data-stu-id="16d2a-168">The preceding code is reasonable.</span></span> <span data-ttu-id="16d2a-169">Funciona.</span><span class="sxs-lookup"><span data-stu-id="16d2a-169">It works.</span></span> <span data-ttu-id="16d2a-170">Mas não é reutilizável.</span><span class="sxs-lookup"><span data-stu-id="16d2a-170">But it isn't reusable.</span></span> <span data-ttu-id="16d2a-171">Agora que o aplicativo está funcionando, é hora de retirar as partes reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="16d2a-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="16d2a-172">Um candidato é o código que exibe a animação em espera.</span><span class="sxs-lookup"><span data-stu-id="16d2a-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="16d2a-173">Esse trecho de código pode se tornar um método:</span><span class="sxs-lookup"><span data-stu-id="16d2a-173">That snippet can become a method:</span></span>

<span data-ttu-id="16d2a-174">Você pode começar criando uma função local em seu arquivo.</span><span class="sxs-lookup"><span data-stu-id="16d2a-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="16d2a-175">Substitua a animação atual pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="16d2a-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="16d2a-176">O código anterior cria uma função local dentro do método Main.</span><span class="sxs-lookup"><span data-stu-id="16d2a-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="16d2a-177">Isso ainda não pode ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="16d2a-177">That's still not reusable.</span></span> <span data-ttu-id="16d2a-178">Portanto, extraia esse código em uma classe.</span><span class="sxs-lookup"><span data-stu-id="16d2a-178">So, extract that code into a class.</span></span> <span data-ttu-id="16d2a-179">Crie um novo arquivo chamado *Utilities.cs* e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="16d2a-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="16d2a-180">As instruções de nível superior só podem estar em um arquivo, e esse arquivo não pode conter namespaces ou tipos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-180">Top-level statements can only be in one file, and that file cannot contain namespaces or types.</span></span>

<span data-ttu-id="16d2a-181">Por fim, você pode limpar o código de animação para remover alguma duplicação:</span><span class="sxs-lookup"><span data-stu-id="16d2a-181">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utiliities.cs" ID="Animation":::

<span data-ttu-id="16d2a-182">Agora você tem um aplicativo completo e refatorou as partes reutilizáveis para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="16d2a-182">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span>

## <a name="summary"></a><span data-ttu-id="16d2a-183">Resumo</span><span class="sxs-lookup"><span data-stu-id="16d2a-183">Summary</span></span>

<span data-ttu-id="16d2a-184">As instruções de nível superior facilitam a criação de programas simples para serem usados para explorar novos algoritmos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-184">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="16d2a-185">Você pode experimentar algoritmos experimentando trechos de código diferentes.</span><span class="sxs-lookup"><span data-stu-id="16d2a-185">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="16d2a-186">Depois de aprender o que funciona, você pode refatorar o código para ser mais passível de manutenção.</span><span class="sxs-lookup"><span data-stu-id="16d2a-186">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="16d2a-187">Instruções de nível superior simplificam programas baseados em aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="16d2a-187">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="16d2a-188">Isso inclui o Azure functions, ações do GitHub e outros utilitários pequenos.</span><span class="sxs-lookup"><span data-stu-id="16d2a-188">These include Azure functions, GitHub actions, and other small utilities.</span></span>
