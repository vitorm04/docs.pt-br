---
title: 'Introdução à linguagem F # em código do Visual Studio'
description: 'Saiba como usar o F # com o código do Visual Studio e o conjunto de plug-in de Ionide.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728622"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="b20f7-103">Introdução à linguagem F # em código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b20f7-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="b20f7-104">Você pode escrever F # em [código do Visual Studio](https://code.visualstudio.com) com o [Ionide plug-in](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), para obter uma ótima experiência de ambiente de desenvolvimento integrado (IDE) de leve e de plataforma cruzada com o IntelliSense e o código básico refatorações.</span><span class="sxs-lookup"><span data-stu-id="b20f7-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="b20f7-105">Visite [Ionide.io](http://ionide.io) para saber mais sobre o conjunto de plug-in.</span><span class="sxs-lookup"><span data-stu-id="b20f7-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b20f7-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b20f7-106">Prerequisites</span></span>

<span data-ttu-id="b20f7-107">Você deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso dos modelos de projeto em Ionide.</span><span class="sxs-lookup"><span data-stu-id="b20f7-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="b20f7-108">Você pode verificar se ele está instalado corretamente, digitando `git --version` em um prompt de comando e pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b20f7-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="b20f7-109">macOS</span><span class="sxs-lookup"><span data-stu-id="b20f7-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="b20f7-110">Usa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="b20f7-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="b20f7-111">A maneira mais fácil de instalar Mono em macOS é por meio de Homebrew.</span><span class="sxs-lookup"><span data-stu-id="b20f7-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="b20f7-112">Simplesmente digite o seguinte em seu terminal:</span><span class="sxs-lookup"><span data-stu-id="b20f7-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="b20f7-113">Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="b20f7-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="b20f7-114">Linux</span><span class="sxs-lookup"><span data-stu-id="b20f7-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="b20f7-115">No Linux, Ionide também usa [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="b20f7-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="b20f7-116">Se você estiver em Debian ou Ubuntu, você pode usar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="b20f7-117">Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="b20f7-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="b20f7-118">Windows</span><span class="sxs-lookup"><span data-stu-id="b20f7-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="b20f7-119">Se você estiver no Windows, você deve [instalar o Visual Studio com suporte do F #](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="b20f7-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="b20f7-120">Isso instala todos os componentes necessários para escrever, compilar e executar código F #.</span><span class="sxs-lookup"><span data-stu-id="b20f7-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="b20f7-121">Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="b20f7-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="b20f7-122">Instalando o plug-in Ionide e código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b20f7-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="b20f7-123">Você pode instalar o Visual Studio Code do [code.visualstudio.com](https://code.visualstudio.com) site.</span><span class="sxs-lookup"><span data-stu-id="b20f7-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="b20f7-124">Em seguida, clique no ícone de extensões e procure "Ionide":</span><span class="sxs-lookup"><span data-stu-id="b20f7-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="b20f7-125">O plug-in somente necessário para suporte a F # no código do Visual Studio é [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b20f7-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="b20f7-126">No entanto, você também pode instalar [Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter [FORJAR](https://fsharp.github.io/FAKE/) suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter [Paket](https://fsprojects.github.io/Paket/) suporte.</span><span class="sxs-lookup"><span data-stu-id="b20f7-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="b20f7-127">FORJAR e Paket F # comunidade ferramentas adicionais para a criação de projetos e gerenciamento de dependências, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b20f7-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="b20f7-128">Criando seu primeiro projeto com Ionide</span><span class="sxs-lookup"><span data-stu-id="b20f7-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="b20f7-129">Para criar um novo projeto de F #, abra o código do Visual Studio em uma nova pasta (você pode nomeá-lo como desejar).</span><span class="sxs-lookup"><span data-stu-id="b20f7-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="b20f7-130">Em seguida, abra a paleta de comando (**exibição > Paleta comando**) e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="b20f7-131">Isso é alimentado pelo [FORGE](https://github.com/fsharp-editing/Forge) projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="b20f7-132">Se você não vir Opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comando: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="b20f7-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="b20f7-133">Selecione "F #: novo projeto" acessando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b20f7-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="b20f7-134">Isso leva você para a próxima etapa para selecionar um modelo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="b20f7-135">Escolha o `classlib` modelo e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b20f7-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="b20f7-136">Em seguida, selecione um diretório para criar o projeto em.</span><span class="sxs-lookup"><span data-stu-id="b20f7-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="b20f7-137">Se você deixar em branco, ele usa o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b20f7-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="b20f7-138">Por fim, nomeie o projeto na etapa final.</span><span class="sxs-lookup"><span data-stu-id="b20f7-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="b20f7-139">F # usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para os nomes de projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="b20f7-140">Este artigo usa `ClassLibraryDemo` como o nome.</span><span class="sxs-lookup"><span data-stu-id="b20f7-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="b20f7-141">Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b20f7-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="b20f7-142">Se você seguiu a etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo seja exibido com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="b20f7-143">O F # projeto em si, sob o `ClassLibraryDemo` pasta.</span><span class="sxs-lookup"><span data-stu-id="b20f7-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="b20f7-144">A estrutura de diretório correto para a adição de pacotes por meio de [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="b20f7-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="b20f7-145">Uma plataforma cruzada criar script com [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="b20f7-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="b20f7-146">O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.</span><span class="sxs-lookup"><span data-stu-id="b20f7-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="b20f7-147">Um `.gitignore` de arquivo se deseja adicionar este projeto ao controle de origem com base no Git.</span><span class="sxs-lookup"><span data-stu-id="b20f7-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="b20f7-148">Escrevendo um código</span><span class="sxs-lookup"><span data-stu-id="b20f7-148">Writing some code</span></span>

<span data-ttu-id="b20f7-149">Abra o *ClassLibraryDemo* pasta.</span><span class="sxs-lookup"><span data-stu-id="b20f7-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="b20f7-150">Você deve ver os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="b20f7-150">You should see the following files:</span></span>

1. <span data-ttu-id="b20f7-151">`ClassLibraryDemo.fs`, um arquivo de implementação do F # com uma classe definida.</span><span class="sxs-lookup"><span data-stu-id="b20f7-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="b20f7-152">`ClassLibraryDemo.fsproj`, um arquivo de projeto F # usado para compilar este projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="b20f7-153">`Script.fsx`, um arquivo de script F # que carrega o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="b20f7-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="b20f7-154">`paket.references`, um arquivo de Paket que especifica as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="b20f7-155">Abra `Script.fsx`e adicione o seguinte código ao final dele:</span><span class="sxs-lookup"><span data-stu-id="b20f7-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="b20f7-156">Esta função converte uma palavra em uma forma de [Pig latino](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="b20f7-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="b20f7-157">A próxima etapa é avaliar usando F # interativo (FSI).</span><span class="sxs-lookup"><span data-stu-id="b20f7-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="b20f7-158">Realce a função inteira (deve ser 11 linhas).</span><span class="sxs-lookup"><span data-stu-id="b20f7-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="b20f7-159">Depois de selecioná-la, mantenha o **Alt** chave e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b20f7-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="b20f7-160">Você observará que uma janela pop-up abaixo, e ele deverá mostrar algo assim:</span><span class="sxs-lookup"><span data-stu-id="b20f7-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![Exemplo de saída de F # interativo com Ionide](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="b20f7-162">Isso foi três coisas:</span><span class="sxs-lookup"><span data-stu-id="b20f7-162">This did three things:</span></span>

1. <span data-ttu-id="b20f7-163">Iniciar o processo de FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-163">It started the FSI process.</span></span>
2. <span data-ttu-id="b20f7-164">Ele enviado o código realçado sobre o processo FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="b20f7-165">O processo FSI avaliado o código enviados pela.</span><span class="sxs-lookup"><span data-stu-id="b20f7-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="b20f7-166">Porque foi enviado por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI!</span><span class="sxs-lookup"><span data-stu-id="b20f7-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="b20f7-167">Na janela interativa, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="b20f7-168">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="b20f7-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="b20f7-169">Agora, vamos tentar com uma vogal como a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="b20f7-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="b20f7-170">Insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="b20f7-171">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="b20f7-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="b20f7-172">A função parece estar funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="b20f7-172">The function appears to be working as expected.</span></span> <span data-ttu-id="b20f7-173">Parabéns, você criou sua primeira função F # em código do Visual Studio e avaliadas-lo com FSI apenas!</span><span class="sxs-lookup"><span data-stu-id="b20f7-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="b20f7-174">Como você pode ter observado, as linhas no FSI são finalizadas com `;;`.</span><span class="sxs-lookup"><span data-stu-id="b20f7-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="b20f7-175">Isso ocorre porque FSI permite que você insira várias linhas.</span><span class="sxs-lookup"><span data-stu-id="b20f7-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="b20f7-176">O `;;` no final permite FSI saber quando o código for concluído.</span><span class="sxs-lookup"><span data-stu-id="b20f7-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="b20f7-177">Explicando o código</span><span class="sxs-lookup"><span data-stu-id="b20f7-177">Explaining the code</span></span>

<span data-ttu-id="b20f7-178">Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.</span><span class="sxs-lookup"><span data-stu-id="b20f7-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="b20f7-179">Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e o converte em uma representação de Pig-latino da palavra.</span><span class="sxs-lookup"><span data-stu-id="b20f7-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="b20f7-180">As regras para isso são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b20f7-180">The rules for this are as follows:</span></span>

<span data-ttu-id="b20f7-181">Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" para o fim da palavra.</span><span class="sxs-lookup"><span data-stu-id="b20f7-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="b20f7-182">Se ele não começa com uma vogal, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="b20f7-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="b20f7-183">Você pode ter observado FSI o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b20f7-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="b20f7-184">Isso indica que `toPigLatin` é uma função que aceita um `string` como entrada (chamado `word`) e retorna outro `string`.</span><span class="sxs-lookup"><span data-stu-id="b20f7-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="b20f7-185">Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da linguagem F # que é a chave para compreender o código F #.</span><span class="sxs-lookup"><span data-stu-id="b20f7-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="b20f7-186">Você também observa isso se você passar o mouse sobre a função no código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b20f7-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="b20f7-187">O corpo da função, você observará duas partes distintas:</span><span class="sxs-lookup"><span data-stu-id="b20f7-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="b20f7-188">Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="b20f7-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="b20f7-189">Um [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e construções um retorno de valor sem os caracteres de entrada com base em se o primeiro caractere foi uma vogal ou não:</span><span class="sxs-lookup"><span data-stu-id="b20f7-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="b20f7-190">O fluxo de `toPigLatin` é assim:</span><span class="sxs-lookup"><span data-stu-id="b20f7-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="b20f7-191">Verifique se o primeiro caractere da palavra entrada é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="b20f7-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="b20f7-192">Se for, anexe "Sim" para o fim da palavra.</span><span class="sxs-lookup"><span data-stu-id="b20f7-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="b20f7-193">Caso contrário, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.</span><span class="sxs-lookup"><span data-stu-id="b20f7-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="b20f7-194">Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas lá.</span><span class="sxs-lookup"><span data-stu-id="b20f7-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="b20f7-195">Isso ocorre porque o F # é baseada em expressão, e a última expressão no corpo de uma função é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b20f7-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="b20f7-196">Porque `if..then..else` em si for uma expressão, o corpo do `then` bloco ou o corpo do `else` bloco será retornado, dependendo do valor de entrada.</span><span class="sxs-lookup"><span data-stu-id="b20f7-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="b20f7-197">Movendo o código de script para o arquivo de implementação</span><span class="sxs-lookup"><span data-stu-id="b20f7-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="b20f7-198">As seções anteriores neste artigo demonstrou uma primeira etapa comum gravar código F #: gravar uma função inicial e executá-la interativamente com FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="b20f7-199">Isso é conhecido como o desenvolvimento controlado por REPL, onde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Loop de impressão avaliar leitura".</span><span class="sxs-lookup"><span data-stu-id="b20f7-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="b20f7-200">É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="b20f7-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="b20f7-201">A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho em um arquivo de implementação do F #.</span><span class="sxs-lookup"><span data-stu-id="b20f7-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="b20f7-202">Ele pode ser compilado pelo compilador F # em um assembly que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="b20f7-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="b20f7-203">Para começar, abra `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="b20f7-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="b20f7-204">Você observará que algum código já está em lá.</span><span class="sxs-lookup"><span data-stu-id="b20f7-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="b20f7-205">Vá em frente e excluir a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.</span><span class="sxs-lookup"><span data-stu-id="b20f7-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="b20f7-206">Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:</span><span class="sxs-lookup"><span data-stu-id="b20f7-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="b20f7-207">Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionarão, mas certifique-se de manter as duas linhas seguintes no arquivo:</span><span class="sxs-lookup"><span data-stu-id="b20f7-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="b20f7-208">A primeira linha é necessária para FSI script para carregar `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="b20f7-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="b20f7-209">A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo no escopo.</span><span class="sxs-lookup"><span data-stu-id="b20f7-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="b20f7-210">Em seguida, na janela FSI, chame a função com o `PigLatin` módulo definido anteriormente:</span><span class="sxs-lookup"><span data-stu-id="b20f7-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="b20f7-211">Sucesso!</span><span class="sxs-lookup"><span data-stu-id="b20f7-211">Success!</span></span> <span data-ttu-id="b20f7-212">Obter os mesmos resultados como antes, mas agora carregado de um arquivo de implementação do F #.</span><span class="sxs-lookup"><span data-stu-id="b20f7-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="b20f7-213">A principal diferença é que os arquivos de origem F # são compilados em assemblies que podem ser executados em qualquer lugar, não apenas em FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="b20f7-214">Resumo</span><span class="sxs-lookup"><span data-stu-id="b20f7-214">Summary</span></span>

<span data-ttu-id="b20f7-215">Neste artigo, você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="b20f7-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="b20f7-216">Como configurar o código do Visual Studio com Ionide.</span><span class="sxs-lookup"><span data-stu-id="b20f7-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="b20f7-217">Como criar seu primeiro projeto F # com Ionide.</span><span class="sxs-lookup"><span data-stu-id="b20f7-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="b20f7-218">Como usar o F # script para gravar sua primeira função F # em Ionide e, em seguida, execute-o no FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="b20f7-219">Como migrar o código de script com fonte de F # e, em seguida, chamar esse código de FSI.</span><span class="sxs-lookup"><span data-stu-id="b20f7-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="b20f7-220">Você agora está pronto para escrever muito mais código F #, usando o código do Visual Studio e Ionide.</span><span class="sxs-lookup"><span data-stu-id="b20f7-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b20f7-221">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="b20f7-221">Troubleshooting</span></span>

<span data-ttu-id="b20f7-222">Aqui estão algumas maneiras que você pode solucionar determinados problemas que possam ser executadas em:</span><span class="sxs-lookup"><span data-stu-id="b20f7-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="b20f7-223">Para obter recursos de Ionide de edição de código, os arquivos de F # precisam ser salvo em disco e dentro de uma pasta que está aberta no espaço de trabalho de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b20f7-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="b20f7-224">Se tiver sido feitas alterações no sistema ou instalado Ionide pré-requisitos com código do Visual Studio abrir, reinicie o código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b20f7-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="b20f7-225">Verifique que você pode usar o compilador F # e F # interativo da linha de comando sem um caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="b20f7-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="b20f7-226">Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador de F #, e `fsi` ou `fsharpi` para o Visual F # ferramentas no Windows e Mono no Mac/Linux, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b20f7-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="b20f7-227">Se você tem caracteres inválidos em seus diretórios de projeto, Ionide podem não funcionar.</span><span class="sxs-lookup"><span data-stu-id="b20f7-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="b20f7-228">Se esse for o caso, renomeie os diretórios do projeto.</span><span class="sxs-lookup"><span data-stu-id="b20f7-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="b20f7-229">Se nenhum dos comandos Ionide está trabalhando, verifique seu [associações de código do Visual Studio](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por engano.</span><span class="sxs-lookup"><span data-stu-id="b20f7-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="b20f7-230">Se Ionide é dividido em seu computador e nenhum deles corrigiu o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o conjunto de plug-in.</span><span class="sxs-lookup"><span data-stu-id="b20f7-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="b20f7-231">Ionide é um projeto de código aberto criado e mantido por membros da comunidade do F #.</span><span class="sxs-lookup"><span data-stu-id="b20f7-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="b20f7-232">Reportar problemas e fique à vontade para contribuir no [Ionide-o VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b20f7-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="b20f7-233">Se você tiver um problema ao relatório, siga [as instruções para obter logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="b20f7-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="b20f7-234">Você também pode pedir para obter ajuda da comunidade do F # em e desenvolvedores Ionide o [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="b20f7-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b20f7-235">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b20f7-235">Next steps</span></span>

<span data-ttu-id="b20f7-236">Para saber mais sobre F # e os recursos do idioma, check-out [Tour do F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="b20f7-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
