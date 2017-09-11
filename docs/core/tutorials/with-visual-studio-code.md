---
title: "Introdução ao Visual Studio Code e C# – Guia do C# | Microsoft Docs"
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
keywords: "C#, Introdução, Aquisição, Instalação, Visual Studio Code, Plataforma Cruzada"
author: kendrahavens
ms.author: mairaw
ms.date: 8/01/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.translationtype: HT
ms.sourcegitcommit: 3bd8800e7410ae4a3b89f5962af957789edd48b0
ms.openlocfilehash: a10fda5663f0a49069388ee8ee7a9ebb575cd549
ms.contentlocale: pt-br
ms.lasthandoff: 08/03/2017

---

# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="af025-104">Introdução ao Visual Studio Code e C#</span><span class="sxs-lookup"><span data-stu-id="af025-104">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="af025-105">O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="af025-105">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="af025-106">Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.</span><span class="sxs-lookup"><span data-stu-id="af025-106">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af025-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="af025-107">Prerequisites</span></span>

1. <span data-ttu-id="af025-108">Instalar o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="af025-108">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="af025-109">Instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="af025-109">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="af025-110">Instalar a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) do Visual Studio Code Marketplace.</span><span class="sxs-lookup"><span data-stu-id="af025-110">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) from the Visual Studio Code Marketplace.</span></span>

## <a name="hello-world"></a><span data-ttu-id="af025-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="af025-111">Hello World</span></span>

<span data-ttu-id="af025-112">Vamos começar com um simples programa "Olá, Mundo" no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="af025-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="af025-113">Abra um projeto:</span><span class="sxs-lookup"><span data-stu-id="af025-113">Open a project:</span></span>

    * <span data-ttu-id="af025-114">Abra o Visual Studio Core.</span><span class="sxs-lookup"><span data-stu-id="af025-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="af025-115">Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**.</span><span class="sxs-lookup"><span data-stu-id="af025-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="af025-116">Selecione a pasta que você deseja que seu projeto em C# esteja e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="af025-116">Select the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="af025-117">Para nosso exemplo, vamos criar uma pasta para nosso projeto chamado 'HelloWorld'.</span><span class="sxs-lookup"><span data-stu-id="af025-117">For our example, we'll create a folder for our project named 'HelloWorld'.</span></span> 

  ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

    * <span data-ttu-id="af025-119">Como alternativa, você pode selecionar **Arquivo** > **Abrir Pasta** no menu principal para abrir a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="af025-119">Alternatively, you can select **File** > **Open Folder** from the main menu to open your project folder.</span></span>

2. <span data-ttu-id="af025-120">Inicialize um projeto em C#:</span><span class="sxs-lookup"><span data-stu-id="af025-120">Initialize a C# project:</span></span>
    * <span data-ttu-id="af025-121">Abra o Terminal Integrado do Visual Studio Code digitando <kbd>CTRL</kbd>+<kbd>\\`</kbd> (acento grave).</span><span class="sxs-lookup"><span data-stu-id="af025-121">Open the Integrated Terminal from Visual Studio Code by typing <kbd>CTRL</kbd>+<kbd>\\`</kbd> (backtick).</span></span> <span data-ttu-id="af025-122">Como alternativa, é possível selecionar **Exibir** > **Terminal Integrado** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="af025-122">Alternatively, you can select **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="af025-123">Na janela do terminal, digite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="af025-123">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="af025-124">Isso cria um arquivo `Program.cs` em sua pasta com um programa simples "Olá, Mundo" já escrito, junto com um arquivo de projeto em C# chamado `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="af025-124">This creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

  ![O novo comando dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="af025-126">Resolva os ativos do build:</span><span class="sxs-lookup"><span data-stu-id="af025-126">Resolve the build assets:</span></span>

    * <span data-ttu-id="af025-127">Para **.NET Core 1.1**, digite `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="af025-127">For **.NET Core 1.1**, type `dotnet restore`.</span></span> <span data-ttu-id="af025-128">Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="af025-128">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

   ![O comando de restauração dotnet](media/with-visual-studio-code/dotnetrestore.png)

    * <span data-ttu-id="af025-130">Para **.NET Core 2.0**, esta etapa é opcional.</span><span class="sxs-lookup"><span data-stu-id="af025-130">For **.NET Core 2.0**, this step is optional.</span></span> <span data-ttu-id="af025-131">O comando `dotnet restore` é executado automaticamente quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="af025-131">The `dotnet restore` command executes automatically when a new project is created.</span></span>

4. <span data-ttu-id="af025-132">Execute o programa "Olá, Mundo":</span><span class="sxs-lookup"><span data-stu-id="af025-132">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="af025-133">Digite `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="af025-133">Type `dotnet run`.</span></span> 

  ![O comando de execução dotnet](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="af025-135">Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="af025-135">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="af025-136">Depurar</span><span class="sxs-lookup"><span data-stu-id="af025-136">Debug</span></span>
1. <span data-ttu-id="af025-137">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="af025-137">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="af025-138">Na primeira vez que você abrir um arquivo do C# no Visual Studio Code, o [OmniSharp](http://www.omnisharp.net/) será carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="af025-138">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) will load in the editor.</span></span>

  ![Abra o arquivo Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="af025-140">O Visual Studio Code solicitará que você adicione os ativos ausentes para compilar e depurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af025-140">Visual Studio Code will prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="af025-141">Selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="af025-141">Select **Yes**.</span></span> 

  ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="af025-143">Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="af025-143">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

  ![Abra a guia Depurar](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="af025-145">Localize a seta verde na parte superior do painel.</span><span class="sxs-lookup"><span data-stu-id="af025-145">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="af025-146">Certifique-se que a lista suspensa ao lado tenha `.NET Core Launch (console)` selecionado.</span><span class="sxs-lookup"><span data-stu-id="af025-146">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

  ![Seleção do .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="af025-148">Adicione um ponto de interrupção ao seu projeto clicando na **margem do editor** (no espaço à esquerda dos números de linha no editor) ao lado da linha 9.</span><span class="sxs-lookup"><span data-stu-id="af025-148">Add a breakpoint to your project by clicking on the **editor margin** (the space on the left of the line numbers in the editor) next to line 9.</span></span>

  ![Definindo um ponto de interrupção](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="af025-150">Selecione <kbd>F5</kbd> ou a seta verde para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="af025-150">Select <kbd>F5</kbd> or the green arrow to start debugging.</span></span> <span data-ttu-id="af025-151">O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="af025-151">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="af025-152">Durante a depuração, você pode exibir as variáveis locais no painel superior esquerdo ou usar o console de depuração.</span><span class="sxs-lookup"><span data-stu-id="af025-152">While debugging you can view your local variables in the top left pane or use the debug console.</span></span>

  ![Executar e depurar](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="af025-154">Selecione a seta verde na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interrompê-la.</span><span class="sxs-lookup"><span data-stu-id="af025-154">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="af025-155">Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="af025-155">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af025-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af025-156">See also</span></span>
<span data-ttu-id="af025-157">[Configurando o Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="af025-157">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="af025-158">Depurando no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af025-158">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)

