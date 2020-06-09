---
title: Instalar o SDK do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f8e5cc134d4132c83544effa7f1937f2a2c8d012
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596300"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="eedff-104">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="eedff-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="eedff-105">Neste artigo, você aprenderá a instalar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eedff-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="eedff-106">O SDK do .NET Core é usado para criar aplicativos e bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eedff-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="eedff-107">O tempo de execução do .NET Core é sempre instalado com o SDK.</span><span class="sxs-lookup"><span data-stu-id="eedff-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="eedff-108">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="eedff-108">Install with an installer</span></span>

<span data-ttu-id="eedff-109">O Windows tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="eedff-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="eedff-110">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="eedff-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="eedff-111">CPUs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="eedff-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="eedff-112">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="eedff-112">Install with an installer</span></span>

<span data-ttu-id="eedff-113">o macOS tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="eedff-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="eedff-114">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="eedff-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="eedff-115">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="eedff-115">Download and manually install</span></span>

<span data-ttu-id="eedff-116">Como alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o SDK.</span><span class="sxs-lookup"><span data-stu-id="eedff-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="eedff-117">Para extrair o SDK e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eedff-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="eedff-118">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="eedff-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="eedff-119">Supõe-se que o tempo de execução seja baixado para o `~/Downloads/dotnet-sdk.pkg` arquivo.</span><span class="sxs-lookup"><span data-stu-id="eedff-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="eedff-120">Instalar no Linux</span><span class="sxs-lookup"><span data-stu-id="eedff-120">Install on Linux</span></span>

