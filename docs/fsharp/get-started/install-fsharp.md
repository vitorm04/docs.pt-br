---
title: Instalar o F#
description: Saiba como instalar F# o com base em seu ambiente.
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855795"
---
# <a name="install-f"></a><span data-ttu-id="80ee4-103">Instalar o F\#</span><span class="sxs-lookup"><span data-stu-id="80ee4-103">Install F\#</span></span>

<span data-ttu-id="80ee4-104">Você pode instalar F# o de várias maneiras, dependendo do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="80ee4-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="80ee4-105">Instalar F# com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80ee4-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="80ee4-106">Se você estiver baixando o [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pela primeira vez, ele instalará primeiro o instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80ee4-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="80ee4-107">Instale o SKU apropriado do Visual Studio a partir do instalador.</span><span class="sxs-lookup"><span data-stu-id="80ee4-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="80ee4-108">Se você já o tiver instalado, clique em **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="80ee4-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="80ee4-109">Em seguida, você verá uma lista de cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="80ee4-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="80ee4-110">Selecione **ASP.net e desenvolvimento** para a Web, F# que instalará o suporte e o suporte do .net Core para projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="80ee4-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="80ee4-111">Em seguida, clique em **Modificar** no lado inferior direito.</span><span class="sxs-lookup"><span data-stu-id="80ee4-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="80ee4-112">Isso instalará tudo o que você selecionou.</span><span class="sxs-lookup"><span data-stu-id="80ee4-112">This will install everything you have selected.</span></span> <span data-ttu-id="80ee4-113">Em seguida, você pode abrir o Visual F# Studio 2017 com suporte a idiomas clicando em **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="80ee4-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="80ee4-114">Instalar F# com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="80ee4-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="80ee4-115">F#é instalado por padrão no [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), não importa qual configuração você escolher.</span><span class="sxs-lookup"><span data-stu-id="80ee4-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="80ee4-116">Após a conclusão da instalação, escolha "iniciar o Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="80ee4-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="80ee4-117">Você também pode iniciá-lo por meio do Finder no macOS.</span><span class="sxs-lookup"><span data-stu-id="80ee4-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="80ee4-118">Instalar F# com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="80ee4-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="80ee4-119">Você deve ter o [git instalado](https://git-scm.com/download) e disponível em seu caminho para fazer uso de modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="80ee4-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="80ee4-120">Você pode verificar se ele está instalado corretamente digitando `git --version` em um prompt de comando e pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="80ee4-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="80ee4-121">macOS</span><span class="sxs-lookup"><span data-stu-id="80ee4-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="80ee4-122">O [mono](https://www.mono-project.com) é usado [ F# ](../tutorials/fsharp-interactive/index.md) para suporte interativo.</span><span class="sxs-lookup"><span data-stu-id="80ee4-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="80ee4-123">A maneira mais fácil de instalar o mono no macOS é via homebrew.</span><span class="sxs-lookup"><span data-stu-id="80ee4-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="80ee4-124">Basta digitar o seguinte em seu terminal:</span><span class="sxs-lookup"><span data-stu-id="80ee4-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="80ee4-125">Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="80ee4-125">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="80ee4-126">Linux</span><span class="sxs-lookup"><span data-stu-id="80ee4-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="80ee4-127">O [mono](https://www.mono-project.com) é usado [ F# ](../tutorials/fsharp-interactive/index.md) para suporte interativo.</span><span class="sxs-lookup"><span data-stu-id="80ee4-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="80ee4-128">Se você estiver no Debian ou Ubuntu, poderá usar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="80ee4-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="80ee4-129">Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="80ee4-129">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="80ee4-130">Windows</span><span class="sxs-lookup"><span data-stu-id="80ee4-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="80ee4-131">Instale o [Visual Studio F# com suporte](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="80ee4-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="80ee4-132">Isso instala todos os componentes necessários para gravar, compilar e executar F# código.</span><span class="sxs-lookup"><span data-stu-id="80ee4-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="80ee4-133">Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="80ee4-133">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

---

<span data-ttu-id="80ee4-134">Em seguida, será necessário [Visual Studio Code](https://code.visualstudio.com) instalado.</span><span class="sxs-lookup"><span data-stu-id="80ee4-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="80ee4-135">Em seguida, clique no ícone extensões e procure "Ionide":</span><span class="sxs-lookup"><span data-stu-id="80ee4-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="80ee4-136">O único plug-in F# necessário para o suporte no Visual Studio Code é [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="80ee4-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="80ee4-137">No entanto, você também pode instalar [Ionide-falsificação](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter suporte [falso](https://fsharp.github.io/FAKE/) e [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter suporte a [paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="80ee4-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="80ee4-138">A FALSIFICAção e a F# paket são ferramentas de comunidade adicionais para a criação de projetos e o gerenciamento de dependências, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="80ee4-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="80ee4-139">Instalar F# em um servidor de compilação</span><span class="sxs-lookup"><span data-stu-id="80ee4-139">Install F# on a Build Server</span></span>

<span data-ttu-id="80ee4-140">Se você estiver usando o .NET Core ou .NET Framework por meio do SDK do .NET, bastará instalar o SDK do .NET em seu servidor de compilação.</span><span class="sxs-lookup"><span data-stu-id="80ee4-140">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="80ee4-141">Ele tem tudo o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="80ee4-141">It has everything you need.</span></span>

<span data-ttu-id="80ee4-142">Se você estiver usando .NET Framework e **não** estiver usando o SDK do .net, será necessário instalar o [ferramentas de Build do Visual Studio SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="80ee4-142">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="80ee4-143">No instalador, selecione **ferramentas de Build da área de trabalho do .net** e, em seguida, selecione o **F#** componente do compilador no lado direito do menu do instalador.</span><span class="sxs-lookup"><span data-stu-id="80ee4-143">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
