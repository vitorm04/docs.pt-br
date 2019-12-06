---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835724"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="974e9-104">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="974e9-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="974e9-105">Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="974e9-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="974e9-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="974e9-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="974e9-107">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="974e9-107">Install with an installer</span></span>

<span data-ttu-id="974e9-108">O Windows tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="974e9-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="974e9-109">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="974e9-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="974e9-110">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="974e9-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="974e9-111">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="974e9-111">Install with an installer</span></span>

<span data-ttu-id="974e9-112">o macOS tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="974e9-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="974e9-113">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="974e9-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="974e9-114">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="974e9-114">Install with a package manager</span></span>

<span data-ttu-id="974e9-115">Você pode instalar o tempo de execução do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="974e9-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="974e9-116">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="974e9-117">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="974e9-117">Install with PowerShell automation</span></span>

<span data-ttu-id="974e9-118">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="974e9-118">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="974e9-119">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-119">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="974e9-120">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="974e9-120">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="974e9-121">Você pode escolher uma versão específica especificando a opção `Channel`.</span><span class="sxs-lookup"><span data-stu-id="974e9-121">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="974e9-122">Inclua a opção `Runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="974e9-122">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="974e9-123">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-123">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="974e9-124">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="974e9-124">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="974e9-125">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="974e9-125">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="974e9-126">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="974e9-126">Install with bash automation</span></span>

<span data-ttu-id="974e9-127">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="974e9-127">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="974e9-128">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-128">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="974e9-129">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="974e9-129">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="974e9-130">Você pode escolher uma versão específica especificando a opção `current`.</span><span class="sxs-lookup"><span data-stu-id="974e9-130">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="974e9-131">Inclua a opção `runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="974e9-131">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="974e9-132">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-132">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="974e9-133">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="974e9-133">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="974e9-134">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="974e9-134">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="974e9-135">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="974e9-135">All .NET Core downloads</span></span>

<span data-ttu-id="974e9-136">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="974e9-136">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="974e9-137">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="974e9-137">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="974e9-138">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="974e9-138">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="974e9-139">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="974e9-139">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="974e9-140">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="974e9-140">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="974e9-141">Docker</span><span class="sxs-lookup"><span data-stu-id="974e9-141">Docker</span></span>

<span data-ttu-id="974e9-142">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="974e9-142">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="974e9-143">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="974e9-143">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="974e9-144">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="974e9-144">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="974e9-145">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="974e9-145">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="974e9-146">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="974e9-146">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="974e9-147">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="974e9-147">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="974e9-148">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="974e9-148">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="974e9-149">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-149">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="974e9-150">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="974e9-150">Next steps</span></span>

- <span data-ttu-id="974e9-151">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="974e9-151">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
