---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567268"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="e4a9d-104">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4a9d-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="e4a9d-105">Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="e4a9d-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="e4a9d-107">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="e4a9d-107">Install with an installer</span></span>

<span data-ttu-id="e4a9d-108">O Windows e o macOS têm instaladores autônomos que podem ser usados para instalar o tempo de execução do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-108">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="e4a9d-109">[CPUs Windows x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [cpus x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="e4a9d-109">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="e4a9d-110">[CPUs do MacOS x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="e4a9d-110">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="e4a9d-111">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="e4a9d-111">Install with a package manager</span></span>

<span data-ttu-id="e4a9d-112">Você pode instalar o tempo de execução do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-112">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="e4a9d-113">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-113">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="e4a9d-114">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4a9d-114">Install with PowerShell automation</span></span>

<span data-ttu-id="e4a9d-115">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-115">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="e4a9d-116">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-116">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e4a9d-117">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-117">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="e4a9d-118">Para instalar a versão atual do .NET Core (3,0), execute o script com a seguinte opção:</span><span class="sxs-lookup"><span data-stu-id="e4a9d-118">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="e4a9d-119">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="e4a9d-119">Install with bash automation</span></span>

<span data-ttu-id="e4a9d-120">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="e4a9d-121">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e4a9d-122">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="e4a9d-123">Para instalar a versão atual do .NET Core (3,0), execute o script com a seguinte opção:</span><span class="sxs-lookup"><span data-stu-id="e4a9d-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="e4a9d-124">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4a9d-124">All .NET Core downloads</span></span>

<span data-ttu-id="e4a9d-125">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="e4a9d-125">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="e4a9d-126">Downloads da versão prévia do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e4a9d-126">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="e4a9d-127">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="e4a9d-127">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="e4a9d-128">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="e4a9d-128">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="e4a9d-129">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="e4a9d-129">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="e4a9d-130">Docker</span><span class="sxs-lookup"><span data-stu-id="e4a9d-130">Docker</span></span>

<span data-ttu-id="e4a9d-131">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-131">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="e4a9d-132">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-132">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="e4a9d-133">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-133">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="e4a9d-134">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-134">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="e4a9d-135">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-135">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="e4a9d-136">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-136">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="e4a9d-137">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="e4a9d-137">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="e4a9d-138">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-138">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4a9d-139">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4a9d-139">Next steps</span></span>

- <span data-ttu-id="e4a9d-140">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="e4a9d-140">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
