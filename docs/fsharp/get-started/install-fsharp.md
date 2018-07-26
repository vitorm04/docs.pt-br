---
title: 'Instalar o F #'
description: 'Saiba como instalar o F # com base em seu ambiente.'
ms.date: 07/03/2018
ms.openlocfilehash: 142265a95e1d3ee1603a89f650a24c6a45709181
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37878838"
---
# <a name="install-f"></a><span data-ttu-id="60535-103">Instalar o F #</span><span class="sxs-lookup"><span data-stu-id="60535-103">Install F#</span></span> #

<span data-ttu-id="60535-104">Você pode instalar F # de várias maneiras, dependendo do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="60535-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="60535-105">Instalar o F # com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60535-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="60535-106">Se você estiver baixando [Visual Studio](https://visualstudio.microsoft.com/) pela primeira vez, ele instalará primeiro o instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60535-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="60535-107">Instale o SKU apropriada do Visual Studio do instalador.</span><span class="sxs-lookup"><span data-stu-id="60535-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="60535-108">Se você já tiver instalado, clique em **modificar**.</span><span class="sxs-lookup"><span data-stu-id="60535-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="60535-109">Em seguida, você verá uma lista de cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="60535-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="60535-110">Selecione **ASP.NET e desenvolvimento web**, que instalará o suporte do F #, suporte ao .NET Core, e projetos do F # suporte para o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="60535-110">Select **ASP.NET and web development**, which will install F# support, .NET Core support, and F# support for ASP.NET Core projects.</span></span>

<span data-ttu-id="60535-111">Em seguida, clique em **modificar** no lado direito inferior.</span><span class="sxs-lookup"><span data-stu-id="60535-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="60535-112">Isso irá instalar tudo o que você selecionou.</span><span class="sxs-lookup"><span data-stu-id="60535-112">This will install everything you have selected.</span></span> <span data-ttu-id="60535-113">Em seguida, você pode abrir o Visual Studio 2017 com o suporte à linguagem F # clicando **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="60535-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="60535-114">Instalar o F # com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="60535-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="60535-115">F # é instalado por padrão em [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/), não importa qual configuração você escolher.</span><span class="sxs-lookup"><span data-stu-id="60535-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter what configuration you choose.</span></span>

<span data-ttu-id="60535-116">Depois de concluir a instalação, escolha "Iniciar o Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="60535-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="60535-117">Você também pode iniciá-lo por meio do localizador no macOS.</span><span class="sxs-lookup"><span data-stu-id="60535-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="60535-118">Instalar F # com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="60535-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="60535-119">Você deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso de modelos de projeto no Ionide.</span><span class="sxs-lookup"><span data-stu-id="60535-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="60535-120">Você pode verificar se ele está instalado corretamente, digitando `git --version` em um prompt de comando e pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="60535-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="60535-121">macOS</span><span class="sxs-lookup"><span data-stu-id="60535-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="60535-122">Usa Ionide [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="60535-122">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="60535-123">A maneira mais fácil de instalar o Mono no macOS é por meio do Homebrew.</span><span class="sxs-lookup"><span data-stu-id="60535-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="60535-124">Simplesmente digite o seguinte no seu terminal:</span><span class="sxs-lookup"><span data-stu-id="60535-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="60535-125">Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="60535-125">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="60535-126">Linux</span><span class="sxs-lookup"><span data-stu-id="60535-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="60535-127">No Linux, Ionide também utiliza [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="60535-127">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="60535-128">Se você estiver no Debian ou Ubuntu, você pode usar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="60535-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="60535-129">Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="60535-129">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="60535-130">Windows</span><span class="sxs-lookup"><span data-stu-id="60535-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="60535-131">Se você estiver no Windows, você deve [instalar o Visual Studio com suporte do F #](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="60535-131">If you're on Windows, you must [install Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="60535-132">Isso instala todos os componentes necessários para escrever, compilar e executar código F #.</span><span class="sxs-lookup"><span data-stu-id="60535-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="60535-133">Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="60535-133">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="60535-134">Em seguida, será necessário [Visual Studio Code](https://code.visualstudio.com) instalado.</span><span class="sxs-lookup"><span data-stu-id="60535-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="60535-135">Em seguida, clique no ícone de extensões e a pesquisa para "Ionide":</span><span class="sxs-lookup"><span data-stu-id="60535-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="60535-136">O único plug-in necessário para suporte a F # no Visual Studio Code é [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="60535-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="60535-137">No entanto, você também pode instalar [FALSIFICAÇÃO Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter [FORJAR](https://fsharp.github.io/FAKE/) dão suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) obter [Paket](https://fsprojects.github.io/Paket/) dão suporte.</span><span class="sxs-lookup"><span data-stu-id="60535-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="60535-138">FALSOS e Paket são adicionais Ferramentas de comunidade F # para projetos de criação e gerenciamento de dependências, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60535-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>