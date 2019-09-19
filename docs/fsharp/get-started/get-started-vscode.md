---
title: Introdução ao F# no Visual Studio Code
description: Saiba como usar F# o com Visual Studio Code e o pacote de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082993"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="c6517-103">Introdução ao F# no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c6517-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="c6517-104">Você pode escrever F# em [Visual Studio Code](https://code.visualstudio.com) com o [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma experiência excelente de plataforma cruzada, ambiente de desenvolvimento integrado leve (IDE) com IntelliSense e refatoração de código básico.</span><span class="sxs-lookup"><span data-stu-id="c6517-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="c6517-105">Visite [Ionide.Io](http://ionide.io) para saber mais sobre o plug-in.</span><span class="sxs-lookup"><span data-stu-id="c6517-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="c6517-106">Para começar, verifique se você tem [ F# o e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="c6517-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="c6517-107">O Ionide vai gerar F# projetos de .NET Framework, não o núcleo dotnet, que pode ter problemas de compatibilidade entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="c6517-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="c6517-108">Se você estiver executando no **Linux** ou no **OSX**, uma maneira mais simples de começar é usar as [ferramentas de linha de comando](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="c6517-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="c6517-109">Criando seu primeiro projeto com o Ionide</span><span class="sxs-lookup"><span data-stu-id="c6517-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="c6517-110">Para criar um novo F# projeto, abra Visual Studio Code em uma nova pasta (você pode nomeá-lo como desejar).</span><span class="sxs-lookup"><span data-stu-id="c6517-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="c6517-111">Em seguida, abra a paleta de comandos (**exibir > paleta de comandos**) e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6517-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="c6517-112">Isso é alimentado pelo projeto [de forjação](https://github.com/fsharp-editing/Forge).</span><span class="sxs-lookup"><span data-stu-id="c6517-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="c6517-113">Se você não vir opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comandos: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="c6517-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="c6517-114">Selecione "F#: Novo projeto "ao pressionar **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c6517-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="c6517-115">Isso levará você para a próxima etapa, que é para selecionar um modelo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c6517-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="c6517-116">Escolha o `classlib` modelo e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c6517-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="c6517-117">Em seguida, escolha um diretório no qual criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="c6517-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="c6517-118">Se você deixá-lo em branco, ele usará o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c6517-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="c6517-119">Por fim, nomeie o projeto na etapa final.</span><span class="sxs-lookup"><span data-stu-id="c6517-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="c6517-120">F#usa o [caso do Pascal](http://c2.com/cgi/wiki?PascalCase) para nomes de projeto.</span><span class="sxs-lookup"><span data-stu-id="c6517-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="c6517-121">Este artigo usa `ClassLibraryDemo` como o nome.</span><span class="sxs-lookup"><span data-stu-id="c6517-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="c6517-122">Depois de inserir o nome desejado para o seu projeto, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c6517-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="c6517-123">Se você seguiu a etapa anterior, deverá obter o espaço de trabalho Visual Studio Code no lado esquerdo para aparecer com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6517-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="c6517-124">O F# projeto em si, sob `ClassLibraryDemo` a pasta.</span><span class="sxs-lookup"><span data-stu-id="c6517-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="c6517-125">A estrutura de diretório correta para adicionar pacotes [`Paket`](https://fsprojects.github.io/Paket/)via.</span><span class="sxs-lookup"><span data-stu-id="c6517-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="c6517-126">Um script de Build de plataforma cruzada com [`FAKE`](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="c6517-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="c6517-127">O `paket.exe` executável que pode buscar pacotes e resolver dependências para você.</span><span class="sxs-lookup"><span data-stu-id="c6517-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="c6517-128">Um `.gitignore` arquivo se você quiser adicionar este projeto ao controle do código-fonte baseado em git.</span><span class="sxs-lookup"><span data-stu-id="c6517-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="c6517-129">Escrevendo código</span><span class="sxs-lookup"><span data-stu-id="c6517-129">Writing some code</span></span>

