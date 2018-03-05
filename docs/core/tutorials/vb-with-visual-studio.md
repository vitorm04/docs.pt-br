---
title: "Compilação de um aplicativo Olá, Mundo com o .NET Core e com Visual Basic no Visual Studio 2017"
description: Saiba como compilar um aplicativo de console simples do .NET Core com o Visual Basic usando o Visual Studio 2017.
keywords: .NET Core, aplicativo do console do .NET Core, Visual Studio 2017
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 0e3dbdb5df72963980f459643fcb5f4588e0029f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="7e771-104">Compilar um aplicativo Olá, Mundo em Visual Basic com o .NET Core no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7e771-104">Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="7e771-105">Este tópico fornece uma introdução passo a passo para compilação, depuração e publicação de um aplicativo de console simples do .NET Core usando Visual Basic no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7e771-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="7e771-106">O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para compilar aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7e771-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="7e771-107">Desde que o aplicativo não tenha dependências específicas da plataforma, ele pode ser executado em qualquer plataforma que tenha como alvo o .NET Core e em qualquer sistema que tenha o .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="7e771-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e771-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7e771-108">Prerequisites</span></span>

<span data-ttu-id="7e771-109">O [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="7e771-109">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="7e771-110">É possível desenvolver seu aplicativo com o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="7e771-110">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="7e771-111">Para obter mais informações, consulte [Pré-requisitos para .NET Core no Windows](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="7e771-111">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="7e771-112">Um aplicativo simples Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="7e771-112">A simple Hello World application</span></span>

<span data-ttu-id="7e771-113">Comece criando um aplicativo de console simples "Olá, Mundo".</span><span class="sxs-lookup"><span data-stu-id="7e771-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="7e771-114">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="7e771-114">Follow these steps:</span></span>

1. <span data-ttu-id="7e771-115">Inicie o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7e771-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="7e771-116">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="7e771-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="7e771-117">Na caixa de diálogo \*Novo projeto\*\*, selecione o nó **Visual Basic** seguido pelo nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="7e771-117">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="7e771-118">Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="7e771-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="7e771-119">Na caixa de texto **Name**, digite "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="7e771-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="7e771-120">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e771-120">Select the **OK** button.</span></span>

   ![Caixa de diálogo Novo Projeto com Aplicativo de Console selecionado](./media/vb-with-visual-studio/new-project.png)
   
1. <span data-ttu-id="7e771-122">O Visual Studio usa o modelo para criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7e771-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="7e771-123">O modelo de aplicativo de console em Visual Basic para o .NET Core define automaticamente uma classe, `Program`, com um único método, `Main`, que usa uma matriz <xref:System.String> como um argumento.</span><span class="sxs-lookup"><span data-stu-id="7e771-123">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="7e771-124">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo tempo de execução quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e771-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="7e771-125">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="7e771-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![O Visual Studio e o novo projeto HelloWorld](./media/vb-with-visual-studio/devenv.png)

   <span data-ttu-id="7e771-127">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="7e771-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="7e771-128">Ele chama o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="7e771-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="7e771-129">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="7e771-129">in the console window.</span></span> <span data-ttu-id="7e771-130">Ao selecionar o botão **HelloWorld** com a seta verde na barra de ferramentas, você pode executar o programa no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="7e771-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="7e771-131">Se fizer isso, a janela do console será visível somente por um breve intervalo antes de ser fechada.</span><span class="sxs-lookup"><span data-stu-id="7e771-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="7e771-132">Isso ocorre porque o método `Main` é encerrado e o aplicativo é fechado assim que a única instrução no método `Main` é executada.</span><span class="sxs-lookup"><span data-stu-id="7e771-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="7e771-133">Para fazer com que o aplicativo pausar antes de fechar a janela do console, adicione o seguinte código imediatamente após a chamada para o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="7e771-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="7e771-134">Esse código solicita que o usuário pressione qualquer tecla e, em seguida, pausa o programa até que uma tecla seja pressionada.</span><span class="sxs-lookup"><span data-stu-id="7e771-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="7e771-135">Na barra de menus, selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="7e771-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="7e771-136">Isso compila seu programa em uma IL (linguagem intermediária) que é convertida em um código binário por um compilador JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="7e771-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="7e771-137">Execute o programa selecionando o botão **HelloWorld** com a seta verde na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7e771-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="7e771-139">Pressione qualquer tecla para fechar a janela de console.</span><span class="sxs-lookup"><span data-stu-id="7e771-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="7e771-140">Aprimorando o aplicativo Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="7e771-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="7e771-141">Aprimore seu aplicativo para solicitar o nome do usuário e exibi-lo juntamente com a data e a hora.</span><span class="sxs-lookup"><span data-stu-id="7e771-141">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="7e771-142">Para modificar e testar o programa, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7e771-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="7e771-143">Insira o código Visual Basic a seguir na janela de código imediatamente após o colchete de abertura que segue a linha `Sub Main(args As String())` e antes do primeiro colchete de fechamento:</span><span class="sxs-lookup"><span data-stu-id="7e771-143">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="7e771-144">Esse código substitui as instruções <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType> e <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> existentes.</span><span class="sxs-lookup"><span data-stu-id="7e771-144">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Arquivo do programa do Visual Studio com o método Main atualizado](./media/vb-with-visual-studio/codewindow.png)

   <span data-ttu-id="7e771-146">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="7e771-146">This code displays "What is your name?"</span></span> <span data-ttu-id="7e771-147">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter.</span><span class="sxs-lookup"><span data-stu-id="7e771-147">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="7e771-148">Ele armazena essa cadeia de caracteres a uma variável chamada `name`.</span><span class="sxs-lookup"><span data-stu-id="7e771-148">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="7e771-149">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="7e771-149">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="7e771-150">Por fim, ele usa uma [cadeia de caracteres interpolada](../../csharp/language-reference/keywords/interpolated-strings.md) para exibir esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="7e771-150">Finally, it uses an [interpolated string](../../csharp/language-reference/keywords/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="7e771-151">Compile o programa selecionando **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="7e771-151">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="7e771-152">Execute o programa no modo de Depuração no Visual Studio selecionando a seta verde na barra de ferramentas, pressionando F5 ou escolhendo o item de menu **Depurar** > **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="7e771-152">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="7e771-153">Responda à solicitação inserindo um nome e pressionando a tecla Enter.</span><span class="sxs-lookup"><span data-stu-id="7e771-153">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="7e771-155">Pressione qualquer tecla para fechar a janela de console.</span><span class="sxs-lookup"><span data-stu-id="7e771-155">Press any key to close the console window.</span></span>

<span data-ttu-id="7e771-156">Você criou e executou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e771-156">You've created and run your application.</span></span> <span data-ttu-id="7e771-157">Para desenvolver um aplicativo profissional, realize algumas etapas adicionais para deixar seu aplicativo pronto para a liberação:</span><span class="sxs-lookup"><span data-stu-id="7e771-157">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="7e771-158">Para obter informações sobre a depuração do aplicativo, consulte [Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7e771-158">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="7e771-159">Para obter informações sobre o desenvolvimento e a publicação de uma versão distribuível do seu aplicativo, consulte [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md) (Publicando um aplicativo Olá, Mundo em C# com o Visual Studio 2017).</span><span class="sxs-lookup"><span data-stu-id="7e771-159">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
