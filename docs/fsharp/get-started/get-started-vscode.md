---
title: Introdução ao F# no Visual Studio Code
description: Saiba como usar F# o com Visual Studio Code e o pacote de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204906"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="6ac7b-103">Introdução ao F# no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6ac7b-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="6ac7b-104">Você pode gravar F# em [Visual Studio Code](https://code.visualstudio.com) com o [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) para obter uma experiência excelente de plataforma cruzada e leve em ambiente de desenvolvimento integrado com IntelliSense e refatoração de código.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="6ac7b-105">Visite [Ionide.Io](http://ionide.io) para saber mais sobre o plug-in.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="6ac7b-106">Para começar, verifique se você tem [ F# o e o plug-in Ionide instalado corretamente](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="6ac7b-107">Criar seu primeiro projeto com o Ionide</span><span class="sxs-lookup"><span data-stu-id="6ac7b-107">Create your first project with Ionide</span></span>

<span data-ttu-id="6ac7b-108">Para criar um novo F# projeto, abra uma linha de comando e crie um novo projeto com o CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

<span data-ttu-id="6ac7b-109">Após a conclusão, altere o diretório para o projeto e abra Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="6ac7b-110">Depois que o projeto for carregado no Visual Studio Code, você deverá F# ver o painel de Gerenciador de soluções no lado esquerdo da janela aberta.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="6ac7b-111">Isso significa que o Ionide carregou com êxito o projeto que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="6ac7b-112">Você pode escrever código no editor antes desse ponto no tempo, mas assim que isso acontecer, tudo concluiu o carregamento.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="6ac7b-113">Configurar F# interativo</span><span class="sxs-lookup"><span data-stu-id="6ac7b-113">Configure F# interactive</span></span>

<span data-ttu-id="6ac7b-114">Primeiro, verifique se o script do .NET Core é o seu ambiente de script padrão:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="6ac7b-115">Abra as configurações de Visual Studio Code (**código** > **preferências** > **configurações**).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="6ac7b-116">Procure o termo  **F# script**.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="6ac7b-117">Clique na caixa de seleção que diz **FSharp: usar scripts do SDK**.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="6ac7b-118">Isso é necessário no momento devido a alguns comportamentos herdados em scripts baseados em .NET Framework que não funcionam com o script do .NET Core e o Ionide está se empenhando atualmente para a compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="6ac7b-119">No futuro, o script do .NET Core se tornará o padrão.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="6ac7b-120">Escreva seu primeiro script</span><span class="sxs-lookup"><span data-stu-id="6ac7b-120">Write your first script</span></span>

<span data-ttu-id="6ac7b-121">Depois de configurar Visual Studio Code para usar o script do .NET Core, navegue até o modo de exibição do Explorer em Visual Studio Code e crie um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="6ac7b-122">Nomeie-o como *MyFirstScript. fsx*.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="6ac7b-123">Agora, adicione o seguinte código a ele:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="6ac7b-124">Essa função converte uma palavra em uma forma de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="6ac7b-125">A próxima etapa é avaliá-lo F# usando o Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="6ac7b-126">Realce a função inteira (deve ter 11 linhas).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="6ac7b-127">Depois de realçar, mantenha pressionada a tecla **ALT** e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="6ac7b-128">Você notará uma janela de terminal exibida na parte inferior da tela e ela deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Exemplo de F# saída interativa com Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="6ac7b-130">Isso fazia três coisas:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-130">This did three things:</span></span>

1. <span data-ttu-id="6ac7b-131">Ele iniciou o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-131">It started the FSI process.</span></span>
2. <span data-ttu-id="6ac7b-132">Ele enviou o código realçado sobre o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="6ac7b-133">O processo do FSI avaliou o código que você enviou.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="6ac7b-134">Como o que você enviou foi uma [função](../language-reference/functions/index.md), agora você pode chamar essa função com o FSI!</span><span class="sxs-lookup"><span data-stu-id="6ac7b-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="6ac7b-135">Na janela interativa, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="6ac7b-136">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="6ac7b-137">Agora, vamos tentar com uma vogal como a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="6ac7b-138">Insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="6ac7b-139">Você deverá ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="6ac7b-140">A função parece estar funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-140">The function appears to be working as expected.</span></span> <span data-ttu-id="6ac7b-141">Parabéns, você acabou de escrever sua F# primeira função em Visual Studio Code e a avaliou com o FSI!</span><span class="sxs-lookup"><span data-stu-id="6ac7b-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="6ac7b-142">Como você deve ter notado, as linhas no FSI são encerradas com `;;`.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="6ac7b-143">Isso ocorre porque o FSI permite que você insira várias linhas.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="6ac7b-144">O `;;` no final permite que o FSI saiba quando o código é concluído.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="6ac7b-145">Explicando o código</span><span class="sxs-lookup"><span data-stu-id="6ac7b-145">Explaining the code</span></span>

<span data-ttu-id="6ac7b-146">Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="6ac7b-147">Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e a converte em uma representação Pig-Latin dessa palavra.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="6ac7b-148">As regras para isso são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-148">The rules for this are as follows:</span></span>

