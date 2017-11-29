---
title: "Introdução ao .NET Core em macOS usando o Visual Studio para Mac"
description: "Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="bb9a9-104">Introdução ao .NET Core em macOS usando o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="bb9a9-104">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="bb9a9-105">O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="bb9a9-106">Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-106">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="bb9a9-107">Seus comentários são muito importantes.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-107">Your feedback is highly valued.</span></span> <span data-ttu-id="bb9a9-108">Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="bb9a9-108">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="bb9a9-109">No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bugs.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-109">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="bb9a9-110">Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-110">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="bb9a9-111">Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu, ou **Forneça uma Sugestão** na tela de boas-vindas. Isso levará você até a página de [UserVoice do Visual Studio para Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-111">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb9a9-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bb9a9-112">Prerequisites</span></span>

<span data-ttu-id="bb9a9-113">Confira o tópico [Pré-requisitos para .NET Core no Mac](../../core/macos-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-113">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="bb9a9-114">Introdução</span><span class="sxs-lookup"><span data-stu-id="bb9a9-114">Getting started</span></span>

<span data-ttu-id="bb9a9-115">Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Criar um projeto](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="bb9a9-116">Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="bb9a9-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="bb9a9-117">Baixe o [Instalador do Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-117">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="bb9a9-118">Execute o instalador.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-118">Run the installer.</span></span> <span data-ttu-id="bb9a9-119">Leia e aceite o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-119">Read and accept the license agreement.</span></span> <span data-ttu-id="bb9a9-120">Durante a instalação, você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-120">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="bb9a9-121">A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-121">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="bb9a9-122">Para conferir um passo a passo do processo de instalação do Visual Studio para Mac, veja [Introdução ao Visual Studio para Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="bb9a9-122">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="bb9a9-123">Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-123">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="bb9a9-124">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="bb9a9-124">Creating a project</span></span>

1. <span data-ttu-id="bb9a9-125">Escolha **Novo Projeto** na tela de Boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-125">Select **New Project** on the Welcome screen.</span></span>

   ![Botão Novo Projeto na tela de Boas-vindas do Visual Studio para Mac](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="bb9a9-127">Na caixa de diálogo **Novo Projeto**, selecione **Aplicativo** sob o nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-127">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="bb9a9-128">Selecione o modelo **Aplicativo de Console** e logo depois **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-128">Select the **Console Application** template followed by **Next**.</span></span>

   ![Lista de modelos de novo projeto](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="bb9a9-130">Digite "HelloWorld" para o **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-130">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="bb9a9-131">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-131">Select **Create**.</span></span>

   ![Configurar a caixa de diálogo Novo Aplicativo de Console](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="bb9a9-133">Aguarde enquanto as dependências do projeto são restauradas.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-133">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="bb9a9-134">O projeto tem um único arquivo em C#, *Program.cs*, que contém uma classe `Program` com um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-134">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="bb9a9-135">A instrução `Console.WriteLine` produzirá "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="bb9a9-135">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="bb9a9-136">no console quando o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-136">to the console when the app is run.</span></span>

   ![Janela principal com o arquivo Program.cs aberto](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="bb9a9-138">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb9a9-138">Run the application</span></span>

<span data-ttu-id="bb9a9-139">Execute o aplicativo no modo Depuração usando <kbd>F5</kbd> ou no modo Versão usando <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-139">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![O painel Saída do Aplicativo mostra Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="bb9a9-141">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="bb9a9-141">Next step</span></span>

<span data-ttu-id="bb9a9-142">O tópico [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac](using-on-mac-vs-full-solution.md) mostra como compilar uma solução completa do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="bb9a9-142">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