<span data-ttu-id="c6517-130">Abra a pasta *ClassLibraryDemo* .</span><span class="sxs-lookup"><span data-stu-id="c6517-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="c6517-131">Você deve ver os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="c6517-131">You should see the following files:</span></span>

1. <span data-ttu-id="c6517-132">`ClassLibraryDemo.fs`, um F# arquivo de implementação com uma classe definida.</span><span class="sxs-lookup"><span data-stu-id="c6517-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="c6517-133">`ClassLibraryDemo.fsproj`, um F# arquivo de projeto usado para compilar este projeto.</span><span class="sxs-lookup"><span data-stu-id="c6517-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="c6517-134">`Script.fsx`, um F# arquivo de script que carrega o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="c6517-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="c6517-135">`paket.references`, um arquivo paket que especifica as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6517-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="c6517-136">Abra `Script.fsx`o e adicione o seguinte código ao final dele:</span><span class="sxs-lookup"><span data-stu-id="c6517-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="c6517-137">Essa função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="c6517-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="c6517-138">A próxima etapa é avaliá-lo F# usando o Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="c6517-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="c6517-139">Realce a função inteira (deve ter 11 linhas).</span><span class="sxs-lookup"><span data-stu-id="c6517-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="c6517-140">Depois de realçado, mantenha pressionada a tecla **ALT** e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c6517-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="c6517-141">Você notará uma janela pop-up abaixo e deverá mostrar algo assim:</span><span class="sxs-lookup"><span data-stu-id="c6517-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Exemplo de F# saída interativa com Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="c6517-143">Isso fazia três coisas:</span><span class="sxs-lookup"><span data-stu-id="c6517-143">This did three things:</span></span>

1. <span data-ttu-id="c6517-144">Ele iniciou o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-144">It started the FSI process.</span></span>
2. <span data-ttu-id="c6517-145">Ele enviou o código realçado sobre o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="c6517-146">O processo do FSI avaliou o código que você enviou.</span><span class="sxs-lookup"><span data-stu-id="c6517-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="c6517-147">Como o que você enviou foi uma [função](../language-reference/functions/index.md), agora você pode chamar essa função com o FSI!</span><span class="sxs-lookup"><span data-stu-id="c6517-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="c6517-148">Na janela interativa, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6517-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="c6517-149">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="c6517-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="c6517-150">Agora, vamos tentar com uma vogal como a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="c6517-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="c6517-151">Insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6517-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="c6517-152">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="c6517-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="c6517-153">A função parece estar funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="c6517-153">The function appears to be working as expected.</span></span> <span data-ttu-id="c6517-154">Parabéns, você acabou de escrever sua F# primeira função em Visual Studio Code e a avaliou com o FSI!</span><span class="sxs-lookup"><span data-stu-id="c6517-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="c6517-155">Como você deve ter notado, as linhas no FSI são encerradas `;;`com.</span><span class="sxs-lookup"><span data-stu-id="c6517-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="c6517-156">Isso ocorre porque o FSI permite que você insira várias linhas.</span><span class="sxs-lookup"><span data-stu-id="c6517-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="c6517-157">O `;;` no final permite que o FSI saiba quando o código é concluído.</span><span class="sxs-lookup"><span data-stu-id="c6517-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="c6517-158">Explicando o código</span><span class="sxs-lookup"><span data-stu-id="c6517-158">Explaining the code</span></span>

<span data-ttu-id="c6517-159">Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.</span><span class="sxs-lookup"><span data-stu-id="c6517-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="c6517-160">Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e a converte em uma representação Pig-Latin dessa palavra.</span><span class="sxs-lookup"><span data-stu-id="c6517-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="c6517-161">As regras para isso são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="c6517-161">The rules for this are as follows:</span></span>