<span data-ttu-id="6ac7b-149">Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" ao final da palavra.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="6ac7b-150">Se não começar com uma vogal, mova o primeiro caractere para o final da palavra e adicione "o".</span><span class="sxs-lookup"><span data-stu-id="6ac7b-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="6ac7b-151">Você pode ter notado o seguinte no FSI:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="6ac7b-152">Isso declara que `toPigLatin` é uma função que usa uma `string` como entrada (chamada `word`) e retorna outra `string`.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="6ac7b-153">Isso é conhecido como a [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da F# chave para entender F# o código.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="6ac7b-154">Você também observará isso se passar o mouse sobre a função em Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="6ac7b-155">No corpo da função, você observará duas partes distintas:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="6ac7b-156">Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="6ac7b-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="6ac7b-157">Uma [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e constrói um valor de retorno dos caracteres de entrada com base em se o primeiro caractere era uma vogal ou não:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="6ac7b-158">O fluxo de `toPigLatin` é assim:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="6ac7b-159">Verifique se o primeiro caractere da palavra de entrada é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="6ac7b-160">Se for, anexe "Sim" ao final da palavra.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="6ac7b-161">Caso contrário, mova esse primeiro caractere para o final da palavra e adicione "</span><span class="sxs-lookup"><span data-stu-id="6ac7b-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="6ac7b-162">Há uma coisa final a ser observada sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitas outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="6ac7b-163">Isso ocorre porque F# o é baseado em expressão e a última expressão no corpo de uma função é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="6ac7b-164">Como `if..then..else` é, em si, uma expressão, o corpo do bloco de `then` ou o corpo do bloco de `else` será retornado dependendo do valor de entrada.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="6ac7b-165">Transforme o aplicativo de console em um gerador de Pig Latin</span><span class="sxs-lookup"><span data-stu-id="6ac7b-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="6ac7b-166">As seções anteriores neste artigo demonstraram uma primeira etapa comum na escrita F# de código: escrever uma função inicial e executá-la interativamente com o FSI.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="6ac7b-167">Isso é conhecido como desenvolvimento controlado por REPL, em que [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Read-Evaluate-Print loop".</span><span class="sxs-lookup"><span data-stu-id="6ac7b-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="6ac7b-168">É uma ótima maneira de experimentar a funcionalidade até que você tenha algo funcionando.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="6ac7b-169">A próxima etapa no desenvolvimento controlado por REPL é mover o código funcional para um F# arquivo de implementação.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="6ac7b-170">Em seguida, ele pode ser compilado F# pelo compilador em um assembly que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="6ac7b-171">Para começar, abra o arquivo *Program. FS* criado anteriormente com o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="6ac7b-172">Você observará que algum código já está lá.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="6ac7b-173">Em seguida, crie um novo [`module`](../language-reference/modules.md) chamado `PigLatin` e copie a função `toPigLatin` que você criou anteriormente como tal:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="6ac7b-174">Esse módulo deve estar acima da função `main` e abaixo da declaração `open System`.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="6ac7b-175">A ordem das declarações é F#importante no, portanto, você precisará definir a função antes de chamá-la em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="6ac7b-176">Agora, na função `main`, chame sua função de gerador Pig Latin nos argumentos:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="6ac7b-177">Agora você pode executar o aplicativo de console na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-177">Now you can run your console app from the command line:</span></span>

```console
dotnet run apple banana
```

<span data-ttu-id="6ac7b-178">E você verá que ele gera o mesmo resultado que o arquivo de script, mas desta vez como um programa em execução!</span><span class="sxs-lookup"><span data-stu-id="6ac7b-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="6ac7b-179">Solução de problemas do Ionide</span><span class="sxs-lookup"><span data-stu-id="6ac7b-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="6ac7b-180">Aqui estão algumas maneiras de solucionar alguns problemas que você pode encontrar:</span><span class="sxs-lookup"><span data-stu-id="6ac7b-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="6ac7b-181">Para obter os recursos de edição de código do Ionide F# , os arquivos precisam ser salvos em disco e dentro de uma pasta que está aberta no espaço de trabalho Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="6ac7b-182">Se você fez alterações no seu sistema ou instalou os pré-requisitos do Ionide com Visual Studio Code abrir, reinicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="6ac7b-183">Se você tiver caracteres inválidos em seus diretórios de projeto, o Ionide poderá não funcionar.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="6ac7b-184">Renomeie os diretórios do projeto se esse for o caso.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="6ac7b-185">Se nenhum dos comandos Ionide estiver funcionando, verifique suas [associações de teclas Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você está substituindo-as por acidente.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-185">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="6ac7b-186">Se o Ionide for interrompido em seu computador e nenhuma das opções acima tiver corrigido o problema, tente remover o diretório `ionide-fsharp` em seu computador e reinstalar o pacote de plug-in.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="6ac7b-187">Se um projeto não for carregado (o F# Gerenciador de soluções mostrará isso), clique com o botão direito do mouse no projeto e clique em **Ver detalhes** para obter mais informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="6ac7b-188">Ionide é um projeto de software livre criado e mantido por membros da F# comunidade.</span><span class="sxs-lookup"><span data-stu-id="6ac7b-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="6ac7b-189">Informe os problemas e fique à vontade para contribuir no [repositório GitHub ionide-vscode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="6ac7b-190">Você também pode pedir ajuda para os desenvolvedores e F# a Comunidade do Ionide no [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6ac7b-191">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6ac7b-191">Next steps</span></span>

<span data-ttu-id="6ac7b-192">Para saber mais sobre F# os recursos do idioma, confira o [Tour do F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="6ac7b-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
