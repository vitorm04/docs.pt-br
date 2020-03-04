---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a41bbdf5419585f06773583dbe82ab0d84ebaa4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157630"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="451fa-104">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="451fa-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="451fa-105">Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="451fa-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="451fa-107">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="451fa-107">Install with an installer</span></span>

<span data-ttu-id="451fa-108">O Windows tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="451fa-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="451fa-109">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="451fa-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="451fa-110">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="451fa-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="451fa-111">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="451fa-111">Install with an installer</span></span>

<span data-ttu-id="451fa-112">o macOS tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="451fa-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="451fa-113">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="451fa-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="451fa-114">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="451fa-114">Download and manually install</span></span>

<span data-ttu-id="451fa-115">Como alternativa para os instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="451fa-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="451fa-116">Para instalar o tempo de execução e habilitar os comandos de CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="451fa-117">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="451fa-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="451fa-118">Supõe-se que o tempo de execução seja baixado para o arquivo de `~/Downloads/dotnet-runtime.pkg`.</span><span class="sxs-lookup"><span data-stu-id="451fa-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="451fa-119">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="451fa-119">Install with a package manager</span></span>

<span data-ttu-id="451fa-120">Você pode instalar o tempo de execução do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="451fa-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="451fa-121">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="451fa-122">A instalação com um Gerenciador de pacotes só tem suporte na arquitetura x64.</span><span class="sxs-lookup"><span data-stu-id="451fa-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="451fa-123">Se você estiver instalando o tempo de execução do .NET Core com uma arquitetura diferente, como o ARM, siga as instruções na seção [baixar e instalar manualmente](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="451fa-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="451fa-124">Para obter mais informações sobre quais arquiteturas têm suporte, consulte [dependências e requisitos do .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="451fa-125">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="451fa-125">Download and manually install</span></span>

<span data-ttu-id="451fa-126">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="451fa-127">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="451fa-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="451fa-128">Os comandos de `export` anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="451fa-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="451fa-129">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="451fa-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="451fa-130">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="451fa-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="451fa-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="451fa-131">For example:</span></span>
>
> - <span data-ttu-id="451fa-132">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="451fa-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="451fa-133">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="451fa-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="451fa-134">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="451fa-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="451fa-135">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da instrução `PATH` existente.</span><span class="sxs-lookup"><span data-stu-id="451fa-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="451fa-136">Se nenhuma instrução de `PATH` for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="451fa-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="451fa-137">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="451fa-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="451fa-138">Essa abordagem permite que você instale versões diferentes em locais separados e escolha explicitamente qual deles usar por qual aplicativo.</span><span class="sxs-lookup"><span data-stu-id="451fa-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="451fa-139">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="451fa-139">Install with PowerShell automation</span></span>

<span data-ttu-id="451fa-140">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="451fa-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="451fa-141">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="451fa-142">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="451fa-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="451fa-143">Você pode escolher uma versão específica especificando a opção `Channel`.</span><span class="sxs-lookup"><span data-stu-id="451fa-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="451fa-144">Inclua a opção `Runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="451fa-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="451fa-145">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="451fa-146">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="451fa-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="451fa-147">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="451fa-148">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="451fa-148">Download and manually install</span></span>

<span data-ttu-id="451fa-149">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="451fa-150">Em seguida, crie um diretório para instalar, por exemplo `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="451fa-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="451fa-151">Por fim, extraia o arquivo zip baixado para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="451fa-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="451fa-152">Por padrão, CLI do .NET Core comandos e aplicativos não usarão o .NET Core instalado dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="451fa-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="451fa-153">Você precisa optar por usá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="451fa-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="451fa-154">Para fazer isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="451fa-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="451fa-155">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="451fa-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="451fa-156">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="451fa-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="451fa-157">Normalmente, o padrão é `C:\Program Files\dotnet`, que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="451fa-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="451fa-158">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="451fa-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="451fa-159">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="451fa-159">Install with bash automation</span></span>

<span data-ttu-id="451fa-160">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="451fa-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="451fa-161">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="451fa-162">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="451fa-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="451fa-163">Você pode escolher uma versão específica especificando a opção `current`.</span><span class="sxs-lookup"><span data-stu-id="451fa-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="451fa-164">Inclua a opção `runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="451fa-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="451fa-165">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="451fa-166">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="451fa-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="451fa-167">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="451fa-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="451fa-168">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="451fa-168">All .NET Core downloads</span></span>

<span data-ttu-id="451fa-169">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="451fa-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="451fa-170">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="451fa-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="451fa-171">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="451fa-171">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="451fa-172">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="451fa-172">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="451fa-173">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="451fa-173">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="451fa-174">Docker</span><span class="sxs-lookup"><span data-stu-id="451fa-174">Docker</span></span>

<span data-ttu-id="451fa-175">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="451fa-175">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="451fa-176">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="451fa-176">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="451fa-177">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="451fa-177">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="451fa-178">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="451fa-178">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="451fa-179">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="451fa-179">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="451fa-180">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="451fa-180">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="451fa-181">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="451fa-181">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="451fa-182">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-182">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="451fa-183">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="451fa-183">Next steps</span></span>

- <span data-ttu-id="451fa-184">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="451fa-184">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
