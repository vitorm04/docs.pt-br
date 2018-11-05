---
title: Introdução ao F# no Visual Studio Code
description: Saiba como usar F# com o Visual Studio Code e o conjunto de plug-in de Ionide.
ms.date: 05/28/2018
ms.openlocfilehash: e962be2796cf0d6eb90d459730659e492f864716
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50192662"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="04367-103">Introdução ao F# no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="04367-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="04367-104">Você pode escrever F# no [Visual Studio Code](https://code.visualstudio.com) com o [plug-in do Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma ótima experiência de ambiente de desenvolvimento integrado (IDE) de plataforma cruzada, mais leve, com o IntelliSense e o código básico refatorações.</span><span class="sxs-lookup"><span data-stu-id="04367-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="04367-105">Visite [Ionide.io](http://ionide.io) para saber mais sobre o plug-in.</span><span class="sxs-lookup"><span data-stu-id="04367-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="04367-106">Para começar, certifique-se de que você tenha [F# e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="04367-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="04367-107">Criando seu primeiro projeto com Ionide</span><span class="sxs-lookup"><span data-stu-id="04367-107">Creating your first project with Ionide</span></span>

<span data-ttu-id="04367-108">Para criar um novo projeto F#, abra o Visual Studio Code em uma nova pasta (você pode nomeá-lo que você quiser).</span><span class="sxs-lookup"><span data-stu-id="04367-108">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="04367-109">Em seguida, abra a paleta de comandos (**exibição > Paleta de comandos**) e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04367-109">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="04367-110">Isso é alimentado pela [FORJAR](https://github.com/fsharp-editing/Forge) projeto.</span><span class="sxs-lookup"><span data-stu-id="04367-110">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="04367-111">Se você não vir Opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comandos: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="04367-111">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="04367-112">Selecione ": novo projeto de F#" pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="04367-112">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="04367-113">Isso leva você para a próxima etapa é selecionar um modelo de projeto.</span><span class="sxs-lookup"><span data-stu-id="04367-113">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="04367-114">Escolher o `classlib` modelo e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="04367-114">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="04367-115">Em seguida, escolha um diretório para criar o projeto no.</span><span class="sxs-lookup"><span data-stu-id="04367-115">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="04367-116">Se você deixar em branco, ele usa o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="04367-116">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="04367-117">Por fim, nomeie o projeto na etapa final.</span><span class="sxs-lookup"><span data-stu-id="04367-117">Finally, name your project in the final step.</span></span> <span data-ttu-id="04367-118">F# usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para nomes de projetos.</span><span class="sxs-lookup"><span data-stu-id="04367-118">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="04367-119">Este artigo usa `ClassLibraryDemo` como o nome.</span><span class="sxs-lookup"><span data-stu-id="04367-119">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="04367-120">Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="04367-120">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="04367-121">Se você seguiu a etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo seja exibido com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04367-121">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="04367-122">O F# projeto em si, sob o `ClassLibraryDemo` pasta.</span><span class="sxs-lookup"><span data-stu-id="04367-122">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="04367-123">A estrutura de diretório correto para adicionar pacotes via [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="04367-123">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="04367-124">Script com de construção de uma plataforma cruzada [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="04367-124">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="04367-125">O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.</span><span class="sxs-lookup"><span data-stu-id="04367-125">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="04367-126">Um `.gitignore` arquivo se você deseja adicionar este projeto ao controle de origem com base em Git.</span><span class="sxs-lookup"><span data-stu-id="04367-126">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="04367-127">Escrever o código</span><span class="sxs-lookup"><span data-stu-id="04367-127">Writing some code</span></span>

<span data-ttu-id="04367-128">Abra o *ClassLibraryDemo* pasta.</span><span class="sxs-lookup"><span data-stu-id="04367-128">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="04367-129">Você verá os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="04367-129">You should see the following files:</span></span>

1. <span data-ttu-id="04367-130">`ClassLibraryDemo.fs`, um arquivo de implementação do F# com uma classe definida.</span><span class="sxs-lookup"><span data-stu-id="04367-130">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="04367-131">`ClassLibraryDemo.fsproj`, um arquivo de projeto F# usado para compilar esse projeto.</span><span class="sxs-lookup"><span data-stu-id="04367-131">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="04367-132">`Script.fsx`, um arquivo de script F# que carrega o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="04367-132">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="04367-133">`paket.references`, um arquivo de Paket que especifica as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="04367-133">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="04367-134">Abra `Script.fsx`e adicione o seguinte código ao final dele:</span><span class="sxs-lookup"><span data-stu-id="04367-134">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="04367-135">Esta função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="04367-135">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="04367-136">A próxima etapa é avaliá-lo usando a linguagem F# interativo (FSI).</span><span class="sxs-lookup"><span data-stu-id="04367-136">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="04367-137">Realce a função inteira (deve ser 11 linhas de comprimento).</span><span class="sxs-lookup"><span data-stu-id="04367-137">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="04367-138">Depois que ele é realçado, mantenha o **Alt** chave e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="04367-138">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="04367-139">Você observará uma janela pop-up abaixo, e ele deve mostrar algo parecido com isto:</span><span class="sxs-lookup"><span data-stu-id="04367-139">You'll notice a window pop up below, and it should show something like this:</span></span>

