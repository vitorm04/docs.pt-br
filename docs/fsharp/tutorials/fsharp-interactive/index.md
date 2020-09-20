---
title: Referência de F# Interativo (dotnet)
description: 'Saiba como F# Interativo (dotNet FSI) é usado para executar o código F # interativamente no console ou para executar scripts em F #.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: ae8d68140ddec8e18ee23e9a43b548907e1ab5c4
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720316"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="f166f-103">Programação interativa com F\#</span><span class="sxs-lookup"><span data-stu-id="f166f-103">Interactive programming with F\#</span></span>

<span data-ttu-id="f166f-104">F# Interativo (dotNet FSI) é usado para executar o código F # interativamente no console ou para executar scripts em F #.</span><span class="sxs-lookup"><span data-stu-id="f166f-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="f166f-105">Em outras palavras, o F# interativo executa um REPL (Ler, Avaliar, Imprimir Loop) para a linguagem F#.</span><span class="sxs-lookup"><span data-stu-id="f166f-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="f166f-106">Para executar o F# Interativo no console do, execute `dotnet fsi` .</span><span class="sxs-lookup"><span data-stu-id="f166f-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="f166f-107">Você encontrará `dotnet fsi` em qualquer SDK do .net.</span><span class="sxs-lookup"><span data-stu-id="f166f-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="f166f-108">Para saber mais sobre as opções de linha de comando disponíveis, veja [Opções de F# Interativo](../../language-reference/fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="f166f-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="f166f-109">Para executar o F# Interativo por meio do Visual Studio, você pode clicar no botão de barra de ferramentas apropriado rotulado como **F# Interativo** ou usar as teclas **Ctrl+Alt+F**.</span><span class="sxs-lookup"><span data-stu-id="f166f-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="f166f-110">Isso abrirá a janela interativa, uma janela da ferramenta que executa uma sessão de F# interativo.</span><span class="sxs-lookup"><span data-stu-id="f166f-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="f166f-111">Você também pode selecionar um código que deseja executar na janela interativa e pressionar a combinação de teclas **ALT + Enter**.</span><span class="sxs-lookup"><span data-stu-id="f166f-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="f166f-112">O F# interativo é iniciado em uma janela da ferramenta rotulada como **F# Interativo**.</span><span class="sxs-lookup"><span data-stu-id="f166f-112">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="f166f-113">Quando você usar essa combinação de teclas, certifique-se de que a janela do editor tenha o foco.</span><span class="sxs-lookup"><span data-stu-id="f166f-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="f166f-114">Se você estiver usando o console ou o Visual Studio, será exibido um prompt de comando e o interpretador aguardará a entrada.</span><span class="sxs-lookup"><span data-stu-id="f166f-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="f166f-115">Você pode inserir o código como faria em um arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="f166f-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="f166f-116">Para compilar e executar o código, insira dois sinais de ponto e vírgula (**;;**) para terminar uma linha ou várias linhas de entrada.</span><span class="sxs-lookup"><span data-stu-id="f166f-116">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="f166f-117">O F# interativo tenta compilar o código e, se tiver êxito, executará o código e imprimirá a assinatura dos tipos e valores que ele compilou.</span><span class="sxs-lookup"><span data-stu-id="f166f-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="f166f-118">Se ocorrerem erros, o interpretador imprime as mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="f166f-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="f166f-119">O código digitado na mesma sessão tem acesso a quaisquer construções inseridas anteriormente, para poder criar os programas.</span><span class="sxs-lookup"><span data-stu-id="f166f-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="f166f-120">Um buffer extensivo na janela da ferramenta permite que você copie o código para um arquivo, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f166f-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="f166f-121">Quando executado no Visual Studio, o F# interativo é executado independentemente do seu projeto, então, por exemplo, não é possível usar construções definidas em seu projeto em F# interativo, a menos que você copie o código para a função na janela interativa.</span><span class="sxs-lookup"><span data-stu-id="f166f-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="f166f-122">Se você tiver um projeto aberto que faça referência a algumas bibliotecas, poderá fazer referência em F# interativo por meio do **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="f166f-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer**.</span></span> <span data-ttu-id="f166f-123">Para fazer referência a uma biblioteca de F# Interativo, expanda o nó **Referências**, abra o menu de atalho da biblioteca e escolha **Enviar para F# Interativo**.</span><span class="sxs-lookup"><span data-stu-id="f166f-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive**.</span></span>

