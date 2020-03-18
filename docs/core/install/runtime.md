---
title: Instale o tempo de execução do .NET Core no Windows, Linux e macOS - .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399010"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="0780b-104">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0780b-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="0780b-105">Neste artigo, você aprenderá como baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="0780b-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="0780b-107">Instale com um instalador</span><span class="sxs-lookup"><span data-stu-id="0780b-107">Install with an installer</span></span>

<span data-ttu-id="0780b-108">O Windows tem instaladores autônomos que podem ser usados para instalar o tempo de execução do .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="0780b-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="0780b-109">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="0780b-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="0780b-110">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="0780b-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="0780b-111">Instale com um instalador</span><span class="sxs-lookup"><span data-stu-id="0780b-111">Install with an installer</span></span>

<span data-ttu-id="0780b-112">O macOS possui instaladores autônomos que podem ser usados para instalar o tempo de execução do .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="0780b-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="0780b-113">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="0780b-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="0780b-114">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="0780b-114">Download and manually install</span></span>

<span data-ttu-id="0780b-115">Como uma alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0780b-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="0780b-116">Para instalar o tempo de execução e ativar os comandos .NET Core CLI disponíveis no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="0780b-117">Em seguida, abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="0780b-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="0780b-118">Presume-se que o tempo de `~/Downloads/dotnet-runtime.pkg` execução seja baixado para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0780b-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="0780b-119">Instale com um gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="0780b-119">Install with a package manager</span></span>

<span data-ttu-id="0780b-120">Você pode instalar o .NET Core Runtime com muitos dos gerentes de pacotes Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="0780b-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="0780b-121">Para obter mais informações, consulte [O Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="0780b-122">Instalá-lo com um gerenciador de pacotes só é suportado na arquitetura x64.</span><span class="sxs-lookup"><span data-stu-id="0780b-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="0780b-123">Se você estiver instalando o .NET Core Runtime com uma arquitetura diferente, como o ARM, siga as instruções na seção [Download e instale manualmente.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="0780b-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="0780b-124">Para obter mais informações sobre quais arquiteturas são suportadas, consulte [as dependências e os requisitos do .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="0780b-125">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="0780b-125">Download and manually install</span></span>

<span data-ttu-id="0780b-126">Para extrair o tempo de execução e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="0780b-127">Em seguida, abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="0780b-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="0780b-128">Os `export` comandos anteriores só disponibilizam os comandos .NET Core CLI para a sessão de terminal em que foi executado.</span><span class="sxs-lookup"><span data-stu-id="0780b-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="0780b-129">Você pode editar seu perfil shell para adicionar permanentemente os comandos.</span><span class="sxs-lookup"><span data-stu-id="0780b-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="0780b-130">Existem vários shells diferentes disponíveis para Linux e cada um tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="0780b-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="0780b-131">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="0780b-131">For example:</span></span>
>
> - <span data-ttu-id="0780b-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="0780b-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="0780b-133">**Korn Shell**: *~/.kshrc* ou *.profile*</span><span class="sxs-lookup"><span data-stu-id="0780b-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="0780b-134">**Z Shell**: *~/.zshrc* ou *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="0780b-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="0780b-135">Edite o arquivo de origem `:$HOME/dotnet` apropriado para o `PATH` shell e adicione ao final da declaração existente.</span><span class="sxs-lookup"><span data-stu-id="0780b-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="0780b-136">Se `PATH` nenhuma declaração estiver incluída, `export PATH=$PATH:$HOME/dotnet`adicione uma nova linha com .</span><span class="sxs-lookup"><span data-stu-id="0780b-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="0780b-137">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0780b-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="0780b-138">Essa abordagem permite instalar diferentes versões em locais separados e escolher explicitamente qual usar por qual aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0780b-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="0780b-139">Instale com a automação PowerShell</span><span class="sxs-lookup"><span data-stu-id="0780b-139">Install with PowerShell automation</span></span>

<span data-ttu-id="0780b-140">Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0780b-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="0780b-141">Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0780b-142">O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="0780b-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0780b-143">Você pode escolher uma versão `Channel` específica especificando o switch.</span><span class="sxs-lookup"><span data-stu-id="0780b-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="0780b-144">Inclua `Runtime` o interruptor para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0780b-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="0780b-145">Caso contrário, o script instala o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="0780b-146">O comando acima instala o tempo de execução do ASP.NET Core para máxima compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="0780b-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="0780b-147">O tempo de execução do ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="0780b-148">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="0780b-148">Download and manually install</span></span>

<span data-ttu-id="0780b-149">Para extrair o tempo de execução e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="0780b-150">Em seguida, crie um diretório para `%USERPROFILE%\dotnet`instalar, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="0780b-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="0780b-151">Finalmente, extraia o arquivo zip baixado nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="0780b-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="0780b-152">Por padrão, os comandos e aplicativos .NET Core CLI não usarão o .NET Core instalado desta forma.</span><span class="sxs-lookup"><span data-stu-id="0780b-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="0780b-153">Você tem que escolher explicitamente usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0780b-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="0780b-154">Para isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="0780b-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="0780b-155">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="0780b-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="0780b-156">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0780b-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="0780b-157">O padrão é `C:\Program Files\dotnet`tipicamente , que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="0780b-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="0780b-158">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="0780b-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="0780b-159">Instale com automação de bash</span><span class="sxs-lookup"><span data-stu-id="0780b-159">Install with bash automation</span></span>

<span data-ttu-id="0780b-160">Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0780b-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="0780b-161">Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0780b-162">O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="0780b-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0780b-163">Você pode escolher uma versão `current` específica especificando o switch.</span><span class="sxs-lookup"><span data-stu-id="0780b-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="0780b-164">Inclua `runtime` o interruptor para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0780b-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="0780b-165">Caso contrário, o script instala o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="0780b-166">O comando acima instala o tempo de execução do ASP.NET Core para máxima compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="0780b-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="0780b-167">O tempo de execução do ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0780b-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="0780b-168">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0780b-168">All .NET Core downloads</span></span>

<span data-ttu-id="0780b-169">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="0780b-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="0780b-170">.NET Core 3.1 downloads</span><span class="sxs-lookup"><span data-stu-id="0780b-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="0780b-171">.NET Core 2.1 downloads</span><span class="sxs-lookup"><span data-stu-id="0780b-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="0780b-172">Docker</span><span class="sxs-lookup"><span data-stu-id="0780b-172">Docker</span></span>

<span data-ttu-id="0780b-173">Os contêineres fornecem uma maneira leve de isolar sua aplicação do resto do sistema host.</span><span class="sxs-lookup"><span data-stu-id="0780b-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="0780b-174">Os contêineres na mesma máquina compartilham apenas o kernel e usam os recursos dados à sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="0780b-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="0780b-175">O .NET Core pode ser executado em um contêiner Docker.</span><span class="sxs-lookup"><span data-stu-id="0780b-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="0780b-176">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="0780b-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="0780b-177">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="0780b-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="0780b-178">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="0780b-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="0780b-179">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="0780b-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="0780b-180">Para obter mais informações sobre como usar o .NET Core em um contêiner Docker, consulte [Introdução a .NET e Docker](../docker/introduction.md) e [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0780b-181">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0780b-181">Next steps</span></span>

- <span data-ttu-id="0780b-182">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0780b-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
