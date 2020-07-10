---
title: Ferramentas para desenvolvedores do .NET do Azure
description: Obtenha as ferramentas para começar a usar as bibliotecas .NET do Azure em um ambiente Windows, Linux ou Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174891"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="6b946-103">Ferramentas do Azure para desenvolvimento com o .NET</span><span class="sxs-lookup"><span data-stu-id="6b946-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="6b946-104">Downloads do SDK</span><span class="sxs-lookup"><span data-stu-id="6b946-104">SDK downloads</span></span>

<span data-ttu-id="6b946-105">As bibliotecas do Azure para .NET são implementadas como [pacotes NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="6b946-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="6b946-106">Consulte a [referência de API](/dotnet/api/overview/azure/?view=azure-dotnet) para obter a documentação de referência organizada pelo serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="6b946-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="6b946-107">Ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="6b946-107">Development tools</span></span>

<span data-ttu-id="6b946-108">O Visual Studio tem ferramentas para muitos serviços do Azure internos.</span><span class="sxs-lookup"><span data-stu-id="6b946-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="6b946-109">Alguns serviços do Azure têm ferramentas ou emuladores adicionais disponíveis, como [Gerenciador de armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="6b946-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="6b946-110">Consulte a documentação do serviço do Azure para obter outras ferramentas, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6b946-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="6b946-111">Selecione seu ambiente de desenvolvimento preferido abaixo.</span><span class="sxs-lookup"><span data-stu-id="6b946-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="6b946-112">Visual Studio no Windows</span><span class="sxs-lookup"><span data-stu-id="6b946-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="6b946-113">O Visual Studio versão 2017 e versões posteriores têm suporte interno para o desenvolvimento do Azure.</span><span class="sxs-lookup"><span data-stu-id="6b946-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="6b946-114">As etapas a seguir descrevem a habilitação do suporte de desenvolvimento do Azure no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6b946-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="6b946-115">Para o Visual Studio 2015 e anterior, <a href="vs2015-install.md">siga estas instruções</a>.</span><span class="sxs-lookup"><span data-stu-id="6b946-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="6b946-116">Etapa 1: baixar o Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6b946-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="6b946-117">Você pode ignorar esta etapa se já tiver o Visual Studio 2019 instalado.</span><span class="sxs-lookup"><span data-stu-id="6b946-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b946-118">Baixar o Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6b946-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="6b946-119">Etapa 2: instalar as duas cargas de trabalho do Azure</span><span class="sxs-lookup"><span data-stu-id="6b946-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="6b946-120">No instalador do Visual Studio, instale o Visual Studio (ou modifique uma instalação existente).</span><span class="sxs-lookup"><span data-stu-id="6b946-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="6b946-121">Verifique se as cargas de trabalho *desenvolvimento do Azure* e *ASP.net e desenvolvimento Web* estão selecionadas.</span><span class="sxs-lookup"><span data-stu-id="6b946-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="6b946-122">Etapa 3: desenvolver com o .NET no Azure</span><span class="sxs-lookup"><span data-stu-id="6b946-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="6b946-123">Comece [implantando seu primeiro aplicativo Web ASP.NET Core no Serviço de Aplicativo do Azure](/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6b946-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="6b946-124">Visual Studio Code (plataforma cruzada)</span><span class="sxs-lookup"><span data-stu-id="6b946-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="6b946-125">Visual Studio Code tem tudo o que você precisa para o desenvolvimento do Azure entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="6b946-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="6b946-126">Etapa 1: Baixar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b946-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="6b946-127">O SDK e as ferramentas de linha de comando para aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b946-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b946-128">Baixar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b946-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="6b946-129">Etapa 2: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6b946-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="6b946-130">Edite e depure aplicativos .NET Core em qualquer sistema operacional: Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="6b946-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b946-131">Baixar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6b946-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="6b946-132">Etapa 3: extensão das ferramentas do Azure</span><span class="sxs-lookup"><span data-stu-id="6b946-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="6b946-133">Instale a extensão de ferramentas do Azure no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6b946-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b946-134">Instalar extensão de ferramentas do Azure</span><span class="sxs-lookup"><span data-stu-id="6b946-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="6b946-135">Etapa 4: desenvolver com o .NET no Azure</span><span class="sxs-lookup"><span data-stu-id="6b946-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="6b946-136">Comece [implantando seu primeiro aplicativo web ASP.NET Core no serviço Azure app no Linux](/azure/app-service/containers/quickstart-dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="6b946-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