<span data-ttu-id="eedff-121">Este artigo será removido em breve.</span><span class="sxs-lookup"><span data-stu-id="eedff-121">This article will be removed soon.</span></span> <span data-ttu-id="eedff-122">Atualmente, ele é substituído por [instalar o .NET Core no Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="eedff-123">Instalar com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eedff-123">Install with Visual Studio</span></span>

<span data-ttu-id="eedff-124">Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão de SDK do .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="eedff-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="eedff-125">Versão do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="eedff-125">.NET Core SDK version</span></span> | <span data-ttu-id="eedff-126">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eedff-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="eedff-127">3.1</span><span class="sxs-lookup"><span data-stu-id="eedff-127">3.1</span></span>                   | <span data-ttu-id="eedff-128">Visual Studio 2019 versão 16,4 ou superior.</span><span class="sxs-lookup"><span data-stu-id="eedff-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="eedff-129">3.0</span><span class="sxs-lookup"><span data-stu-id="eedff-129">3.0</span></span>                   | <span data-ttu-id="eedff-130">Visual Studio 2019 versão 16,3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="eedff-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="eedff-131">2.2</span><span class="sxs-lookup"><span data-stu-id="eedff-131">2.2</span></span>                   | <span data-ttu-id="eedff-132">Visual Studio 2017 versão 15,9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="eedff-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="eedff-133">2.1</span><span class="sxs-lookup"><span data-stu-id="eedff-133">2.1</span></span>                   | <span data-ttu-id="eedff-134">Visual Studio 2017 versão 15,7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="eedff-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="eedff-135">Se você já tiver o Visual Studio instalado, poderá verificar sua versão com as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="eedff-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="eedff-136">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eedff-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="eedff-137">Selecione **ajuda**  >  **sobre Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="eedff-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="eedff-138">Leia o número de versão na caixa de diálogo **sobre** .</span><span class="sxs-lookup"><span data-stu-id="eedff-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="eedff-139">O Visual Studio pode instalar o SDK do .NET Core e o tempo de execução mais recentes.</span><span class="sxs-lookup"><span data-stu-id="eedff-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="eedff-140">[Baixe o Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="eedff-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="eedff-141">Selecionar uma carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="eedff-141">Select a workload</span></span>

<span data-ttu-id="eedff-142">Ao instalar ou modificar o Visual Studio, selecione uma ou mais das cargas de trabalho a seguir, dependendo do tipo de aplicativo que você está criando:</span><span class="sxs-lookup"><span data-stu-id="eedff-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="eedff-143">A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .</span><span class="sxs-lookup"><span data-stu-id="eedff-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="eedff-144">A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="eedff-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="eedff-145">A carga de trabalho de **desenvolvimento do Azure** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="eedff-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="eedff-146">A carga de trabalho **.net desktop Development** na seção **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="eedff-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="eedff-147">[![Carga de trabalho do Windows Visual Studio 2019 com .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="eedff-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="eedff-148">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="eedff-148">Download and manually install</span></span>

<span data-ttu-id="eedff-149">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eedff-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="eedff-150">Em seguida, crie um diretório para instalar, por exemplo `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="eedff-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="eedff-151">Por fim, extraia o arquivo zip baixado para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="eedff-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="eedff-152">Por padrão, CLI do .NET Core comandos e aplicativos não usarão o .NET Core instalado dessa forma e você deverá optar por usá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="eedff-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="eedff-153">Para fazer isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="eedff-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="eedff-154">Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.</span><span class="sxs-lookup"><span data-stu-id="eedff-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="eedff-155">Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eedff-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="eedff-156">O padrão é normalmente `C:\Program Files\dotnet` , que os instaladores usam.</span><span class="sxs-lookup"><span data-stu-id="eedff-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="eedff-157">Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:</span><span class="sxs-lookup"><span data-stu-id="eedff-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="eedff-158">Instalar com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="eedff-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="eedff-159">Visual Studio para Mac instala o SDK do .NET Core quando a carga de trabalho do **.NET Core** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="eedff-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="eedff-160">Para começar a usar o desenvolvimento do .NET Core no macOS, consulte [instalar o Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="eedff-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="eedff-161">Para a versão mais recente, o .NET Core 3,1, você deve usar a visualização Visual Studio para Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="eedff-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="eedff-162">[![recurso macOS Visual Studio 2019 para Mac com carga de trabalho do .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="eedff-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="eedff-163">Instalar junto com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eedff-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="eedff-164">Visual Studio Code é um editor de código-fonte leve e avançado que é executado em sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eedff-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="eedff-165">Visual Studio Code está disponível para Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="eedff-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="eedff-166">Embora Visual Studio Code não venha com um instalador .NET Core automatizado como o Visual Studio, adicionar o suporte ao .NET Core é simples.</span><span class="sxs-lookup"><span data-stu-id="eedff-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="eedff-167">[Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="eedff-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="eedff-168">[Baixe e instale o SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="eedff-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="eedff-169">[Instale a extensão C# do Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="eedff-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="eedff-170">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="eedff-170">Install with PowerShell automation</span></span>

<span data-ttu-id="eedff-171">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="eedff-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="eedff-172">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="eedff-173">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="eedff-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eedff-174">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="eedff-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="eedff-175">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="eedff-175">Install with bash automation</span></span>

<span data-ttu-id="eedff-176">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="eedff-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="eedff-177">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="eedff-178">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="eedff-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eedff-179">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="eedff-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="eedff-180">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="eedff-180">All .NET Core downloads</span></span>

<span data-ttu-id="eedff-181">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="eedff-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="eedff-182">Downloads do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="eedff-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="eedff-183">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="eedff-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="eedff-184">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="eedff-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="eedff-185">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="eedff-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="eedff-186">Docker</span><span class="sxs-lookup"><span data-stu-id="eedff-186">Docker</span></span>

<span data-ttu-id="eedff-187">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="eedff-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="eedff-188">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eedff-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="eedff-189">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="eedff-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="eedff-190">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="eedff-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="eedff-191">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="eedff-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="eedff-192">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="eedff-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="eedff-193">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="eedff-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="eedff-194">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eedff-195">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="eedff-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="eedff-196">[Tutorial: tutorial de Olá, mundo](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="eedff-197">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="eedff-198">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="eedff-199">[Trabalhando com o notarization Catalina do MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="eedff-200">[Tutorial: introdução ao MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="eedff-201">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="eedff-202">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="eedff-203">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="eedff-204">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="eedff-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
