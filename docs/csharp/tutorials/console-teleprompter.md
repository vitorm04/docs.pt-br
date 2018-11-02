---
title: Aplicativo do Console
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 9255ad9b1fefc828e767fb8e6ccc62b2eaf23fd6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183614"
---
# <a name="console-application"></a><span data-ttu-id="562d1-103">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="562d1-103">Console Application</span></span>

<span data-ttu-id="562d1-104">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="562d1-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="562d1-105">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="562d1-105">You’ll learn:</span></span>

- <span data-ttu-id="562d1-106">As noções básicas da CLI (Interface de Linha de Comando) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="562d1-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="562d1-107">A estrutura de um aplicativo de console C#</span><span class="sxs-lookup"><span data-stu-id="562d1-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="562d1-108">E/S do Console</span><span class="sxs-lookup"><span data-stu-id="562d1-108">Console I/O</span></span>
- <span data-ttu-id="562d1-109">Fundamentos das APIs de E/S de arquivo no .NET</span><span class="sxs-lookup"><span data-stu-id="562d1-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="562d1-110">Os fundamentos da programação assíncrona controlada por tarefas no .NET Core</span><span class="sxs-lookup"><span data-stu-id="562d1-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="562d1-111">Você compilará um aplicativo que lê um arquivo de texto e exibe o conteúdo desse arquivo de texto no console.</span><span class="sxs-lookup"><span data-stu-id="562d1-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="562d1-112">A saída para o console é conduzida a fim de corresponder à leitura em voz alta.</span><span class="sxs-lookup"><span data-stu-id="562d1-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="562d1-113">É possível acelerar ou diminuir o ritmo pressionando as teclas "<" (menor que) ou ">" (maior que).</span><span class="sxs-lookup"><span data-stu-id="562d1-113">You can speed up or slow down the pace by pressing the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span>

<span data-ttu-id="562d1-114">Há vários recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="562d1-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="562d1-115">Vamos compilá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="562d1-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="562d1-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="562d1-116">Prerequisites</span></span>

<span data-ttu-id="562d1-117">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="562d1-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="562d1-118">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="562d1-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="562d1-119">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="562d1-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="562d1-120">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="562d1-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="562d1-121">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="562d1-121">Create the Application</span></span>

<span data-ttu-id="562d1-122">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="562d1-122">The first step is to create a new application.</span></span> <span data-ttu-id="562d1-123">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="562d1-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="562d1-124">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="562d1-124">Make that the current directory.</span></span> <span data-ttu-id="562d1-125">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="562d1-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="562d1-126">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="562d1-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="562d1-127">Antes de começar as modificações, vamos percorrer as etapas para execução do aplicativo simples Hello World.</span><span class="sxs-lookup"><span data-stu-id="562d1-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="562d1-128">Depois de criar o aplicativo, digite `dotnet restore` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="562d1-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="562d1-129">Esse comando executa o processo de restauração do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="562d1-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="562d1-130">O NuGet é um gerenciador de pacotes do .NET.</span><span class="sxs-lookup"><span data-stu-id="562d1-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="562d1-131">Esse comando baixa qualquer uma das dependências ausentes para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="562d1-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="562d1-132">Como esse é um novo projeto, nenhuma das dependências foram aplicadas, portanto, a primeira execução baixará a estrutura do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="562d1-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="562d1-133">Após essa etapa inicial, você só precisará executar o `dotnet restore` ao adicionar novos pacotes dependentes, ou atualizar as versões de qualquer uma de suas dependências.</span><span class="sxs-lookup"><span data-stu-id="562d1-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="562d1-134">Depois de restaurar os pacotes, execute `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="562d1-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="562d1-135">Isso executa o mecanismo de compilação e cria o executável de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="562d1-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="562d1-136">Por fim, execute `dotnet run` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="562d1-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="562d1-137">O código simples do aplicativo Hello World está totalmente em Program.cs.</span><span class="sxs-lookup"><span data-stu-id="562d1-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="562d1-138">Abra esse arquivo com o seu editor de texto favorito.</span><span class="sxs-lookup"><span data-stu-id="562d1-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="562d1-139">Estamos prestes a fazer nossas primeiras alterações.</span><span class="sxs-lookup"><span data-stu-id="562d1-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="562d1-140">Na parte superior do arquivo, confira uma instrução using:</span><span class="sxs-lookup"><span data-stu-id="562d1-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="562d1-141">Essa instrução informa ao compilador que quaisquer tipos do namespace `System` estão dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="562d1-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="562d1-142">Assim como em outras linguagens orientadas a objeto que você pode ter usado, o C# usa namespaces para organizar tipos.</span><span class="sxs-lookup"><span data-stu-id="562d1-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="562d1-143">Este programa Olá, Mundo não é diferente.</span><span class="sxs-lookup"><span data-stu-id="562d1-143">This Hello World program is no different.</span></span> <span data-ttu-id="562d1-144">Você pode ver que o programa é encerrado no namespace com o nome baseado no nome do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="562d1-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="562d1-145">Para este tutorial, vamos alterar o nome do namespace para `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="562d1-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="562d1-146">Como ler e exibir o arquivo</span><span class="sxs-lookup"><span data-stu-id="562d1-146">Reading and Echoing the File</span></span>