<span data-ttu-id="c6517-162">Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" ao final da palavra.</span><span class="sxs-lookup"><span data-stu-id="c6517-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="c6517-163">Se não começar com uma vogal, mova o primeiro caractere para o final da palavra e adicione "o".</span><span class="sxs-lookup"><span data-stu-id="c6517-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="c6517-164">Você pode ter notado o seguinte no FSI:</span><span class="sxs-lookup"><span data-stu-id="c6517-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="c6517-165">Isso declara que `toPigLatin` é uma função que usa `string` como entrada (chamada `word`) e retorna outra `string`.</span><span class="sxs-lookup"><span data-stu-id="c6517-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="c6517-166">Isso é conhecido como a [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da F# chave para entender F# o código.</span><span class="sxs-lookup"><span data-stu-id="c6517-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="c6517-167">Você também observará isso se passar o mouse sobre a função em Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c6517-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="c6517-168">No corpo da função, você observará duas partes distintas:</span><span class="sxs-lookup"><span data-stu-id="c6517-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="c6517-169">Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="c6517-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="c6517-170">Uma [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno dos caracteres de entrada com base em se o primeiro caractere era uma vogal ou não:</span><span class="sxs-lookup"><span data-stu-id="c6517-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="c6517-171">O fluxo de `toPigLatin` é assim:</span><span class="sxs-lookup"><span data-stu-id="c6517-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="c6517-172">Verifique se o primeiro caractere da palavra de entrada é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="c6517-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="c6517-173">Se for, anexe "Sim" ao final da palavra.</span><span class="sxs-lookup"><span data-stu-id="c6517-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="c6517-174">Caso contrário, mova esse primeiro caractere para o final da palavra e adicione "</span><span class="sxs-lookup"><span data-stu-id="c6517-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="c6517-175">Há uma coisa final a ser observada sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitas outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="c6517-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="c6517-176">Isso ocorre porque F# o é baseado em expressão e a última expressão no corpo de uma função é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c6517-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="c6517-177">Como `if..then..else` o próprio é uma expressão, o corpo `then` do bloco `else` ou o corpo do bloco será retornado dependendo do valor de entrada.</span><span class="sxs-lookup"><span data-stu-id="c6517-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="c6517-178">Movendo o código do script para o arquivo de implementação</span><span class="sxs-lookup"><span data-stu-id="c6517-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="c6517-179">As seções anteriores neste artigo demonstraram uma primeira etapa comum na escrita F# de código: escrever uma função inicial e executá-la interativamente com o FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="c6517-180">Isso é conhecido como desenvolvimento controlado por REPL, em que [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Read-Evaluate-Print loop".</span><span class="sxs-lookup"><span data-stu-id="c6517-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="c6517-181">É uma ótima maneira de experimentar a funcionalidade até que você tenha algo funcionando.</span><span class="sxs-lookup"><span data-stu-id="c6517-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="c6517-182">A próxima etapa no desenvolvimento controlado por REPL é mover o código funcional para um F# arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="c6517-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="c6517-183">Em seguida, ele pode ser compilado F# pelo compilador em um assembly que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="c6517-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="c6517-184">Para começar, abra `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="c6517-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="c6517-185">Você observará que algum código já está lá.</span><span class="sxs-lookup"><span data-stu-id="c6517-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="c6517-186">Vá em frente e exclua a definição de classe, mas lembre- [`namespace`](../language-reference/namespaces.md) se de deixar a declaração na parte superior.</span><span class="sxs-lookup"><span data-stu-id="c6517-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="c6517-187">Em seguida, crie um [`module`](../language-reference/modules.md) novo `PigLatin` chamado e copie `toPigLatin` a função para ele da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c6517-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="c6517-188">Em seguida, abra `Script.fsx` o arquivo novamente e exclua a `toPigLatin` função inteira, mas certifique-se de manter as duas linhas a seguir no arquivo:</span><span class="sxs-lookup"><span data-stu-id="c6517-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="c6517-189">Selecione as duas linhas de texto e pressione Alt + Enter para executar essas linhas no FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="c6517-190">Eles carregarão o conteúdo da biblioteca Pig Latin no processo FSI e `open` o `ClassLibraryDemo` namespace para que você tenha acesso à funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="c6517-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="c6517-191">Em seguida, na janela do FSI, chame a função com `PigLatin` o módulo que você definiu anteriormente:</span><span class="sxs-lookup"><span data-stu-id="c6517-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="c6517-192">Êxito!</span><span class="sxs-lookup"><span data-stu-id="c6517-192">Success!</span></span> <span data-ttu-id="c6517-193">Você Obtém os mesmos resultados que antes, mas agora é carregado de F# um arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="c6517-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="c6517-194">A principal diferença aqui é que F# os arquivos de origem são compilados em assemblies que podem ser executados em qualquer lugar, não apenas no FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="c6517-195">Resumo</span><span class="sxs-lookup"><span data-stu-id="c6517-195">Summary</span></span>

<span data-ttu-id="c6517-196">Neste artigo, você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="c6517-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="c6517-197">Como configurar Visual Studio Code com o Ionide.</span><span class="sxs-lookup"><span data-stu-id="c6517-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="c6517-198">Como criar seu primeiro F# projeto com o Ionide.</span><span class="sxs-lookup"><span data-stu-id="c6517-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="c6517-199">Como usar F# o script para escrever sua primeira F# função em Ionide e executá-la no FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="c6517-200">Como migrar seu código de script F# para origem e, em seguida, chamar esse código do FSI.</span><span class="sxs-lookup"><span data-stu-id="c6517-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="c6517-201">Agora você está equipado para escrever muito mais F# código usando Visual Studio Code e Ionide.</span><span class="sxs-lookup"><span data-stu-id="c6517-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c6517-202">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c6517-202">Troubleshooting</span></span>

<span data-ttu-id="c6517-203">Aqui estão algumas maneiras de solucionar alguns problemas que você pode encontrar:</span><span class="sxs-lookup"><span data-stu-id="c6517-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="c6517-204">Para obter os recursos de edição de código do Ionide F# , os arquivos precisam ser salvos em disco e dentro de uma pasta que está aberta no espaço de trabalho Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c6517-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="c6517-205">Se você fez alterações no seu sistema ou instalou os pré-requisitos do Ionide com Visual Studio Code abrir, reinicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c6517-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="c6517-206">Verifique se você pode usar o F# compilador e F# interativo da linha de comando sem um caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c6517-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="c6517-207">Você pode fazer isso digitando `fsc` uma linha de comando para o F# compilador e `fsi` ou `fsharpi` para as ferramentas visuais F# no Windows e mono no Mac/Linux, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c6517-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="c6517-208">Se você tiver caracteres inválidos em seus diretórios de projeto, o Ionide poderá não funcionar.</span><span class="sxs-lookup"><span data-stu-id="c6517-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="c6517-209">Renomeie os diretórios do projeto se esse for o caso.</span><span class="sxs-lookup"><span data-stu-id="c6517-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="c6517-210">Se nenhum dos comandos Ionide estiver funcionando, verifique suas [associações de teclas Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você está substituindo-as por acidente.</span><span class="sxs-lookup"><span data-stu-id="c6517-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="c6517-211">Se o Ionide for interrompido em seu computador e nenhuma das opções acima tiver corrigido o problema, tente remover `ionide-fsharp` o diretório em seu computador e reinstalar o pacote de plug-in.</span><span class="sxs-lookup"><span data-stu-id="c6517-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="c6517-212">Ionide é um projeto de software livre criado e mantido por membros da F# comunidade.</span><span class="sxs-lookup"><span data-stu-id="c6517-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="c6517-213">Informe os [problemas e fique à vontade para contribuir no Ionide-VSCode: Repositório](https://github.com/ionide/ionide-vscode-fsharp)do GitHub do FSharp.</span><span class="sxs-lookup"><span data-stu-id="c6517-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="c6517-214">Se você tiver um problema para relatar, siga [as instruções para obter os logs a serem usados ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="c6517-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="c6517-215">Você também pode pedir ajuda para os desenvolvedores e F# a Comunidade do Ionide no [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="c6517-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6517-216">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c6517-216">Next steps</span></span>

<span data-ttu-id="c6517-217">Para saber mais sobre F# os recursos do idioma, confira o [Tour do F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="c6517-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