<span data-ttu-id="f166f-124">Você pode controlar os argumentos de linha de comando do F# interativo (opções) ajustando as configurações.</span><span class="sxs-lookup"><span data-stu-id="f166f-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="f166f-125">No menu **Ferramentas**, selecione **Opções...** e expanda **Ferramentas do F#**.</span><span class="sxs-lookup"><span data-stu-id="f166f-125">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="f166f-126">As duas configurações que podem ser alteradas são as opções do F# interativo e a configuração do **F# Interativo de 64 bits**, que é relevante apenas se você estiver executando o F# interativo em uma máquina de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f166f-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="f166f-127">Essa configuração determina se você deseja executar a versão de 64 bits dedicada do fsi.exe ou do fsianycpu.exe, que usa a arquitetura de máquina para determinar se deve ser executada como um processo de 32 ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f166f-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="f166f-128">Criando scripts com o F\#</span><span class="sxs-lookup"><span data-stu-id="f166f-128">Scripting with F\#</span></span>

<span data-ttu-id="f166f-129">Os scripts usam a extensão de arquivo **.fsx** ou **.fsscript**.</span><span class="sxs-lookup"><span data-stu-id="f166f-129">Scripts use the file extension **.fsx** or **.fsscript**.</span></span> <span data-ttu-id="f166f-130">Em vez de compilar o código-fonte e, posteriormente, executar o assembly compilado, você pode apenas executar **dotnet FSI** e especificar o nome de arquivo do script do código-fonte f # e o f # Interactive lê o código e o executa em tempo real.</span><span class="sxs-lookup"><span data-stu-id="f166f-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="f166f-131">Diferenças entre os ambientes interativo, de script e compilados</span><span class="sxs-lookup"><span data-stu-id="f166f-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="f166f-132">Quando você está compilando código em F# interativo, se estiver executando de forma interativa ou executando um script, o símbolo **INTERACTIVE** será definido.</span><span class="sxs-lookup"><span data-stu-id="f166f-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="f166f-133">Quando você está compilando código no compilador, o símbolo **COMPILED** é definido.</span><span class="sxs-lookup"><span data-stu-id="f166f-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="f166f-134">Assim, se o código precisar ser diferente nos modos compilados e interativos, você poderá usar diretivas de pré-processador para compilação condicional para determinar qual você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="f166f-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="f166f-135">Algumas diretivas estão disponíveis durante a execução de scripts no F# interativo, mas não estão disponíveis quando você está executando o compilador.</span><span class="sxs-lookup"><span data-stu-id="f166f-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="f166f-136">A tabela a seguir resume as diretivas que estão disponíveis quando você estiver usando o F# interativo.</span><span class="sxs-lookup"><span data-stu-id="f166f-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="f166f-137">Diretiva</span><span class="sxs-lookup"><span data-stu-id="f166f-137">Directive</span></span>|<span data-ttu-id="f166f-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="f166f-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="f166f-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="f166f-139">**#help**</span></span>|<span data-ttu-id="f166f-140">Exibe informações sobre as diretivas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f166f-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="f166f-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="f166f-141">**#I**</span></span>|<span data-ttu-id="f166f-142">Especifica um caminho de pesquisa de assembly entre aspas.</span><span class="sxs-lookup"><span data-stu-id="f166f-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="f166f-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="f166f-143">**#load**</span></span>|<span data-ttu-id="f166f-144">Lê um arquivo de origem, compila e o executa.</span><span class="sxs-lookup"><span data-stu-id="f166f-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="f166f-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="f166f-145">**#quit**</span></span>|<span data-ttu-id="f166f-146">Finaliza uma sessão do F# interativo.</span><span class="sxs-lookup"><span data-stu-id="f166f-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="f166f-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="f166f-147">**#r**</span></span>|<span data-ttu-id="f166f-148">Faz referência a um assembly.</span><span class="sxs-lookup"><span data-stu-id="f166f-148">References an assembly.</span></span>|
|<span data-ttu-id="f166f-149">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="f166f-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="f166f-150">Por si só, **#time** alterna se deve exibir informações sobre o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f166f-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="f166f-151">Quando habilitado, o F# interativo mede informações em tempo real, em tempo de CPU e de coleta de lixo de cada seção do código que é interpretado e executado.</span><span class="sxs-lookup"><span data-stu-id="f166f-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="f166f-152">Quando você especificar arquivos ou caminhos em F# interativo, uma sequência literal é esperada.</span><span class="sxs-lookup"><span data-stu-id="f166f-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="f166f-153">Portanto, arquivos e caminhos devem estar entre aspas e os caracteres de escape comuns se aplicam.</span><span class="sxs-lookup"><span data-stu-id="f166f-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="f166f-154">Além disso, você pode usar o caractere @ para fazer com que o F# interativo interprete uma cadeia de caracteres que contenha um caminho como uma cadeia de caracteres textuais.</span><span class="sxs-lookup"><span data-stu-id="f166f-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="f166f-155">Isso faz com que o F# interativo ignore quaisquer caracteres de escape.</span><span class="sxs-lookup"><span data-stu-id="f166f-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="f166f-156">Uma das diferenças entre o modo interativo e compilado é a maneira como você acessa argumentos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f166f-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="f166f-157">No modo compilado, use **System.Environment.GetCommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="f166f-157">In compiled mode, use **System.Environment.GetCommandLineArgs**.</span></span> <span data-ttu-id="f166f-158">Em scripts, use **fsi.CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="f166f-158">In scripts, use **fsi.CommandLineArgs**.</span></span>

