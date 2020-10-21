---
title: Instalar o F#
description: 'Saiba como instalar o F # de várias maneiras diferentes.'
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224289"
---
# <a name="install-f"></a><span data-ttu-id="742ae-103">Instalar o F\#</span><span class="sxs-lookup"><span data-stu-id="742ae-103">Install F\#</span></span>

<span data-ttu-id="742ae-104">Você pode instalar o F # de várias maneiras, dependendo do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="742ae-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="742ae-105">Instalar o F # com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="742ae-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="742ae-106">Se você estiver baixando o [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pela primeira vez, ele será instalado primeiro instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="742ae-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="742ae-107">Instale a edição apropriada do Visual Studio por meio do instalador.</span><span class="sxs-lookup"><span data-stu-id="742ae-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="742ae-108">Se você já tiver o Visual Studio instalado, escolha **Modificar** ao lado da edição à qual você deseja adicionar o F #.</span><span class="sxs-lookup"><span data-stu-id="742ae-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="742ae-109">Na página cargas de trabalho, selecione o **ASP.net e** a carga de trabalho de desenvolvimento Web, que inclui o suporte a F # e .NET Core para projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="742ae-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="742ae-110">Escolha **Modificar** no canto inferior direito para instalar tudo o que você selecionou.</span><span class="sxs-lookup"><span data-stu-id="742ae-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="742ae-111">Em seguida, você pode abrir o Visual Studio com o F # escolhendo **Iniciar** no instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="742ae-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="742ae-112">Instalar F # com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="742ae-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="742ae-113">Verifique se você tem o [git](https://git-scm.com/download) instalado e disponível no seu caminho.</span><span class="sxs-lookup"><span data-stu-id="742ae-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="742ae-114">Você pode verificar se ele está instalado corretamente digitando `git --version` em um prompt de comando e pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="742ae-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="742ae-115">Instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) e [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="742ae-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="742ae-116">Selecione o ícone extensões e procure "Ionide":</span><span class="sxs-lookup"><span data-stu-id="742ae-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="742ae-117">O único plug-in necessário para o suporte a F # no Visual Studio Code é [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="742ae-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="742ae-118">No entanto, você também pode instalar [Ionide-falsificação](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter suporte [falso](https://fake.build/) e [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter suporte a [paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="742ae-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="742ae-119">A FALSIFICAção e a paket são ferramentas de comunidade F # adicionais para a criação de projetos e o gerenciamento de dependências, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="742ae-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="742ae-120">Instalar F # com Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="742ae-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="742ae-121">O F # é instalado por padrão no [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), não importa qual configuração você escolher.</span><span class="sxs-lookup"><span data-stu-id="742ae-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="742ae-122">Após a conclusão da instalação, escolha **iniciar o Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="742ae-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="742ae-123">Você também pode abrir o Visual Studio por meio do Finder no macOS.</span><span class="sxs-lookup"><span data-stu-id="742ae-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="742ae-124">Instalar o F # em um servidor de compilação</span><span class="sxs-lookup"><span data-stu-id="742ae-124">Install F# on a build server</span></span>

<span data-ttu-id="742ae-125">Se você estiver usando o .NET Core ou .NET Framework por meio do SDK do .NET, bastará instalar o SDK do .NET em seu servidor de compilação.</span><span class="sxs-lookup"><span data-stu-id="742ae-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="742ae-126">Ele tem tudo o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="742ae-126">It has everything you need.</span></span>

<span data-ttu-id="742ae-127">Se você estiver usando .NET Framework e **não** estiver usando o SDK do .net, precisará instalar o [ferramentas de Build do Visual Studio SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="742ae-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="742ae-128">No instalador, selecione **ferramentas de Build do .net desktop**e, em seguida, selecione o componente do **compilador F #** no lado direito do menu do instalador.</span><span class="sxs-lookup"><span data-stu-id="742ae-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
