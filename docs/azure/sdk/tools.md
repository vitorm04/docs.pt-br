---
title: Ferramentas para desenvolvedores .NET do Azure e .NET Core
description: Obtenha as ferramentas para começar a usar as bibliotecas .NET do Azure em um ambiente Windows, Linux ou Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071937"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="417c0-103">Ferramentas para desenvolvedores .NET e .NET Core do Azure</span><span class="sxs-lookup"><span data-stu-id="417c0-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="417c0-104">Downloads do SDK</span><span class="sxs-lookup"><span data-stu-id="417c0-104">SDK downloads</span></span>

<span data-ttu-id="417c0-105">As bibliotecas Azure para .NET são implementadas como [pacotes NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="417c0-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="417c0-106">Consulte a referência da [API](/dotnet/api/overview/azure/?view=azure-dotnet) para obter instruções de instalação organizadas pelo serviço Azure.</span><span class="sxs-lookup"><span data-stu-id="417c0-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="417c0-107">Ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="417c0-107">Development tools</span></span>

<span data-ttu-id="417c0-108">O Visual Studio possui ferramentas para muitos serviços do Azure embutidos.</span><span class="sxs-lookup"><span data-stu-id="417c0-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="417c0-109">Alguns serviços do Azure têm ferramentas ou emuladores adicionais disponíveis, como [o Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="417c0-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="417c0-110">Consulte a documentação do seu serviço Azure para quaisquer ferramentas adicionais, se necessário.</span><span class="sxs-lookup"><span data-stu-id="417c0-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="417c0-111">Estas instruções instalam o ambiente de desenvolvimento inicial recomendado para o seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="417c0-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="417c0-112">Windows</span><span class="sxs-lookup"><span data-stu-id="417c0-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="417c0-113">As versões do Visual Studio 2017 e posteriormente têm suporte integrado para o desenvolvimento do Azure.</span><span class="sxs-lookup"><span data-stu-id="417c0-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="417c0-114">As etapas abaixo descrevem a habilitação do suporte ao desenvolvimento do Azure no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="417c0-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="417c0-115">Para o Visual Studio 2015 e anterior, <a href="vs2015-install.md">siga estas instruções</a>.</span><span class="sxs-lookup"><span data-stu-id="417c0-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="417c0-116">Passo 1: Baixar visual studio 2019</span><span class="sxs-lookup"><span data-stu-id="417c0-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="417c0-117">Você pode pular essa etapa se já tiver o Visual Studio 2019 instalado.</span><span class="sxs-lookup"><span data-stu-id="417c0-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="417c0-118">Baixar o Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="417c0-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="417c0-119">Etapa 2: instalar as duas cargas de trabalho do Azure</span><span class="sxs-lookup"><span data-stu-id="417c0-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="417c0-120">No instalador do Visual Studio, instale o Visual Studio (ou modifique uma instalação existente).</span><span class="sxs-lookup"><span data-stu-id="417c0-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="417c0-121">Certifique-se de que as cargas de trabalho de desenvolvimento e *desenvolvimento de ASP.NET e desenvolvimento web* do *Azure* sejam selecionadas.</span><span class="sxs-lookup"><span data-stu-id="417c0-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="417c0-122">Etapa 3: desenvolver com o .NET no Azure</span><span class="sxs-lookup"><span data-stu-id="417c0-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="417c0-123">Comece [implantando seu primeiro aplicativo Web ASP.NET Core no Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="417c0-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="417c0-124">macOS</span><span class="sxs-lookup"><span data-stu-id="417c0-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="417c0-125">O Visual Studio para Mac tem tudo o que você precisa para desenvolvimento do Azure.</span><span class="sxs-lookup"><span data-stu-id="417c0-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="417c0-126">Etapa 1: baixar o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="417c0-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="417c0-127">Baixar o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="417c0-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="417c0-128">Durante a instalação, as ferramentas do Azure são selecionadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="417c0-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="417c0-129">Linux</span><span class="sxs-lookup"><span data-stu-id="417c0-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="417c0-130">O Visual Studio Code tem tudo o que você precisa para desenvolvimento do Azure no Linux.</span><span class="sxs-lookup"><span data-stu-id="417c0-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="417c0-131">Etapa 1: Baixar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="417c0-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="417c0-132">O SDK e as ferramentas de linha de comando para aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="417c0-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="417c0-133">Baixar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="417c0-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="417c0-134">Etapa 2: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="417c0-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="417c0-135">Edite e depure aplicativos .NET Core em qualquer sistema operacional: Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="417c0-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="417c0-136">Baixar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="417c0-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
