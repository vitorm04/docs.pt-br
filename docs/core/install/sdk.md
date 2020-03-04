---
title: Instalar o SDK do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 0aa323533dd9136372c2bbc330c9c3056fdf428c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157565"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="9b0e1-104">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b0e1-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="9b0e1-105">Neste artigo, você aprenderá a instalar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="9b0e1-106">O SDK do .NET Core é usado para criar aplicativos e bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="9b0e1-107">O tempo de execução do .NET Core é sempre instalado com o SDK.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="9b0e1-108">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="9b0e1-108">Install with an installer</span></span>

<span data-ttu-id="9b0e1-109">O Windows tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9b0e1-110">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9b0e1-111">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="9b0e1-112">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="9b0e1-112">Install with an installer</span></span>

<span data-ttu-id="9b0e1-113">o macOS tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9b0e1-114">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="9b0e1-115">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="9b0e1-115">Download and manually install</span></span>

<span data-ttu-id="9b0e1-116">Como alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o SDK.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="9b0e1-117">Para extrair o SDK e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9b0e1-118">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="9b0e1-119">Supõe-se que o tempo de execução seja baixado para o arquivo de `~/Downloads/dotnet-sdk.pkg`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="9b0e1-120">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="9b0e1-120">Install with a package manager</span></span>