<span data-ttu-id="562d1-147">O primeiro recurso a ser adicionado é a capacidade de ler um arquivo de texto e a exibição de todo esse texto para um console.</span><span class="sxs-lookup"><span data-stu-id="562d1-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="562d1-148">Primeiro, vamos adicionar um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="562d1-148">First, let’s add a text file.</span></span> <span data-ttu-id="562d1-149">Copie o arquivo [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) do repositório do GitHub para este [exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) no diretório de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="562d1-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="562d1-150">Isso servirá como o script de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="562d1-150">This will serve as the script for your application.</span></span> <span data-ttu-id="562d1-151">Se desejar obter informações sobre como baixar o aplicativo de exemplo para este tópico, consulte as instruções no tópico [Exemplos e Tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="562d1-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="562d1-152">Em seguida, adicione o seguinte método em sua classe `Program` (logo abaixo do método `Main`):</span><span class="sxs-lookup"><span data-stu-id="562d1-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="562d1-153">Esse método usa tipos de dois namespaces novos.</span><span class="sxs-lookup"><span data-stu-id="562d1-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="562d1-154">Para que isso seja compilado, será necessário adicionar as duas linhas a seguir na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="562d1-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="562d1-155">A interface <xref:System.Collections.Generic.IEnumerable%601> é definida no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="562d1-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="562d1-156">A classe <xref:System.IO.File> é definida no namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="562d1-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="562d1-157">Esse método é um tipo especial de método C# chamado de *Método iterador*.</span><span class="sxs-lookup"><span data-stu-id="562d1-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="562d1-158">Os métodos enumeradores retornam sequências que são avaliadas lentamente.</span><span class="sxs-lookup"><span data-stu-id="562d1-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="562d1-159">Isso significa que cada item na sequência é gerado conforme a solicitação do código que está consumindo a sequência.</span><span class="sxs-lookup"><span data-stu-id="562d1-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="562d1-160">Os métodos enumeradores contêm uma ou mais instruções [`yield return`](../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="562d1-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="562d1-161">O objeto retornado pelo método `ReadFrom` contém o código para gerar cada item na sequência.</span><span class="sxs-lookup"><span data-stu-id="562d1-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="562d1-162">Neste exemplo, isso envolve a leitura da próxima linha de texto do arquivo de origem e o retorno dessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="562d1-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="562d1-163">Toda vez que o código de chamada solicita o próximo item da sequência, o código lê a próxima linha de texto do arquivo e a retorna.</span><span class="sxs-lookup"><span data-stu-id="562d1-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="562d1-164">Após a leitura completa do arquivo, a sequência indicará que não há mais itens.</span><span class="sxs-lookup"><span data-stu-id="562d1-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="562d1-165">Há dois outros elementos da sintaxe em C# que podem ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="562d1-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="562d1-166">A instrução [`using`](../language-reference/keywords/using-statement.md) nesse método gerencia a limpeza de recursos.</span><span class="sxs-lookup"><span data-stu-id="562d1-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="562d1-167">A variável inicializada na instrução `using` (`reader`, neste exemplo) deve implementar a interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="562d1-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="562d1-168">Essa interface define um único método, `Dispose`, que deve ser chamado quando o recurso for liberado.</span><span class="sxs-lookup"><span data-stu-id="562d1-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="562d1-169">O compilador gera essa chamada quando a execução atingir a chave de fechamento da instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="562d1-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="562d1-170">O código gerado pelo compilador garante que o recurso seja liberado, mesmo se uma exceção for lançada do código no bloco definido pela instrução using.</span><span class="sxs-lookup"><span data-stu-id="562d1-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="562d1-171">A variável `reader` é definida usando a palavra-chave `var`.</span><span class="sxs-lookup"><span data-stu-id="562d1-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="562d1-172">[`var`](../language-reference/keywords/var.md) define uma *variável local de tipo implícito*.</span><span class="sxs-lookup"><span data-stu-id="562d1-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="562d1-173">Isso significa que o tipo da variável é determinado pelo tipo de tempo de compilação do objeto atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="562d1-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="562d1-174">Aqui, esse é o valor retornado do método <xref:System.IO.File.OpenText(System.String)>, que é um objeto <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="562d1-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="562d1-175">Agora, vamos preencher o código para ler o arquivo no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="562d1-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="562d1-176">Execute o programa (usando `dotnet run`, e você poderá ver todas as linhas impressa no console).</span><span class="sxs-lookup"><span data-stu-id="562d1-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="562d1-177">Adicionar atrasos e formatar a saída</span><span class="sxs-lookup"><span data-stu-id="562d1-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="562d1-178">O que você possui está sendo exibido muito rápido para permitir a leitura em voz alta.</span><span class="sxs-lookup"><span data-stu-id="562d1-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="562d1-179">Agora você precisa adicionar os atrasos na saída.</span><span class="sxs-lookup"><span data-stu-id="562d1-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="562d1-180">Ao começar, você compilará parte do código principal que permite o processamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="562d1-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="562d1-181">No entanto, essas primeiras etapas seguirão alguns antipadrões.</span><span class="sxs-lookup"><span data-stu-id="562d1-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="562d1-182">Os antipadrões são indicados nos comentários durante a adição do código, e o código será atualizado em etapas posteriores.</span><span class="sxs-lookup"><span data-stu-id="562d1-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="562d1-183">Há duas etapas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="562d1-183">There are two steps to this section.</span></span> <span data-ttu-id="562d1-184">Primeiro, você atualizará o método iterador a fim de retornar palavras individuais em vez de linhas inteiras.</span><span class="sxs-lookup"><span data-stu-id="562d1-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="562d1-185">Isso é feito com estas modificações.</span><span class="sxs-lookup"><span data-stu-id="562d1-185">That’s done with these modifications.</span></span> <span data-ttu-id="562d1-186">Substitua a instrução `yield return line;` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="562d1-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="562d1-187">Em seguida, será necessário modificar a forma como você consume as linhas do arquivo, e adicionar um atraso depois de escrever cada palavra.</span><span class="sxs-lookup"><span data-stu-id="562d1-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="562d1-188">Substitua a instrução `Console.WriteLine(line)` no método `Main` pelo seguinte bloco:</span><span class="sxs-lookup"><span data-stu-id="562d1-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="562d1-189">A classe <xref:System.Threading.Tasks.Task> é o namespace <xref:System.Threading.Tasks>, portanto, você precisa adicionar essa instrução `using` na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="562d1-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="562d1-190">Execute o exemplo e verifique a saída.</span><span class="sxs-lookup"><span data-stu-id="562d1-190">Run the sample, and check the output.</span></span> <span data-ttu-id="562d1-191">Agora, cada palavra única é impressa, seguida por um atraso de 200 ms.</span><span class="sxs-lookup"><span data-stu-id="562d1-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="562d1-192">No entanto, a saída exibida mostra alguns problemas, pois o arquivo de texto de origem contém várias linhas com mais de 80 caracteres sem uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="562d1-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="562d1-193">Isso pode ser difícil de ler durante a rolagem da tela.</span><span class="sxs-lookup"><span data-stu-id="562d1-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="562d1-194">Mas também é fácil de corrigir.</span><span class="sxs-lookup"><span data-stu-id="562d1-194">That’s easy to fix.</span></span> <span data-ttu-id="562d1-195">Apenas mantenha o controle do comprimento de cada linha e gere uma nova linha sempre que o comprimento atingir um certo limite.</span><span class="sxs-lookup"><span data-stu-id="562d1-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="562d1-196">Declare uma variável local após a declaração de `words` no método `ReadFrom` que contém o comprimento da linha:</span><span class="sxs-lookup"><span data-stu-id="562d1-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="562d1-197">Em seguida, adicione o seguinte código após a instrução `yield return word + " ";` (antes da chave de fechamento):</span><span class="sxs-lookup"><span data-stu-id="562d1-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="562d1-198">Execute o exemplo e você poderá ler em voz alta de acordo com o ritmo pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="562d1-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="562d1-199">Tarefas assíncronas</span><span class="sxs-lookup"><span data-stu-id="562d1-199">Async Tasks</span></span>

<span data-ttu-id="562d1-200">Nesta etapa final, você adicionará o código para gravar a saída de forma assíncrona em uma tarefa, enquanto executa também outra tarefa para ler a entrada do usuário, casos ele queira acelerar ou diminuir o ritmo da exibição do texto ou interromper a exibição do texto por completo.</span><span class="sxs-lookup"><span data-stu-id="562d1-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="562d1-201">Essa etapa tem alguns passos e, no final, você terá todas as atualizações necessárias.</span><span class="sxs-lookup"><span data-stu-id="562d1-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="562d1-202">A primeira etapa é criar um método de retorno <xref:System.Threading.Tasks.Task> assíncrono que representa o código que você criou até agora para ler e exibir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="562d1-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="562d1-203">Adicione este método à sua classe `Program` (ele é obtido do corpo de seu método `Main`):</span><span class="sxs-lookup"><span data-stu-id="562d1-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="562d1-204">Você observará duas alterações.</span><span class="sxs-lookup"><span data-stu-id="562d1-204">You’ll notice two changes.</span></span> <span data-ttu-id="562d1-205">Primeiro, no corpo do método, em vez de chamar <xref:System.Threading.Tasks.Task.Wait> para aguardar de forma síncrona a conclusão de uma tarefa, essa versão usa a palavra-chave `await`.</span><span class="sxs-lookup"><span data-stu-id="562d1-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="562d1-206">Para fazer isso, você precisa adicionar o modificador `async` à assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="562d1-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="562d1-207">Esse método retorna `Task`.</span><span class="sxs-lookup"><span data-stu-id="562d1-207">This method returns a `Task`.</span></span> <span data-ttu-id="562d1-208">Observe que não há instruções return que retornam um objeto `Task`.</span><span class="sxs-lookup"><span data-stu-id="562d1-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="562d1-209">Em vez disso, esse objeto `Task` é criado pelo código gerado pelo compilador quando você usa o operador `await`.</span><span class="sxs-lookup"><span data-stu-id="562d1-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="562d1-210">Você pode imaginar que esse método retorna quando atinge um `await`.</span><span class="sxs-lookup"><span data-stu-id="562d1-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="562d1-211">A `Task` retornada indica que o trabalho não foi concluído.</span><span class="sxs-lookup"><span data-stu-id="562d1-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="562d1-212">O método será retomado quando a tarefa em espera for concluída.</span><span class="sxs-lookup"><span data-stu-id="562d1-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="562d1-213">Após a execução completa, a `Task` retornada indicará a conclusão.</span><span class="sxs-lookup"><span data-stu-id="562d1-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="562d1-214">O código de chamada pode monitorar essa `Task` retornada para determinar quando ela foi concluída.</span><span class="sxs-lookup"><span data-stu-id="562d1-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="562d1-215">Chame esse novo método em seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="562d1-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="562d1-216">Aqui, em `Main`, o código aguarda de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="562d1-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="562d1-217">Use o operador `await` em vez de esperar de forma síncrona sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="562d1-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="562d1-218">Porém, no método `Main` do aplicativo de console, não é possível usar o operador `await`.</span><span class="sxs-lookup"><span data-stu-id="562d1-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="562d1-219">Isso resultaria no encerramento do aplicativo antes da conclusão de todas as tarefas.</span><span class="sxs-lookup"><span data-stu-id="562d1-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="562d1-220">Caso use o C# 7.1 ou posterior, você poderá criar aplicativos de console com o método [`async` `Main`](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="562d1-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="562d1-221">Em seguida, é necessário escrever o segundo método assíncrono a ser lido no Console e ficar atento às teclas "<" (menor que), ">" (maior que) e "X" ou "x".</span><span class="sxs-lookup"><span data-stu-id="562d1-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ (less than), ‘>’ (greater than) and ‘X’ or ‘x’ keys.</span></span> <span data-ttu-id="562d1-222">Este é o método que você adiciona à tarefa:</span><span class="sxs-lookup"><span data-stu-id="562d1-222">Here’s the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="562d1-223">Isso cria uma expressão lambda para representar um delegado <xref:System.Action> que lê uma chave no Console e modifica uma variável local que representa o atraso quando o usuário pressiona as teclas "<" (menor que) ou ">" (maior que).</span><span class="sxs-lookup"><span data-stu-id="562d1-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span> <span data-ttu-id="562d1-224">O método de delegado termina quando o usuário pressiona a tecla "X" ou "x", que permitem ao usuário interromper a exibição de texto a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="562d1-224">The delegate method finishes when user presses the ‘X’ or ‘x’  keys, which allow the user to stop the text display at any time.</span></span>
<span data-ttu-id="562d1-225">Esse método usa <xref:System.Console.ReadKey> para bloquear e aguardar até que o usuário pressione uma tecla.</span><span class="sxs-lookup"><span data-stu-id="562d1-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="562d1-226">Para concluir esse recurso, você precisa criar um novo método de retorno `async Task` que inicia essas duas tarefas (`GetInput` e `ShowTeleprompter`) e também gerencia os dados compartilhados entre essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="562d1-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="562d1-227">É hora de criar uma classe que pode manipular os dados compartilhados entre essas duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="562d1-227">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="562d1-228">Essa classe contém duas propriedades públicas: o atraso e um sinalizador `Done` para indicar que o arquivo foi lido completamente:</span><span class="sxs-lookup"><span data-stu-id="562d1-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="562d1-229">Coloque essa classe em um novo arquivo e cerque-a pelo namespace `TeleprompterConsole`, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="562d1-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="562d1-230">Também é necessário adicionar uma instrução `using static` para que você possa fazer referência ao método `Min` e `Max` sem os nomes de classe ou namespace delimitadores.</span><span class="sxs-lookup"><span data-stu-id="562d1-230">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="562d1-231">Uma instrução [`using static`](../language-reference/keywords/using-static.md) importa os métodos de uma classe.</span><span class="sxs-lookup"><span data-stu-id="562d1-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="562d1-232">Isso é o oposto das instruções `using` usadas até este ponto, as quais importaram todas as classes de um namespace.</span><span class="sxs-lookup"><span data-stu-id="562d1-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="562d1-233">O outro recurso de linguagem novo é a instrução [`lock`](../language-reference/keywords/lock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="562d1-233">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="562d1-234">Essa instrução garante a existência de apenas um thread nesse código a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="562d1-234">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="562d1-235">Se houver um thread na seção bloqueada, outros threads deverão aguardar até que o primeiro thread saia dessa seção.</span><span class="sxs-lookup"><span data-stu-id="562d1-235">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="562d1-236">A instrução `lock` usa um objeto que protege a seção de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="562d1-236">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="562d1-237">Essa classe segue uma linguagem padrão para bloquear um objeto privado na classe.</span><span class="sxs-lookup"><span data-stu-id="562d1-237">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="562d1-238">Em seguida, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o novo objeto `config`.</span><span class="sxs-lookup"><span data-stu-id="562d1-238">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="562d1-239">Escreva um método final `async` de retorno de `Task` para iniciar as duas tarefas e sair quando a primeira tarefa for concluída:</span><span class="sxs-lookup"><span data-stu-id="562d1-239">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="562d1-240">O novo método aqui é a chamada <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])>.</span><span class="sxs-lookup"><span data-stu-id="562d1-240">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="562d1-241">Isso cria uma `Task` que termina assim que qualquer uma das tarefas na lista de argumentos for concluída.</span><span class="sxs-lookup"><span data-stu-id="562d1-241">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="562d1-242">Depois, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o objeto `config` para o atraso:</span><span class="sxs-lookup"><span data-stu-id="562d1-242">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="562d1-243">Essa nova versão de `ShowTeleprompter` chama um novo método na classe `TeleprompterConfig`.</span><span class="sxs-lookup"><span data-stu-id="562d1-243">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="562d1-244">Agora, você precisa atualizar `Main` para chamar `RunTeleprompter` em vez de `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="562d1-244">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="562d1-245">Conclusão</span><span class="sxs-lookup"><span data-stu-id="562d1-245">Conclusion</span></span>

<span data-ttu-id="562d1-246">Este tutorial mostrou a você alguns recursos da linguagem C# e as bibliotecas .NET Core relacionadas ao trabalho em aplicativos de Console.</span><span class="sxs-lookup"><span data-stu-id="562d1-246">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="562d1-247">Use esse conhecimento como base para explorar mais sobre a linguagem e sobre as classes apresentadas aqui.</span><span class="sxs-lookup"><span data-stu-id="562d1-247">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="562d1-248">Você já viu os fundamentos de E/S do Arquivo e do Console, uso com bloqueio e sem bloqueio da programação assíncrona controlada por tarefa, um tour pela linguagem C# e como os programas em C# são organizados, além da Interface de linha de comando e ferramentas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="562d1-248">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="562d1-249">Para obter mais informações sobre E/S de arquivo, consulte o tópico [E/S de arquivo e de fluxo](../../standard/io/index.md).</span><span class="sxs-lookup"><span data-stu-id="562d1-249">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="562d1-250">Para obter mais informações sobre o modelo de programação assíncrona usado neste tutorial, consulte os tópicos [Programação assíncrona controlada por tarefas](../..//standard/parallel-programming/task-based-asynchronous-programming.md) e [Programação assíncrona](../async.md).</span><span class="sxs-lookup"><span data-stu-id="562d1-250">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
