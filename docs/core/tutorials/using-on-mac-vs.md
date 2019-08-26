---
title: Introdução ao .NET Core no macOS, usando o Visual Studio para Mac
description: Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: 7dd8d5e8828c5337a52e9d1ea207aa5ef568556e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660498"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="3e32d-103">Introdução ao .NET Core no macOS, usando o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="3e32d-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="3e32d-104">O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e32d-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="3e32d-105">Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e32d-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="3e32d-106">Seus comentários são muito importantes.</span><span class="sxs-lookup"><span data-stu-id="3e32d-106">Your feedback is highly valued.</span></span> <span data-ttu-id="3e32d-107">Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="3e32d-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="3e32d-108">No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bugs.</span><span class="sxs-lookup"><span data-stu-id="3e32d-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="3e32d-109">Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="3e32d-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="3e32d-110">Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu ou **Forneça uma Sugestão** na tela de boas-vindas. Isso levará você até a página da Web da [Comunidade de Desenvolvedores do Visual Studio para Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="3e32d-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e32d-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3e32d-111">Prerequisites</span></span>

<span data-ttu-id="3e32d-112">Confira o tópico [Pré-requisitos para .NET Core no Mac](../macos-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="3e32d-112">See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="3e32d-113">Verifique o guia [Suporte do .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) para garantir que você esteja usando uma versão compatível do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e32d-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="3e32d-114">Introdução</span><span class="sxs-lookup"><span data-stu-id="3e32d-114">Get started</span></span>

<span data-ttu-id="3e32d-115">Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Criar um projeto](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="3e32d-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="3e32d-116">Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="3e32d-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="3e32d-117">Baixe o [Instalador do Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="3e32d-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="3e32d-118">Execute o instalador.</span><span class="sxs-lookup"><span data-stu-id="3e32d-118">Run the installer.</span></span> <span data-ttu-id="3e32d-119">Leia e aceite o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="3e32d-119">Read and accept the license agreement.</span></span> <span data-ttu-id="3e32d-120">Durante a instalação, escolha a opção para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e32d-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="3e32d-121">Você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="3e32d-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="3e32d-122">A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e32d-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="3e32d-123">Para um passo a passo do processo de instalação do Visual Studio para Mac, confira [Documentação do Visual Studio para Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="3e32d-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="3e32d-124">Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="3e32d-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="3e32d-125">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="3e32d-125">Creating a project</span></span>

1. <span data-ttu-id="3e32d-126">Escolha **Novo** na Janela de Início.</span><span class="sxs-lookup"><span data-stu-id="3e32d-126">Select **New** on the Start Window.</span></span>

   ![O botão Novo na tela de Boas-vindas do Visual Studio para Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="3e32d-128">Na caixa de diálogo **Novo Projeto**, selecione **Aplicativo** sob o nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="3e32d-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="3e32d-129">Selecione o modelo **Aplicativo de Console** e logo depois **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3e32d-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Lista de modelos de novo projeto](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="3e32d-131">Se você tiver mais de uma versão do .NET Core instalada, escolha a estrutura de destino para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3e32d-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="3e32d-132">Digite "HelloWorld" para o **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3e32d-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="3e32d-133">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="3e32d-133">Select **Create**.</span></span>

   ![Configurar a caixa de diálogo Novo Aplicativo de Console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="3e32d-135">Aguarde enquanto as dependências do projeto são restauradas.</span><span class="sxs-lookup"><span data-stu-id="3e32d-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="3e32d-136">O projeto tem um único arquivo em C#, *Program.cs*, que contém uma classe `Program` com um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="3e32d-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="3e32d-137">A instrução `Console.WriteLine` produzirá "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3e32d-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="3e32d-138">no console quando o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="3e32d-138">to the console when the app is run.</span></span>

   ![Janela principal com o arquivo Program.cs aberto](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="3e32d-140">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3e32d-140">Run the application</span></span>

<span data-ttu-id="3e32d-141">Execute o aplicativo no modo de Depurar usando ⌘ ↵ (Command+Enter) ou no modo Liberar usando ⌥ ⌘ ↵ (Option+Command+Enter).</span><span class="sxs-lookup"><span data-stu-id="3e32d-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![O painel Saída do Aplicativo mostra Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="3e32d-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3e32d-143">Next step</span></span>

<span data-ttu-id="3e32d-144">O tópico [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac](using-on-mac-vs-full-solution.md) mostra como compilar uma solução completa do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="3e32d-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
