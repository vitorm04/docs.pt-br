---
title: Instalar o SDK do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 54819b409422e8bda9efe25478aa3424683a380b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567468"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="822f3-104">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="822f3-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="822f3-105">Neste artigo, você aprenderá a instalar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="822f3-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="822f3-106">O SDK do .NET Core é usado para criar aplicativos e bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="822f3-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="822f3-107">O tempo de execução do .NET Core é sempre instalado com o SDK.</span><span class="sxs-lookup"><span data-stu-id="822f3-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="822f3-108">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="822f3-108">Install with an installer</span></span>

<span data-ttu-id="822f3-109">O Windows e o macOS têm instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="822f3-109">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="822f3-110">[CPUs Windows x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [cpus x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="822f3-110">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="822f3-111">[CPUs do MacOS x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="822f3-111">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="822f3-112">Instalar com um Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="822f3-112">Install with a package manager</span></span>

<span data-ttu-id="822f3-113">Você pode instalar o SDK do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns.</span><span class="sxs-lookup"><span data-stu-id="822f3-113">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="822f3-114">Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-114">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="822f3-115">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="822f3-115">Download and manually install</span></span>

<span data-ttu-id="822f3-116">Para extrair o SDK e tornar os comandos disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="822f3-116">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="822f3-117">Em seguida, abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="822f3-117">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="822f3-118">Os comandos acima só disponibilizarão os comandos do SDK do .NET para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="822f3-118">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="822f3-119">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="822f3-119">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="822f3-120">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="822f3-120">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="822f3-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="822f3-121">For example:</span></span>
>
> - <span data-ttu-id="822f3-122">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="822f3-122">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="822f3-123">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="822f3-123">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="822f3-124">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="822f3-124">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="822f3-125">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da instrução `PATH` existente.</span><span class="sxs-lookup"><span data-stu-id="822f3-125">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="822f3-126">Se nenhuma instrução de `PATH` for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="822f3-126">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="822f3-127">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="822f3-127">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="822f3-128">Instalar com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="822f3-128">Install with Visual Studio</span></span>

<span data-ttu-id="822f3-129">Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão de SDK do .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="822f3-129">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="822f3-130">Versão do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="822f3-130">.NET Core SDK version</span></span> | <span data-ttu-id="822f3-131">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="822f3-131">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="822f3-132">visualização de 3,1</span><span class="sxs-lookup"><span data-stu-id="822f3-132">3.1 Preview</span></span>           | <span data-ttu-id="822f3-133">Visual Studio 2019 versão 16,4 Preview ou superior.</span><span class="sxs-lookup"><span data-stu-id="822f3-133">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="822f3-134">3.0</span><span class="sxs-lookup"><span data-stu-id="822f3-134">3.0</span></span>                   | <span data-ttu-id="822f3-135">Visual Studio 2019 versão 16,3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="822f3-135">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="822f3-136">2.2</span><span class="sxs-lookup"><span data-stu-id="822f3-136">2.2</span></span>                   | <span data-ttu-id="822f3-137">Visual Studio 2017 versão 15,9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="822f3-137">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="822f3-138">2.1</span><span class="sxs-lookup"><span data-stu-id="822f3-138">2.1</span></span>                   | <span data-ttu-id="822f3-139">Visual Studio 2017 versão 15,7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="822f3-139">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="822f3-140">Se você já tiver o Visual Studio instalado, poderá verificar sua versão com as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="822f3-140">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="822f3-141">{1&gt;Abra o Visual Studio.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="822f3-141">Open Visual Studio.</span></span>
01. <span data-ttu-id="822f3-142">Selecione **ajuda** > **sobre Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="822f3-142">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="822f3-143">Leia o número de versão na caixa de diálogo **sobre** .</span><span class="sxs-lookup"><span data-stu-id="822f3-143">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="822f3-144">O Visual Studio pode instalar o SDK do .NET Core e o tempo de execução mais recentes.</span><span class="sxs-lookup"><span data-stu-id="822f3-144">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="822f3-145">[Baixe o Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="822f3-145">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="822f3-146">Selecionar uma carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="822f3-146">Select a workload</span></span>

<span data-ttu-id="822f3-147">Ao instalar ou modificar o Visual Studio, selecione uma das cargas de trabalho a seguir, dependendo do tipo de aplicativo que você está criando:</span><span class="sxs-lookup"><span data-stu-id="822f3-147">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="822f3-148">A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .</span><span class="sxs-lookup"><span data-stu-id="822f3-148">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="822f3-149">A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="822f3-149">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="822f3-150">A carga de trabalho de **desenvolvimento do Azure** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="822f3-150">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="822f3-151">A carga de trabalho **.net desktop Development** na seção **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="822f3-151">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="822f3-152">[![o Windows Visual Studio 2019 com carga de trabalho do .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="822f3-152">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="822f3-153">Instalar com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="822f3-153">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="822f3-154">Visual Studio para Mac instala o SDK do .NET Core quando a carga de trabalho do **.NET Core** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="822f3-154">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="822f3-155">Para começar a usar o desenvolvimento do .NET Core no macOS, consulte [instalar o Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="822f3-155">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="822f3-156">[![macOS Visual Studio 2019 para Mac com o recurso de carga de trabalho do .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="822f3-156">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="822f3-157">Instalar junto com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="822f3-157">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="822f3-158">Visual Studio Code é um editor de código-fonte leve e avançado que é executado em sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="822f3-158">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="822f3-159">Visual Studio Code está disponível para Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="822f3-159">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="822f3-160">Embora Visual Studio Code não venha com um instalador .NET Core automatizado como o Visual Studio, adicionar o suporte ao .NET Core é simples.</span><span class="sxs-lookup"><span data-stu-id="822f3-160">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="822f3-161">[Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="822f3-161">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="822f3-162">[Baixe e instale o SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="822f3-162">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="822f3-163">[Instale a C# extensão do Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="822f3-163">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="822f3-164">Instalar com a automação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="822f3-164">Install with PowerShell automation</span></span>

<span data-ttu-id="822f3-165">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="822f3-165">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="822f3-166">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-166">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="822f3-167">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="822f3-167">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="822f3-168">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="822f3-168">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="822f3-169">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="822f3-169">Install with bash automation</span></span>

<span data-ttu-id="822f3-170">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK.</span><span class="sxs-lookup"><span data-stu-id="822f3-170">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="822f3-171">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-171">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="822f3-172">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="822f3-172">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="822f3-173">Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.</span><span class="sxs-lookup"><span data-stu-id="822f3-173">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="822f3-174">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="822f3-174">All .NET Core downloads</span></span>

<span data-ttu-id="822f3-175">Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:</span><span class="sxs-lookup"><span data-stu-id="822f3-175">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="822f3-176">Downloads da versão prévia do .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="822f3-176">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="822f3-177">Downloads do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="822f3-177">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="822f3-178">Downloads do .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="822f3-178">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="822f3-179">Downloads do .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="822f3-179">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="822f3-180">Docker</span><span class="sxs-lookup"><span data-stu-id="822f3-180">Docker</span></span>

<span data-ttu-id="822f3-181">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="822f3-181">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="822f3-182">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="822f3-182">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="822f3-183">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="822f3-183">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="822f3-184">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="822f3-184">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="822f3-185">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="822f3-185">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="822f3-186">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="822f3-186">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="822f3-187">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="822f3-187">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="822f3-188">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-188">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="822f3-189">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="822f3-189">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="822f3-190">[Tutorial: C# tutorial de Olá, mundo](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-190">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="822f3-191">[Tutorial: Visual Basic Olá, mundo tutorial](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-191">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="822f3-192">[Tutorial: criar um novo aplicativo com Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="822f3-192">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="822f3-193">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-193">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="822f3-194">[Tutorial: introdução ao MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-194">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="822f3-195">[Tutorial: criar um novo aplicativo com Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="822f3-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="822f3-196">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="822f3-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