<span data-ttu-id="9b0e1-121">Você pode instalar o SDK do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="9b0e1-122">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="9b0e1-123">A instalação com um Gerenciador de pacotes só tem suporte na arquitetura x64.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="9b0e1-124">Se você estiver instalando o SDK do .NET Core com uma arquitetura diferente, como o ARM, siga as instruções de [download e instale manualmente](#download-and-manually-install) abaixo.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="9b0e1-125">Para obter mais informações sobre quais arquiteturas têm suporte, consulte [dependências e requisitos do .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9b0e1-126">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="9b0e1-126">Download and manually install</span></span>

<span data-ttu-id="9b0e1-127">Para extrair o SDK e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9b0e1-128">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9b0e1-129">Os comandos de `export` anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9b0e1-130">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9b0e1-131">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9b0e1-132">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-132">For example:</span></span>
>
> - <span data-ttu-id="9b0e1-133">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="9b0e1-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9b0e1-134">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="9b0e1-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9b0e1-135">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="9b0e1-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="9b0e1-136">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da instrução `PATH` existente.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9b0e1-137">Se nenhuma instrução de `PATH` for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9b0e1-138">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="9b0e1-139">Instalar com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b0e1-139">Install with Visual Studio</span></span>

<span data-ttu-id="9b0e1-140">Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão de SDK do .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="9b0e1-141">Versão do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b0e1-141">.NET Core SDK version</span></span> | <span data-ttu-id="9b0e1-142">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b0e1-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9b0e1-143">3.1</span><span class="sxs-lookup"><span data-stu-id="9b0e1-143">3.1</span></span>                   | <span data-ttu-id="9b0e1-144">Visual Studio 2019 versão 16,4 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9b0e1-145">3.0</span><span class="sxs-lookup"><span data-stu-id="9b0e1-145">3.0</span></span>                   | <span data-ttu-id="9b0e1-146">Visual Studio 2019 versão 16,3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9b0e1-147">2.2</span><span class="sxs-lookup"><span data-stu-id="9b0e1-147">2.2</span></span>                   | <span data-ttu-id="9b0e1-148">Visual Studio 2017 versão 15,9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9b0e1-149">2.1</span><span class="sxs-lookup"><span data-stu-id="9b0e1-149">2.1</span></span>                   | <span data-ttu-id="9b0e1-150">Visual Studio 2017 versão 15,7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9b0e1-151">Se você já tiver o Visual Studio instalado, poderá verificar sua versão com as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9b0e1-152">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="9b0e1-153">Selecione **ajuda** > **sobre Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9b0e1-154">Leia o número de versão na caixa de diálogo **sobre** .</span><span class="sxs-lookup"><span data-stu-id="9b0e1-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9b0e1-155">O Visual Studio pode instalar o SDK do .NET Core e o tempo de execução mais recentes.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="9b0e1-156">[Baixar o Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9b0e1-157">Selecionar uma carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="9b0e1-157">Select a workload</span></span>

<span data-ttu-id="9b0e1-158">Ao instalar ou modificar o Visual Studio, selecione uma ou mais das cargas de trabalho a seguir, dependendo do tipo de aplicativo que você está criando:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9b0e1-159">A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .</span><span class="sxs-lookup"><span data-stu-id="9b0e1-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9b0e1-160">A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="9b0e1-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9b0e1-161">A carga de trabalho de **desenvolvimento do Azure** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="9b0e1-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9b0e1-162">A carga de trabalho **.net desktop Development** na seção **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="9b0e1-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9b0e1-163">[![o Windows Visual Studio 2019 com carga de trabalho do .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9b0e1-164">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="9b0e1-164">Download and manually install</span></span>

<span data-ttu-id="9b0e1-165">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9b0e1-166">Em seguida, crie um diretório para instalar, por exemplo `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="9b0e1-167">Por fim, extraia o arquivo zip baixado para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="9b0e1-168">Por padrão, CLI do .NET Core comandos e aplicativos não usarão o .NET Core instalado dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="9b0e1-169">Você precisa optar por usá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="9b0e1-170">Para fazer isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="9b0e1-171">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="9b0e1-172">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="9b0e1-173">Normalmente, o padrão é `C:\Program Files\dotnet`, que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="9b0e1-174">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="9b0e1-175">Instalar com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="9b0e1-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="9b0e1-176">Visual Studio para Mac instala o SDK do .NET Core quando a carga de trabalho do **.NET Core** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="9b0e1-177">Para começar a usar o desenvolvimento do .NET Core no macOS, consulte [instalar o Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="9b0e1-178">Para a versão mais recente, o .NET Core 3,1, você deve usar a visualização Visual Studio para Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="9b0e1-179">[![macOS Visual Studio 2019 para Mac com o recurso de carga de trabalho do .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9b0e1-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9b0e1-180">Instalar junto com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9b0e1-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9b0e1-181">Visual Studio Code é um editor de código-fonte leve e avançado que é executado em sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9b0e1-182">Visual Studio Code está disponível para Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9b0e1-183">Embora Visual Studio Code não venha com um instalador .NET Core automatizado como o Visual Studio, adicionar o suporte ao .NET Core é simples.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9b0e1-184">[Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9b0e1-185">[Baixe e instale o SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9b0e1-186">[Instale a C# extensão do Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9b0e1-187">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b0e1-187">Install with PowerShell automation</span></span>

<span data-ttu-id="9b0e1-188">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9b0e1-189">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9b0e1-190">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9b0e1-191">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="9b0e1-192">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="9b0e1-192">Install with bash automation</span></span>

<span data-ttu-id="9b0e1-193">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9b0e1-194">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9b0e1-195">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9b0e1-196">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="9b0e1-197">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b0e1-197">All .NET Core downloads</span></span>

<span data-ttu-id="9b0e1-198">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="9b0e1-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="9b0e1-199">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9b0e1-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9b0e1-200">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="9b0e1-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="9b0e1-201">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="9b0e1-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="9b0e1-202">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9b0e1-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="9b0e1-203">Docker</span><span class="sxs-lookup"><span data-stu-id="9b0e1-203">Docker</span></span>

<span data-ttu-id="9b0e1-204">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9b0e1-205">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9b0e1-206">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="9b0e1-207">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9b0e1-208">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9b0e1-209">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9b0e1-210">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="9b0e1-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9b0e1-211">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b0e1-212">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9b0e1-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9b0e1-213">[Tutorial: tutorial de Olá, mundo](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9b0e1-214">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b0e1-215">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9b0e1-216">[Trabalhando com o notarization Catalina do MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="9b0e1-217">[Tutorial: introdução ao MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="9b0e1-218">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b0e1-219">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9b0e1-220">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b0e1-221">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e1-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