![Exemplo de saída de F# interativo com Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="04367-141">Isso fazia três coisas:</span><span class="sxs-lookup"><span data-stu-id="04367-141">This did three things:</span></span>

1. <span data-ttu-id="04367-142">Ele iniciou o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-142">It started the FSI process.</span></span>
2. <span data-ttu-id="04367-143">Ele enviado o código realçado ao longo do processo FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-143">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="04367-144">O processo FSI avaliado o código enviado ao longo.</span><span class="sxs-lookup"><span data-stu-id="04367-144">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="04367-145">Porque era enviados por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI!</span><span class="sxs-lookup"><span data-stu-id="04367-145">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="04367-146">Na janela interativa, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04367-146">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="04367-147">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="04367-147">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="04367-148">Agora, vamos tentar com uma vogal como a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="04367-148">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="04367-149">Insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04367-149">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="04367-150">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="04367-150">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="04367-151">A função parece estar funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="04367-151">The function appears to be working as expected.</span></span> <span data-ttu-id="04367-152">Parabéns, você escreveu sua primeira função F# no Visual Studio Code e avaliado-lo com FSI apenas!</span><span class="sxs-lookup"><span data-stu-id="04367-152">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="04367-153">Como você pode ter notado, as linhas no FSI são finalizadas com `;;`.</span><span class="sxs-lookup"><span data-stu-id="04367-153">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="04367-154">Isso ocorre porque FSI permite que você insira várias linhas.</span><span class="sxs-lookup"><span data-stu-id="04367-154">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="04367-155">O `;;` no final informa FSI quando o código for concluído.</span><span class="sxs-lookup"><span data-stu-id="04367-155">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="04367-156">Explicando o código</span><span class="sxs-lookup"><span data-stu-id="04367-156">Explaining the code</span></span>

<span data-ttu-id="04367-157">Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.</span><span class="sxs-lookup"><span data-stu-id="04367-157">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="04367-158">Como você pode ver, `toPigLatin` é uma função que leva a uma palavra como sua entrada e o converte em uma representação de Pig Latin dessa palavra.</span><span class="sxs-lookup"><span data-stu-id="04367-158">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="04367-159">As regras para isso são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="04367-159">The rules for this are as follows:</span></span>

<span data-ttu-id="04367-160">Se o primeiro caractere em uma palavra começa com uma vogal, adicione "Sim" ao final da palavra.</span><span class="sxs-lookup"><span data-stu-id="04367-160">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="04367-161">Se ele não começa com uma vogal, mover desse primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="04367-161">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="04367-162">Você talvez tenha observado a seguir no FSI:</span><span class="sxs-lookup"><span data-stu-id="04367-162">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="04367-163">Isso indica que `toPigLatin` é uma função que usa um `string` como entrada (chamado `word`) e retorna outra `string`.</span><span class="sxs-lookup"><span data-stu-id="04367-163">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="04367-164">Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental do F# que é a chave para entender o código F#.</span><span class="sxs-lookup"><span data-stu-id="04367-164">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="04367-165">Você também perceberá isso se você passar o mouse sobre a função no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="04367-165">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="04367-166">O corpo da função, você observará duas partes distintas:</span><span class="sxs-lookup"><span data-stu-id="04367-166">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="04367-167">Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponder a um dos padrões fornecidos via [correspondência de padrões](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="04367-167">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="04367-168">Uma [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e construções de um retorno de valor sem os caracteres de entrada com base em se o primeiro caractere foi uma vogal ou não:</span><span class="sxs-lookup"><span data-stu-id="04367-168">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="04367-169">O fluxo de `toPigLatin` , portanto, é:</span><span class="sxs-lookup"><span data-stu-id="04367-169">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="04367-170">Verifique se o primeiro caractere da palavra entrada é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="04367-170">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="04367-171">Se for, anexe "Sim" para o fim da palavra.</span><span class="sxs-lookup"><span data-stu-id="04367-171">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="04367-172">Caso contrário, mover desse primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="04367-172">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="04367-173">Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas por aí.</span><span class="sxs-lookup"><span data-stu-id="04367-173">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="04367-174">Isso ocorre porque o F# é baseada em expressão, e a última expressão no corpo de uma função é o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="04367-174">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="04367-175">Porque `if..then..else` em si for uma expressão, o corpo dos `then` bloco ou no corpo do `else` bloco será retornado, dependendo do valor de entrada.</span><span class="sxs-lookup"><span data-stu-id="04367-175">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="04367-176">Mover o código de script no arquivo de implementação</span><span class="sxs-lookup"><span data-stu-id="04367-176">Moving your script code into the implementation file</span></span>

<span data-ttu-id="04367-177">As seções anteriores deste artigo demonstrou uma primeira etapa comum ao escrever código F#: gravar uma função inicial e executá-lo interativamente com FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-177">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="04367-178">Isso é conhecido como o desenvolvimento controlado por REPL, onde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Loop de leitura-avaliação-impressão".</span><span class="sxs-lookup"><span data-stu-id="04367-178">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="04367-179">É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="04367-179">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="04367-180">A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho para um arquivo de implementação F#.</span><span class="sxs-lookup"><span data-stu-id="04367-180">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="04367-181">Ele, em seguida, pode ser compilado pelo compilador do F# em um assembly que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="04367-181">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="04367-182">Para começar, abra `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="04367-182">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="04367-183">Você observará que algum código já está em lá.</span><span class="sxs-lookup"><span data-stu-id="04367-183">You'll notice that some code is already in there.</span></span> <span data-ttu-id="04367-184">Vá em frente e exclua a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.</span><span class="sxs-lookup"><span data-stu-id="04367-184">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="04367-185">Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:</span><span class="sxs-lookup"><span data-stu-id="04367-185">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="04367-186">Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionar, mas certifique-se de manter as duas linhas seguintes no arquivo:</span><span class="sxs-lookup"><span data-stu-id="04367-186">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="04367-187">A primeira linha é necessária para FSI de script para carregar `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="04367-187">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="04367-188">A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="04367-188">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="04367-189">Em seguida, na janela FSI, chame a função com o `PigLatin` módulo que você definiu anteriormente:</span><span class="sxs-lookup"><span data-stu-id="04367-189">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="04367-190">Sucesso!</span><span class="sxs-lookup"><span data-stu-id="04367-190">Success!</span></span> <span data-ttu-id="04367-191">Obter os mesmos resultados que antes, mas agora é carregado de um arquivo de implementação F#.</span><span class="sxs-lookup"><span data-stu-id="04367-191">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="04367-192">A principal diferença é que os arquivos de origem do F# são compilados em assemblies que podem ser executados em qualquer lugar, não apenas na FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-192">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="04367-193">Resumo</span><span class="sxs-lookup"><span data-stu-id="04367-193">Summary</span></span>

<span data-ttu-id="04367-194">Neste artigo, você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="04367-194">In this article, you've learned:</span></span>

1. <span data-ttu-id="04367-195">Como configurar o Visual Studio Code com Ionide.</span><span class="sxs-lookup"><span data-stu-id="04367-195">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="04367-196">Como criar seu primeiro projeto F# com Ionide.</span><span class="sxs-lookup"><span data-stu-id="04367-196">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="04367-197">Como usar o F# script para escrever sua primeira função F# em Ionide e, em seguida, execute-o na FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-197">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="04367-198">Como migrar seu código de script para o código-fonte do F# e, em seguida, chama esse código de FSI.</span><span class="sxs-lookup"><span data-stu-id="04367-198">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="04367-199">Você agora está pronto para escrever muito mais código do F# usando o Visual Studio Code e Ionide.</span><span class="sxs-lookup"><span data-stu-id="04367-199">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="04367-200">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="04367-200">Troubleshooting</span></span>

<span data-ttu-id="04367-201">Aqui estão algumas maneiras que você pode solucionar alguns problemas que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="04367-201">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="04367-202">Para obter recursos de Ionide de edição de código, os arquivos de F# precisam ser salvos em disco e de dentro de uma pasta que está aberta no espaço de trabalho do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="04367-202">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="04367-203">Se você fez alterações ao seu sistema ou instalar pré-requisitos de Ionide abrir o Visual Studio Code, reinicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="04367-203">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="04367-204">Verifique que você pode usar o compilador F# e F# interativo da linha de comando sem um caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="04367-204">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="04367-205">Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador F#, e `fsi` ou `fsharpi` para o Visual F# ferramentas no Windows e o Mono no Mac/Linux, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="04367-205">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="04367-206">Se você tiver caracteres inválidos em seus diretórios de projeto, Ionide pode não funcionar.</span><span class="sxs-lookup"><span data-stu-id="04367-206">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="04367-207">Se esse for o caso, renomeie os diretórios de projeto.</span><span class="sxs-lookup"><span data-stu-id="04367-207">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="04367-208">Se nenhum dos comandos Ionide estão funcionando, verifique sua [associações de teclas do Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por acidente.</span><span class="sxs-lookup"><span data-stu-id="04367-208">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="04367-209">Se Ionide é dividido em seu computador e nenhum deles tiver corrigido o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o pacote de plug-in.</span><span class="sxs-lookup"><span data-stu-id="04367-209">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="04367-210">Ionide é um projeto de código-fonte aberto criado e mantido por membros da comunidade do F#.</span><span class="sxs-lookup"><span data-stu-id="04367-210">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="04367-211">Reportar problemas e fique à vontade contribuir com o [Ionide VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="04367-211">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="04367-212">Se você tiver um problema ao relatório, siga [as instruções para obter os logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="04367-212">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="04367-213">Você também pode fazer para obter ajuda dos desenvolvedores Ionide e comunidade do F# na [Ionide Gitter canal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="04367-213">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="04367-214">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="04367-214">Next steps</span></span>

<span data-ttu-id="04367-215">Para saber mais sobre F# e os recursos da linguagem, fazer check-out [Tour do F#](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="04367-215">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
