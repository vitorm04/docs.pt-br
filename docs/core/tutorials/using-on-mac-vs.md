---
title: Introdução ao .NET Core usando o Visual Studio para Mac
description: Este tópico explica como compilar um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740486"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="62e51-103">Introdução ao .NET Core no macOS, usando o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="62e51-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="62e51-104">O Visual Studio para Mac fornece um IDE (Ambiente de desenvolvimento integrado) completo para desenvolver aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62e51-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="62e51-105">Este artigo orienta você pela criação de um aplicativo de console simples usando o Visual Studio para Mac e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62e51-105">This article walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="62e51-106">Seus comentários são muito importantes.</span><span class="sxs-lookup"><span data-stu-id="62e51-106">Your feedback is highly valued.</span></span> <span data-ttu-id="62e51-107">Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="62e51-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="62e51-108">No Visual Studio para Mac, escolha **Ajuda** > **Relatar um Problema** no menu, ou **Relatar um Problema** na tela de boas-vindas. Isso abrirá uma janela para registrar um relatório de bugs.</span><span class="sxs-lookup"><span data-stu-id="62e51-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="62e51-109">Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="62e51-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="62e51-110">Para fazer uma sugestão, escolha **Ajuda** > **Forneça uma Sugestão** no menu ou **Forneça uma Sugestão** na tela de boas-vindas. Isso levará você até a página da Web da [Comunidade de Desenvolvedores do Visual Studio para Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="62e51-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62e51-111">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="62e51-111">Prerequisites</span></span>

<span data-ttu-id="62e51-112">Consulte o artigo [dependências e requisitos do .NET Core](../install/dependencies.md?pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="62e51-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos) article.</span></span>

<span data-ttu-id="62e51-113">Verifique o artigo de [suporte do .NET Core](/visualstudio/mac/net-core-support) para garantir que você esteja usando uma versão com suporte do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62e51-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="62e51-114">Introdução</span><span class="sxs-lookup"><span data-stu-id="62e51-114">Get started</span></span>

<span data-ttu-id="62e51-115">Se você já tiver instalado os pré-requisitos e o Visual Studio para Mac, ignore esta seção e vá até [Criar um projeto](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="62e51-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="62e51-116">Execute estas etapas para instalar os pré-requisitos e o Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="62e51-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="62e51-117">Baixe o [Instalador do Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="62e51-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="62e51-118">Execute o instalador.</span><span class="sxs-lookup"><span data-stu-id="62e51-118">Run the installer.</span></span> <span data-ttu-id="62e51-119">Leia e aceite o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="62e51-119">Read and accept the license agreement.</span></span> <span data-ttu-id="62e51-120">Durante a instalação, escolha a opção para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62e51-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="62e51-121">Você tem a oportunidade de instalar o Xamarin, uma tecnologia de desenvolvimento de aplicativo móvel multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="62e51-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="62e51-122">A instalação do Xamarin e de seus componentes relacionados é opcional para o desenvolvimento em .NET Core.</span><span class="sxs-lookup"><span data-stu-id="62e51-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="62e51-123">Para um passo a passo do processo de instalação do Visual Studio para Mac, confira [Documentação do Visual Studio para Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="62e51-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="62e51-124">Após a conclusão da instalação, inicie o IDE do Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="62e51-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="62e51-125">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="62e51-125">Creating a project</span></span>

1. <span data-ttu-id="62e51-126">Selecione **novo** na janela iniciar.</span><span class="sxs-lookup"><span data-stu-id="62e51-126">Select **New** on the start window.</span></span>

   ![O botão Novo na tela de Boas-vindas do Visual Studio para Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="62e51-128">Na caixa de diálogo **Novo Projeto**, selecione **Aplicativo** sob o nó **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="62e51-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="62e51-129">Selecione o modelo **Aplicativo de Console** e logo depois **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="62e51-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Lista de modelos de novo projeto](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="62e51-131">Se você tiver mais de uma versão do .NET Core instalada, escolha a estrutura de destino para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="62e51-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="62e51-132">Digite "HelloWorld" para o **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="62e51-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="62e51-133">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="62e51-133">Select **Create**.</span></span>

   ![Configurar a caixa de diálogo Novo Aplicativo de Console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="62e51-135">Aguarde enquanto as dependências do projeto são restauradas.</span><span class="sxs-lookup"><span data-stu-id="62e51-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="62e51-136">O projeto tem um único arquivo em C#, *Program.cs*, que contém uma classe `Program` com um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="62e51-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="62e51-137">A instrução `Console.WriteLine` produzirá "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="62e51-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="62e51-138">no console quando o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="62e51-138">to the console when the app is run.</span></span>

   ![Janela principal com o arquivo Program.cs aberto](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="62e51-140">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="62e51-140">Run the application</span></span>

<span data-ttu-id="62e51-141">Execute o aplicativo no modo de Depurar usando ⌘ ↵ (Command+Enter) ou no modo Liberar usando ⌥ ⌘ ↵ (Option+Command+Enter).</span><span class="sxs-lookup"><span data-stu-id="62e51-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![O painel Saída do Aplicativo mostra Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="62e51-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="62e51-143">Next step</span></span>

<span data-ttu-id="62e51-144">O tópico [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac](using-on-mac-vs-full-solution.md) mostra como compilar uma solução completa do .NET Core que inclui uma biblioteca reutilizável e testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="62e51-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
