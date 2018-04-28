---
title: Introdução ao C# e Visual Studio Code – Guia do C#
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: d4ee1c9ef66ef61156453786f65d16470d7a5ea2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="7e4e3-103">Introdução ao Visual Studio Code e C#</span><span class="sxs-lookup"><span data-stu-id="7e4e3-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="7e4e3-104">O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="7e4e3-105">Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e4e3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7e4e3-106">Prerequisites</span></span>

1. <span data-ttu-id="7e4e3-107">Instalar o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="7e4e3-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="7e4e3-108">Instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="7e4e3-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="7e4e3-109">Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="7e4e3-110">Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="7e4e3-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="7e4e3-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="7e4e3-111">Hello World</span></span>

<span data-ttu-id="7e4e3-112">Vamos começar com um simples programa "Olá, Mundo" no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7e4e3-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="7e4e3-113">Abra um projeto:</span><span class="sxs-lookup"><span data-stu-id="7e4e3-113">Open a project:</span></span>

    * <span data-ttu-id="7e4e3-114">Abra o Visual Studio Core.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="7e4e3-115">Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**; ou.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="7e4e3-116">Selecione **Arquivo** > **Abrir Pasta** no menu principal para abrir a pasta em que você deseja armazenar seu projeto C# e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="7e4e3-117">Para nosso exemplo, estamos criando uma pasta para nosso projeto chamado *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="7e4e3-119">Inicialize um projeto em C#:</span><span class="sxs-lookup"><span data-stu-id="7e4e3-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="7e4e3-120">Abra o Terminal Integrado do Visual Studio Code selecionando **Exibir** > **Terminal Integrado** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="7e4e3-121">Na janela do terminal, digite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="7e4e3-122">Este comando cria um arquivo de projeto `HelloWorld.csproj` e um arquivo de código `Program.cs` com um código simples, que imprime "Hello, World!" quando executado.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![O novo comando dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="7e4e3-124">Resolva as dependências de build:</span><span class="sxs-lookup"><span data-stu-id="7e4e3-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="7e4e3-125">Para o **.NET Core 1.x**, digite `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="7e4e3-126">Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![O comando de restauração dotnet](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="7e4e3-128">Execute o programa "Olá, Mundo":</span><span class="sxs-lookup"><span data-stu-id="7e4e3-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="7e4e3-129">Digite `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-129">Type `dotnet run`.</span></span> 

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="7e4e3-131">Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="7e4e3-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="7e4e3-132">Depurar</span><span class="sxs-lookup"><span data-stu-id="7e4e3-132">Debug</span></span>

1. <span data-ttu-id="7e4e3-133">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="7e4e3-134">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](http://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="7e4e3-136">O Visual Studio Code solicitará que você adicione os ativos ausentes para compilar e depurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="7e4e3-137">Selecione **Sim** na barra superior.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-137">Select **Yes**.</span></span> 

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="7e4e3-139">Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Abra a guia Depurar](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="7e4e3-141">Localize a seta verde na parte superior do painel.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="7e4e3-142">Certifique-se que a lista suspensa ao lado tenha `.NET Core Launch (console)` selecionado.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Seleção do .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="7e4e3-144">Adicione um ponto de interrupção ao seu código. Para isso, clique no **editor de margem** logo à esquerda dos números de linha no editor. Para este exemplo, faça isso na linha 9.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="7e4e3-146">Para iniciar a depuração, use a tecla <kbd>F5</kbd> ou a seta verde.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="7e4e3-147">O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="7e4e3-148">Durante a depuração, você pode exibir as variáveis locais no painel superior esquerdo ou usar o console de depuração.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Executar e depurar](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="7e4e3-150">Selecione a seta verde na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interrompê-la.</span><span class="sxs-lookup"><span data-stu-id="7e4e3-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="7e4e3-151">Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="7e4e3-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e4e3-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e4e3-152">See also</span></span>
<span data-ttu-id="7e4e3-153">[Configurando o Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="7e4e3-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="7e4e3-154">Depurando no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e4e3-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
