---
title: Instale o .NET Core SDK no Windows, Linux e macOS - .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399003"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="e69e0-104">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e69e0-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="e69e0-105">Neste artigo, você aprenderá como instalar o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="e69e0-106">O .NET Core SDK é usado para criar aplicativos e bibliotecas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e69e0-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="e69e0-107">O tempo de execução do .NET Core está sempre instalado com o SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="e69e0-108">Instale com um instalador</span><span class="sxs-lookup"><span data-stu-id="e69e0-108">Install with an installer</span></span>

<span data-ttu-id="e69e0-109">O Windows possui instaladores autônomos que podem ser usados para instalar o SDK .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="e69e0-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="e69e0-110">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="e69e0-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="e69e0-111">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="e69e0-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="e69e0-112">Instale com um instalador</span><span class="sxs-lookup"><span data-stu-id="e69e0-112">Install with an installer</span></span>

<span data-ttu-id="e69e0-113">O macOS possui instaladores autônomos que podem ser usados para instalar o SDK .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="e69e0-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="e69e0-114">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="e69e0-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="e69e0-115">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="e69e0-115">Download and manually install</span></span>

<span data-ttu-id="e69e0-116">Como uma alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="e69e0-117">Para extrair o SDK e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e69e0-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e69e0-118">Em seguida, abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="e69e0-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="e69e0-119">Presume-se que o tempo de `~/Downloads/dotnet-sdk.pkg` execução seja baixado para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="e69e0-120">Instale com um gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="e69e0-120">Install with a package manager</span></span>

