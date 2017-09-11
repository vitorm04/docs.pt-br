---
title: Scripts dotnet-install
description: "Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado."
keywords: dotnet-install, dotnet-install scripts, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/28/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.translationtype: HT
ms.sourcegitcommit: c6e199800a86bc8b275fed4e3ba3ea6f77c7d2fa
ms.openlocfilehash: 92c2b4dcd446d3bf68783768db25ad55b14fac44
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---

# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="a4f5c-104">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="a4f5c-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="a4f5c-105">Nome</span><span class="sxs-lookup"><span data-stu-id="a4f5c-105">Name</span></span>

<span data-ttu-id="a4f5c-106">`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a4f5c-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a4f5c-107">Synopsis</span></span>

<span data-ttu-id="a4f5c-108">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="a4f5c-109">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="a4f5c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4f5c-110">Description</span></span>

<span data-ttu-id="a4f5c-111">O scripts `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-111">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="a4f5c-112">É recomendável usar a versão estável que está hospedada no [site principal do .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="a4f5c-112">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="a4f5c-113">Os caminhos diretos para os scripts são:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-113">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="a4f5c-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="a4f5c-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="a4f5c-116">A principal utilidade desses scripts é para cenários de automação e instalações não administrativas.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-116">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="a4f5c-117">Há dois scripts: um é um script do PowerShell que funciona no Windows.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-117">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="a4f5c-118">O outro script é um script de bash que funciona em Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-118">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="a4f5c-119">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-119">Both scripts have the same behavior.</span></span> <span data-ttu-id="a4f5c-120">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-120">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="a4f5c-121">Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-121">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="a4f5c-122">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-122">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="a4f5c-123">Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-123">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="a4f5c-124">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-124">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="a4f5c-125">Substitua esse comportamento padrão especificando o argumento `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-125">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="a4f5c-126">Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-126">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="a4f5c-127">Você pode instalar uma versão específica usando o argumento `--version`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-127">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="a4f5c-128">A versão deve ser especificada como uma versão de terceiros (por exemplo, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="a4f5c-128">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="a4f5c-129">Se omitida, será usada a versão `latest`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-129">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="a4f5c-130">Opções</span><span class="sxs-lookup"><span data-stu-id="a4f5c-130">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="a4f5c-131">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-131">Specifies the source channel for the installation.</span></span> <span data-ttu-id="a4f5c-132">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-132">The possible values are:</span></span>

- <span data-ttu-id="a4f5c-133">`Current` – versão atual</span><span class="sxs-lookup"><span data-stu-id="a4f5c-133">`Current` - Current release</span></span>
- <span data-ttu-id="a4f5c-134">`LTS` – canal de suporte de longo prazo (versão atual com suporte)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-134">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="a4f5c-135">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.0` ou `1.0`)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-135">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="a4f5c-136">O nome do branch [por exemplo, `release/2.0.0`, `release/2.0.0-preview2` ou `master` para a versão mais recente do branch `master` (versões noturnas "mais avançadas")]</span><span class="sxs-lookup"><span data-stu-id="a4f5c-136">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="a4f5c-137">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-137">The default value is `LTS`.</span></span> <span data-ttu-id="a4f5c-138">Para saber mais sobre os canais de suporte do .NET, veja o tópico [Ciclo de vida de suporte do .NET Core](https://www.microsoft.com/net/core/support).</span><span class="sxs-lookup"><span data-stu-id="a4f5c-138">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="a4f5c-139">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-139">Represents a specific build version.</span></span> <span data-ttu-id="a4f5c-140">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-140">The possible values are:</span></span>

- <span data-ttu-id="a4f5c-141">`latest` – build mais recente no canal (usado com a opção `-Channel`)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-141">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="a4f5c-142">`coherent` – build coerente mais recente no canal; usa a última combinação de pacotes estáveis (usado com as opções `-Channel` do nome do Branch)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-142">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="a4f5c-143">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-143">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="a4f5c-144">Por exemplo: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="a4f5c-144">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="a4f5c-145">Se omitida, `-Version` será padronizada para `latest`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-145">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="a4f5c-146">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-146">Specifies the installation path.</span></span> <span data-ttu-id="a4f5c-147">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-147">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="a4f5c-148">O valor padrão é *%LocalAppData%\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-148">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="a4f5c-149">Observe que os binários são colocados diretamente no diretório.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-149">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="a4f5c-150">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-150">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="a4f5c-151">Os valores possíveis são `auto`, `x64` e `x86`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-151">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="a4f5c-152">O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-152">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="a4f5c-153">Se for definida, essa opção limitará a instalação para o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-153">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="a4f5c-154">Não ocorre a instalação completa do SDK.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-154">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="a4f5c-155">Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-155">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="a4f5c-156">Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-156">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="a4f5c-157">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-157">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="a4f5c-158">Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-158">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="a4f5c-159">Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-159">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="a4f5c-160">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-160">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="a4f5c-161">Não recomendamos a alteração desse valor.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-161">It isn't recommended that you change this value.</span></span> <span data-ttu-id="a4f5c-162">O padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-162">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="a4f5c-163">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="a4f5c-164">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="a4f5c-164">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="a4f5c-165">Exiba informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-165">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="a4f5c-166">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="a4f5c-166">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="a4f5c-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4f5c-167">Examples</span></span>

<span data-ttu-id="a4f5c-168">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-168">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="a4f5c-169">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-169">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="a4f5c-170">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-170">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="a4f5c-171">Instale a visualização mais recente do canal 2.0 no local especificado:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-171">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="a4f5c-172">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-172">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="a4f5c-173">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-173">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="a4f5c-174">Instale a versão 1.1.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-174">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="a4f5c-175">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-175">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="a4f5c-176">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4f5c-176">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

## <a name="see-also"></a><span data-ttu-id="a4f5c-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4f5c-177">See also</span></span>

<span data-ttu-id="a4f5c-178">[Versões do .NET Core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="a4f5c-178">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="a4f5c-179">Arquivo de download de tempo de execução e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a4f5c-179">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

