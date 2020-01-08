---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340954"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="85d5c-104">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="85d5c-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="85d5c-105">Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85d5c-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="85d5c-106">O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85d5c-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="85d5c-107">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="85d5c-107">Install with an installer</span></span>

<span data-ttu-id="85d5c-108">O Windows tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="85d5c-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="85d5c-109">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="85d5c-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="85d5c-110">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="85d5c-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="85d5c-111">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="85d5c-111">Install with an installer</span></span>

<span data-ttu-id="85d5c-112">o macOS tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:</span><span class="sxs-lookup"><span data-stu-id="85d5c-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="85d5c-113">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="85d5c-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="85d5c-114">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="85d5c-114">Install with a package manager</span></span>

<span data-ttu-id="85d5c-115">Você pode instalar o tempo de execução do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="85d5c-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="85d5c-116">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="85d5c-117">A instalação com um Gerenciador de pacotes só tem suporte na arquitetura x64.</span><span class="sxs-lookup"><span data-stu-id="85d5c-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="85d5c-118">Se você estiver instalando o tempo de execução do .NET Core com uma arquitetura diferente, como o ARM, siga as instruções na seção [baixar e instalar manualmente](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="85d5c-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="85d5c-119">Para obter mais informações sobre quais arquiteturas têm suporte, consulte [dependências e requisitos do .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="85d5c-120">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="85d5c-120">Download and manually install</span></span>

<span data-ttu-id="85d5c-121">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85d5c-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="85d5c-122">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="85d5c-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="85d5c-123">Os comandos de `export` anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="85d5c-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="85d5c-124">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="85d5c-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="85d5c-125">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="85d5c-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="85d5c-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="85d5c-126">For example:</span></span>
>
> - <span data-ttu-id="85d5c-127">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="85d5c-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="85d5c-128">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="85d5c-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="85d5c-129">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="85d5c-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="85d5c-130">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da instrução `PATH` existente.</span><span class="sxs-lookup"><span data-stu-id="85d5c-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="85d5c-131">Se nenhuma instrução de `PATH` for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="85d5c-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="85d5c-132">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="85d5c-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="85d5c-133">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="85d5c-133">Install with PowerShell automation</span></span>

<span data-ttu-id="85d5c-134">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85d5c-134">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="85d5c-135">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-135">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="85d5c-136">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="85d5c-136">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="85d5c-137">Você pode escolher uma versão específica especificando a opção `Channel`.</span><span class="sxs-lookup"><span data-stu-id="85d5c-137">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="85d5c-138">Inclua a opção `Runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85d5c-138">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="85d5c-139">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-139">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="85d5c-140">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="85d5c-140">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="85d5c-141">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85d5c-141">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="85d5c-142">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="85d5c-142">Install with bash automation</span></span>

<span data-ttu-id="85d5c-143">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85d5c-143">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="85d5c-144">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-144">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="85d5c-145">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="85d5c-145">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="85d5c-146">Você pode escolher uma versão específica especificando a opção `current`.</span><span class="sxs-lookup"><span data-stu-id="85d5c-146">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="85d5c-147">Inclua a opção `runtime` para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85d5c-147">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="85d5c-148">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-148">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="85d5c-149">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="85d5c-149">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="85d5c-150">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85d5c-150">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="85d5c-151">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="85d5c-151">All .NET Core downloads</span></span>

<span data-ttu-id="85d5c-152">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="85d5c-152">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="85d5c-153">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="85d5c-153">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="85d5c-154">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="85d5c-154">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="85d5c-155">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="85d5c-155">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="85d5c-156">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="85d5c-156">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="85d5c-157">Docker</span><span class="sxs-lookup"><span data-stu-id="85d5c-157">Docker</span></span>

<span data-ttu-id="85d5c-158">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="85d5c-158">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="85d5c-159">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85d5c-159">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="85d5c-160">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="85d5c-160">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="85d5c-161">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="85d5c-161">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="85d5c-162">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="85d5c-162">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="85d5c-163">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="85d5c-163">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="85d5c-164">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="85d5c-164">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="85d5c-165">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-165">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="85d5c-166">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="85d5c-166">Next steps</span></span>

- <span data-ttu-id="85d5c-167">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="85d5c-167">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