<span data-ttu-id="e69e0-121">Você pode instalar o .NET Core SDK com muitos dos gerentes de pacotes Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="e69e0-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="e69e0-122">Para obter mais informações, consulte [O Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="e69e0-123">A instalação com um gerenciador de pacotes só é suportada na arquitetura x64.</span><span class="sxs-lookup"><span data-stu-id="e69e0-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="e69e0-124">Se você estiver instalando o .NET Core SDK com uma arquitetura diferente, como o ARM, siga o [Download e instale manualmente](#download-and-manually-install) as instruções abaixo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="e69e0-125">Para obter mais informações sobre quais arquiteturas são suportadas, consulte [as dependências e os requisitos do .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="e69e0-126">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="e69e0-126">Download and manually install</span></span>

<span data-ttu-id="e69e0-127">Para extrair o SDK e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e69e0-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e69e0-128">Em seguida, abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="e69e0-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="e69e0-129">Os `export` comandos anteriores só disponibilizam os comandos .NET Core CLI para a sessão de terminal em que foi executado.</span><span class="sxs-lookup"><span data-stu-id="e69e0-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="e69e0-130">Você pode editar seu perfil shell para adicionar permanentemente os comandos.</span><span class="sxs-lookup"><span data-stu-id="e69e0-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="e69e0-131">Existem vários shells diferentes disponíveis para Linux e cada um tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="e69e0-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="e69e0-132">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e69e0-132">For example:</span></span>
>
> - <span data-ttu-id="e69e0-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="e69e0-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="e69e0-134">**Korn Shell**: *~/.kshrc* ou *.profile*</span><span class="sxs-lookup"><span data-stu-id="e69e0-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="e69e0-135">**Z Shell**: *~/.zshrc* ou *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="e69e0-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="e69e0-136">Edite o arquivo de origem `:$HOME/dotnet` apropriado para o `PATH` shell e adicione ao final da declaração existente.</span><span class="sxs-lookup"><span data-stu-id="e69e0-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="e69e0-137">Se `PATH` nenhuma declaração estiver incluída, `export PATH=$PATH:$HOME/dotnet`adicione uma nova linha com .</span><span class="sxs-lookup"><span data-stu-id="e69e0-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="e69e0-138">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="e69e0-139">Instale com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e69e0-139">Install with Visual Studio</span></span>

<span data-ttu-id="e69e0-140">Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão target .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="e69e0-141">Versão .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e69e0-141">.NET Core SDK version</span></span> | <span data-ttu-id="e69e0-142">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e69e0-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="e69e0-143">3.1</span><span class="sxs-lookup"><span data-stu-id="e69e0-143">3.1</span></span>                   | <span data-ttu-id="e69e0-144">Visual Studio 2019 versão 16.4 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e69e0-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="e69e0-145">3.0</span><span class="sxs-lookup"><span data-stu-id="e69e0-145">3.0</span></span>                   | <span data-ttu-id="e69e0-146">Visual Studio 2019 versão 16.3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e69e0-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="e69e0-147">2.2</span><span class="sxs-lookup"><span data-stu-id="e69e0-147">2.2</span></span>                   | <span data-ttu-id="e69e0-148">Visual Studio 2017 versão 15.9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e69e0-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="e69e0-149">2.1</span><span class="sxs-lookup"><span data-stu-id="e69e0-149">2.1</span></span>                   | <span data-ttu-id="e69e0-150">Visual Studio 2017 versão 15.7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e69e0-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="e69e0-151">Se você já tiver o Visual Studio instalado, você pode verificar sua versão com as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="e69e0-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="e69e0-152">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e69e0-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="e69e0-153">Selecione **ajuda** > **sobre o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e69e0-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="e69e0-154">Leia o número da versão da caixa de diálogo **Sobre.**</span><span class="sxs-lookup"><span data-stu-id="e69e0-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="e69e0-155">O Visual Studio pode instalar o SDK do Núcleo .NET mais recente e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e69e0-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="e69e0-156">[Baixe Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="e69e0-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="e69e0-157">Selecione uma carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="e69e0-157">Select a workload</span></span>

<span data-ttu-id="e69e0-158">Ao instalar ou modificar o Visual Studio, selecione uma ou mais das seguintes cargas de trabalho, dependendo do tipo de aplicativo que você está construindo:</span><span class="sxs-lookup"><span data-stu-id="e69e0-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="e69e0-159">A carga de trabalho **de desenvolvimento multiplataforma .NET Core** na seção Outros **conjuntos de ferramentas.**</span><span class="sxs-lookup"><span data-stu-id="e69e0-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="e69e0-160">A **carga de trabalho de desenvolvimento ASP.NET e web** na seção Nuvem de & **Web.**</span><span class="sxs-lookup"><span data-stu-id="e69e0-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="e69e0-161">A carga de trabalho de desenvolvimento do **Azure** na seção **Nuvem de & da Web.**</span><span class="sxs-lookup"><span data-stu-id="e69e0-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="e69e0-162">A carga de **trabalho de desenvolvimento de desktop .NET** na seção Desktop & **Mobile.**</span><span class="sxs-lookup"><span data-stu-id="e69e0-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="e69e0-163">[![Windows Visual Studio 2019 com carga de trabalho .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="e69e0-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="e69e0-164">Baixe e instale manualmente</span><span class="sxs-lookup"><span data-stu-id="e69e0-164">Download and manually install</span></span>

<span data-ttu-id="e69e0-165">Para extrair o tempo de execução e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e69e0-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e69e0-166">Em seguida, crie um diretório para `%USERPROFILE%\dotnet`instalar, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="e69e0-167">Finalmente, extraia o arquivo zip baixado nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="e69e0-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="e69e0-168">Por padrão, os comandos e aplicativos .NET Core CLI não usarão o .NET Core instalado desta forma.</span><span class="sxs-lookup"><span data-stu-id="e69e0-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="e69e0-169">Você tem que escolher explicitamente usá-lo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="e69e0-170">Para isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="e69e0-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="e69e0-171">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="e69e0-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="e69e0-172">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e69e0-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="e69e0-173">O padrão é `C:\Program Files\dotnet`tipicamente , que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="e69e0-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="e69e0-174">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="e69e0-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="e69e0-175">Instale com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="e69e0-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="e69e0-176">O Visual Studio for Mac instala o .NET Core SDK quando a carga de trabalho **.NET Core** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="e69e0-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="e69e0-177">Para começar com o desenvolvimento do .NET Core no macOS, consulte [Install Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="e69e0-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="e69e0-178">Para a versão mais recente, .NET Core 3.1, você deve usar o Visual Studio para Visualização Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="e69e0-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="e69e0-179">[![macOS Visual Studio 2019 para Mac com o recurso de carga de trabalho .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="e69e0-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="e69e0-180">Instale ao lado do Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e69e0-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="e69e0-181">Visual Studio Code é um poderoso e leve editor de código-fonte que é executado na sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e69e0-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="e69e0-182">Visual Studio Code está disponível para Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="e69e0-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="e69e0-183">Enquanto o Visual Studio Code não vem com um instalador automatizado .NET Core como o Visual Studio faz, adicionar suporte ao .NET Core é simples.</span><span class="sxs-lookup"><span data-stu-id="e69e0-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="e69e0-184">[Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="e69e0-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="e69e0-185">[Baixe e instale o .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="e69e0-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="e69e0-186">[Instale a extensão C# do mercado Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="e69e0-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="e69e0-187">Instale com a automação PowerShell</span><span class="sxs-lookup"><span data-stu-id="e69e0-187">Install with PowerShell automation</span></span>

<span data-ttu-id="e69e0-188">Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="e69e0-189">Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e69e0-190">O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e69e0-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e69e0-191">Para instalar a versão atual do .NET Core, execute o script com o seguinte switch.</span><span class="sxs-lookup"><span data-stu-id="e69e0-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="e69e0-192">Instale com automação de bash</span><span class="sxs-lookup"><span data-stu-id="e69e0-192">Install with bash automation</span></span>

<span data-ttu-id="e69e0-193">Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do SDK.</span><span class="sxs-lookup"><span data-stu-id="e69e0-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="e69e0-194">Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e69e0-195">O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e69e0-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e69e0-196">Para instalar a versão atual do .NET Core, execute o script com o seguinte switch.</span><span class="sxs-lookup"><span data-stu-id="e69e0-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="e69e0-197">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e69e0-197">All .NET Core downloads</span></span>

<span data-ttu-id="e69e0-198">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="e69e0-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="e69e0-199">.NET Core 3.1 downloads</span><span class="sxs-lookup"><span data-stu-id="e69e0-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="e69e0-200">.NET Core 3.0 downloads</span><span class="sxs-lookup"><span data-stu-id="e69e0-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="e69e0-201">.NET Core 2.2 downloads</span><span class="sxs-lookup"><span data-stu-id="e69e0-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="e69e0-202">.NET Core 2.1 downloads</span><span class="sxs-lookup"><span data-stu-id="e69e0-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="e69e0-203">Docker</span><span class="sxs-lookup"><span data-stu-id="e69e0-203">Docker</span></span>

<span data-ttu-id="e69e0-204">Os contêineres fornecem uma maneira leve de isolar sua aplicação do resto do sistema host.</span><span class="sxs-lookup"><span data-stu-id="e69e0-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="e69e0-205">Os contêineres na mesma máquina compartilham apenas o kernel e usam os recursos dados à sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="e69e0-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="e69e0-206">O .NET Core pode ser executado em um contêiner Docker.</span><span class="sxs-lookup"><span data-stu-id="e69e0-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="e69e0-207">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="e69e0-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="e69e0-208">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="e69e0-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="e69e0-209">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="e69e0-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="e69e0-210">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="e69e0-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="e69e0-211">Para obter mais informações sobre como usar o .NET Core em um contêiner Docker, consulte [Introdução a .NET e Docker](../docker/introduction.md) e [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e69e0-212">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e69e0-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="e69e0-213">[Tutorial: Tutorial do Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="e69e0-214">[Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e69e0-215">[Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="e69e0-216">[Trabalhando com nota notatrização macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="e69e0-217">[Tutorial: Comece no macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="e69e0-218">[Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e69e0-219">[Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="e69e0-220">[Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e69e0-221">[Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="e69e0-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
