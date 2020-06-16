---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768281"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="25dec-104">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="25dec-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="25dec-105">Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="25dec-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="25dec-107">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="25dec-107">Install with an installer</span></span>

<span data-ttu-id="25dec-108">O Windows tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="25dec-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="25dec-109">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="25dec-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="25dec-110">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="25dec-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="25dec-111">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="25dec-111">Install with an installer</span></span>

<span data-ttu-id="25dec-112">o macOS tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="25dec-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="25dec-113">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="25dec-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="25dec-114">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="25dec-114">Download and manually install</span></span>

<span data-ttu-id="25dec-115">Como alternativa para os instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25dec-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="25dec-116">Para instalar o tempo de execução e habilitar os comandos de CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="25dec-117">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="25dec-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="25dec-118">Supõe-se que o tempo de execução seja baixado para o `~/Downloads/dotnet-runtime.pkg` arquivo.</span><span class="sxs-lookup"><span data-stu-id="25dec-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="25dec-119">Instalar no Linux</span><span class="sxs-lookup"><span data-stu-id="25dec-119">Install on Linux</span></span>

<span data-ttu-id="25dec-120">Este artigo será removido em breve.</span><span class="sxs-lookup"><span data-stu-id="25dec-120">This article will be removed soon.</span></span> <span data-ttu-id="25dec-121">Atualmente, ele é substituído por [instalar o .NET Core no Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="25dec-122">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="25dec-122">Install with PowerShell automation</span></span>

<span data-ttu-id="25dec-123">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25dec-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="25dec-124">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="25dec-125">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="25dec-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="25dec-126">Você pode escolher uma versão específica especificando a `Channel` opção.</span><span class="sxs-lookup"><span data-stu-id="25dec-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="25dec-127">Inclua a `Runtime` opção para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25dec-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="25dec-128">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="25dec-129">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="25dec-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="25dec-130">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="25dec-131">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="25dec-131">Download and manually install</span></span>

<span data-ttu-id="25dec-132">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="25dec-133">Em seguida, crie um diretório para instalar, por exemplo `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="25dec-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="25dec-134">Por fim, extraia o arquivo zip baixado para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="25dec-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="25dec-135">Por padrão, CLI do .NET Core comandos e aplicativos não usarão o .NET Core instalado dessa forma e você deverá optar por usá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="25dec-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="25dec-136">Para fazer isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="25dec-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="25dec-137">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="25dec-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="25dec-138">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25dec-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="25dec-139">O padrão é normalmente `C:\Program Files\dotnet` , que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="25dec-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="25dec-140">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="25dec-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="25dec-141">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="25dec-141">Install with bash automation</span></span>

<span data-ttu-id="25dec-142">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25dec-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="25dec-143">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="25dec-144">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="25dec-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="25dec-145">Você pode escolher uma versão específica especificando a `current` opção.</span><span class="sxs-lookup"><span data-stu-id="25dec-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="25dec-146">Inclua a `runtime` opção para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25dec-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="25dec-147">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="25dec-148">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="25dec-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="25dec-149">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25dec-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="25dec-150">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="25dec-150">All .NET Core downloads</span></span>

<span data-ttu-id="25dec-151">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="25dec-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="25dec-152">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="25dec-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="25dec-153">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="25dec-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="25dec-154">Docker</span><span class="sxs-lookup"><span data-stu-id="25dec-154">Docker</span></span>

<span data-ttu-id="25dec-155">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="25dec-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="25dec-156">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25dec-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="25dec-157">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="25dec-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="25dec-158">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="25dec-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="25dec-159">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="25dec-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="25dec-160">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="25dec-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="25dec-161">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="25dec-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="25dec-162">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="25dec-163">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="25dec-163">Next steps</span></span>

- <span data-ttu-id="25dec-164">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="25dec-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
