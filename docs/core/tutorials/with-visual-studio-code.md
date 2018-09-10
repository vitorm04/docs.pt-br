---
title: Introdução ao C# e Visual Studio Code – Guia do C#
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 321edcebdea141b7290fa57b47c8d9fc91d3521c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277423"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="33388-103">Introdução ao Visual Studio Code e C#</span><span class="sxs-lookup"><span data-stu-id="33388-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="33388-104">O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="33388-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="33388-105">Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.</span><span class="sxs-lookup"><span data-stu-id="33388-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="33388-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="33388-106">Prerequisites</span></span>

1. <span data-ttu-id="33388-107">Instalar o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="33388-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="33388-108">Instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="33388-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="33388-109">Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="33388-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="33388-110">Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="33388-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="33388-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="33388-111">Hello World</span></span>

<span data-ttu-id="33388-112">Vamos começar com um simples programa "Olá, Mundo" no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="33388-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="33388-113">Abra um projeto:</span><span class="sxs-lookup"><span data-stu-id="33388-113">Open a project:</span></span>

    * <span data-ttu-id="33388-114">Abra o Visual Studio Core.</span><span class="sxs-lookup"><span data-stu-id="33388-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="33388-115">Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**; ou.</span><span class="sxs-lookup"><span data-stu-id="33388-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="33388-116">Selecione **Arquivo** > **Abrir Pasta** no menu principal para abrir a pasta em que você deseja armazenar seu projeto C# e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="33388-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="33388-117">Para nosso exemplo, estamos criando uma pasta para nosso projeto chamado *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="33388-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="33388-119">Inicialize um projeto em C#:</span><span class="sxs-lookup"><span data-stu-id="33388-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="33388-120">Abra o Terminal Integrado do Visual Studio Code selecionando **Exibir** > **Terminal Integrado** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="33388-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="33388-121">Na janela do terminal, digite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="33388-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="33388-122">Este comando cria um arquivo de projeto `HelloWorld.csproj` e um arquivo de código `Program.cs` com um código simples, que imprime "Hello, World!" quando executado.</span><span class="sxs-lookup"><span data-stu-id="33388-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![O novo comando dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="33388-124">Resolva as dependências de build:</span><span class="sxs-lookup"><span data-stu-id="33388-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="33388-125">Para o **.NET Core 1.x**, digite `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="33388-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="33388-126">Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="33388-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![O comando de restauração dotnet](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="33388-128">Execute o programa "Olá, Mundo":</span><span class="sxs-lookup"><span data-stu-id="33388-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="33388-129">Digite `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="33388-129">Type `dotnet run`.</span></span>

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="33388-131">Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="33388-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="33388-132">Depurar</span><span class="sxs-lookup"><span data-stu-id="33388-132">Debug</span></span>

1. <span data-ttu-id="33388-133">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="33388-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="33388-134">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](http://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="33388-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="33388-136">O Visual Studio Code solicitará que você adicione os ativos ausentes para compilar e depurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="33388-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="33388-137">Selecione **Sim** na barra superior.</span><span class="sxs-lookup"><span data-stu-id="33388-137">Select **Yes**.</span></span>

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="33388-139">Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="33388-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Abra a guia Depurar](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="33388-141">Localize a seta verde na parte superior do painel.</span><span class="sxs-lookup"><span data-stu-id="33388-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="33388-142">Certifique-se que a lista suspensa ao lado tenha `.NET Core Launch (console)` selecionado.</span><span class="sxs-lookup"><span data-stu-id="33388-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Seleção do .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="33388-144">Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="33388-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="33388-146">Para iniciar a depuração, use a tecla <kbd>F5</kbd> ou a seta verde.</span><span class="sxs-lookup"><span data-stu-id="33388-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="33388-147">O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="33388-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="33388-148">Durante a depuração, você pode exibir as variáveis locais no painel superior esquerdo ou usar o console de depuração.</span><span class="sxs-lookup"><span data-stu-id="33388-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Executar e depurar](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="33388-150">Selecione a seta verde na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interrompê-la.</span><span class="sxs-lookup"><span data-stu-id="33388-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP]
> <span data-ttu-id="33388-151">Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="33388-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="faq"></a><span data-ttu-id="33388-152">Perguntas Frequentes</span><span class="sxs-lookup"><span data-stu-id="33388-152">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="33388-153">Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="33388-153">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="33388-154">Meu depurador diz: "Nenhuma configuração".</span><span class="sxs-lookup"><span data-stu-id="33388-154">My debugger says "No Configuration."</span></span>

<span data-ttu-id="33388-155">A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você.</span><span class="sxs-lookup"><span data-stu-id="33388-155">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="33388-156">O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="33388-156">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="33388-157">Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug".</span><span class="sxs-lookup"><span data-stu-id="33388-157">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="33388-158">Selecionar isso gera os arquivos de configuração. vscode, launch.json e tasks.json que você precisa.</span><span class="sxs-lookup"><span data-stu-id="33388-158">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="33388-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33388-159">See also</span></span>

* [<span data-ttu-id="33388-160">Configurando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="33388-160">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
* [<span data-ttu-id="33388-161">Depurando no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="33388-161">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