<span data-ttu-id="f166f-159">O código a seguir ilustra como criar uma função que lê os argumentos da linha de comando em um script e também demonstra como fazer referência a outro conjunto por meio de um script.</span><span class="sxs-lookup"><span data-stu-id="f166f-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="f166f-160">O primeiro arquivo de código, **MyAssembly.fs**, é o código do assembly que está sendo referenciado.</span><span class="sxs-lookup"><span data-stu-id="f166f-160">The first code file, **MyAssembly.fs**, is the code for the assembly being referenced.</span></span> <span data-ttu-id="f166f-161">Compile esse arquivo com a linha de comando: **fsc -a MyAssembly.fs** e, em seguida, execute o segundo arquivo como um script com a linha de comando: **fsi --exec file1.fsx** test</span><span class="sxs-lookup"><span data-stu-id="f166f-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="f166f-162">A saída é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f166f-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="f166f-163">Gerenciamento de Pacotes em F# Interativo</span><span class="sxs-lookup"><span data-stu-id="f166f-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="f166f-164">O gerenciamento de pacotes está disponível como um recurso de visualização em versões do `dotnet fsi` fornecidas no `3.1.300` e em versões posteriores do SDK do .net, bem como todas as `5.*` versões do SDK do .net.</span><span class="sxs-lookup"><span data-stu-id="f166f-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="f166f-165">Para habilitá-lo nesta versão de visualização, execute `dotnet fsi` com o `--langversion:preview` argumento.</span><span class="sxs-lookup"><span data-stu-id="f166f-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="f166f-166">A `#r` sintaxe para referenciar uma dll no F# interativo também pode ser usada para fazer referência a um pacote NuGet por meio da seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f166f-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>
```

<span data-ttu-id="f166f-167">Por exemplo, para fazer referência ao `FSharp.Data` pacote, use a seguinte `#r` referência:</span><span class="sxs-lookup"><span data-stu-id="f166f-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="f166f-168">Depois de executar essa linha, a versão mais recente do `FSharp.Data` pacote será baixada para o cache do NuGet e referenciada na sessão de F# interativo atual.</span><span class="sxs-lookup"><span data-stu-id="f166f-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="f166f-169">Além do nome do pacote, versões específicas de um pacote podem ser referenciadas por meio de uma sintaxe curta:</span><span class="sxs-lookup"><span data-stu-id="f166f-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="f166f-170">ou de maneira mais explícita:</span><span class="sxs-lookup"><span data-stu-id="f166f-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="f166f-171">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="f166f-171">Related articles</span></span>

|<span data-ttu-id="f166f-172">Título</span><span class="sxs-lookup"><span data-stu-id="f166f-172">Title</span></span>|<span data-ttu-id="f166f-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="f166f-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="f166f-174">Opções do F# Interativo</span><span class="sxs-lookup"><span data-stu-id="f166f-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="f166f-175">Descreve a sintaxe de linha de comando e as opções para o F# Interativo, fsi.exe.</span><span class="sxs-lookup"><span data-stu-id="f166f-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
