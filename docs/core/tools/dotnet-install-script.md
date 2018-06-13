---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: acdf49950ebb49751c55ae72b3f623e590489202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214374"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="bc008-103">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="bc008-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="bc008-104">Nome</span><span class="sxs-lookup"><span data-stu-id="bc008-104">Name</span></span>

<span data-ttu-id="bc008-105">`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc008-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc008-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bc008-106">Synopsis</span></span>

<span data-ttu-id="bc008-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="bc008-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="bc008-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="bc008-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="bc008-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc008-109">Description</span></span>

<span data-ttu-id="bc008-110">O scripts `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc008-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="bc008-111">É recomendável usar a versão estável que está hospedada no [site principal do .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="bc008-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="bc008-112">Os caminhos diretos para os scripts são:</span><span class="sxs-lookup"><span data-stu-id="bc008-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="bc008-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="bc008-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="bc008-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="bc008-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="bc008-115">A principal utilidade desses scripts é para cenários de automação e instalações não administrativas.</span><span class="sxs-lookup"><span data-stu-id="bc008-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="bc008-116">Há dois scripts: um é um script do PowerShell que funciona no Windows.</span><span class="sxs-lookup"><span data-stu-id="bc008-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="bc008-117">O outro script é um script de bash que funciona em Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="bc008-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="bc008-118">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="bc008-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="bc008-119">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="bc008-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="bc008-120">Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="bc008-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="bc008-121">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="bc008-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="bc008-122">Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`.</span><span class="sxs-lookup"><span data-stu-id="bc008-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="bc008-123">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="bc008-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="bc008-124">Substitua esse comportamento padrão especificando o argumento `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="bc008-124">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="bc008-125">Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="bc008-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="bc008-126">Você pode instalar uma versão específica usando o argumento `--version`.</span><span class="sxs-lookup"><span data-stu-id="bc008-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="bc008-127">A versão deve ser especificada como uma versão de terceiros (por exemplo, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="bc008-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="bc008-128">Se omitida, será usada a versão `latest`.</span><span class="sxs-lookup"><span data-stu-id="bc008-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="bc008-129">Opções</span><span class="sxs-lookup"><span data-stu-id="bc008-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="bc008-130">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="bc008-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="bc008-131">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="bc008-131">The possible values are:</span></span>

- <span data-ttu-id="bc008-132">`Current` – versão atual</span><span class="sxs-lookup"><span data-stu-id="bc008-132">`Current` - Current release</span></span>
- <span data-ttu-id="bc008-133">`LTS` – canal de suporte de longo prazo (versão atual com suporte)</span><span class="sxs-lookup"><span data-stu-id="bc008-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="bc008-134">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.0` ou `1.0`)</span><span class="sxs-lookup"><span data-stu-id="bc008-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="bc008-135">O nome do branch [por exemplo, `release/2.0.0`, `release/2.0.0-preview2` ou `master` para a versão mais recente do branch `master` (versões noturnas "mais avançadas")]</span><span class="sxs-lookup"><span data-stu-id="bc008-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="bc008-136">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="bc008-136">The default value is `LTS`.</span></span> <span data-ttu-id="bc008-137">Para saber mais sobre os canais de suporte do .NET, veja o tópico [Ciclo de vida de suporte do .NET Core](https://www.microsoft.com/net/core/support).</span><span class="sxs-lookup"><span data-stu-id="bc008-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="bc008-138">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="bc008-138">Represents a specific build version.</span></span> <span data-ttu-id="bc008-139">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="bc008-139">The possible values are:</span></span>

- <span data-ttu-id="bc008-140">`latest` – build mais recente no canal (usado com a opção `-Channel`)</span><span class="sxs-lookup"><span data-stu-id="bc008-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="bc008-141">`coherent` – build coerente mais recente no canal; usa a última combinação de pacotes estáveis (usado com as opções `-Channel` do nome do Branch)</span><span class="sxs-lookup"><span data-stu-id="bc008-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="bc008-142">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="bc008-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="bc008-143">Por exemplo: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="bc008-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="bc008-144">Se omitida, `-Version` será padronizada para `latest`.</span><span class="sxs-lookup"><span data-stu-id="bc008-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="bc008-145">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="bc008-145">Specifies the installation path.</span></span> <span data-ttu-id="bc008-146">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="bc008-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="bc008-147">O valor padrão é *%LocalAppData%\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="bc008-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="bc008-148">Observe que os binários são colocados diretamente no diretório.</span><span class="sxs-lookup"><span data-stu-id="bc008-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="bc008-149">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="bc008-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="bc008-150">Os valores possíveis são `auto`, `x64` e `x86`.</span><span class="sxs-lookup"><span data-stu-id="bc008-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="bc008-151">O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="bc008-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="bc008-152">Se for definida, essa opção limitará a instalação para o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="bc008-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="bc008-153">Não ocorre a instalação completa do SDK.</span><span class="sxs-lookup"><span data-stu-id="bc008-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="bc008-154">Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc008-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="bc008-155">Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="bc008-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="bc008-156">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="bc008-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="bc008-157">Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="bc008-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="bc008-158">Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="bc008-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="bc008-159">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="bc008-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="bc008-160">Não recomendamos a alteração desse valor.</span><span class="sxs-lookup"><span data-stu-id="bc008-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="bc008-161">O padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="bc008-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="bc008-162">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="bc008-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="bc008-163">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="bc008-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="bc008-164">Exiba informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="bc008-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="bc008-165">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="bc008-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="bc008-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bc008-166">Examples</span></span>

<span data-ttu-id="bc008-167">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="bc008-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="bc008-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="bc008-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="bc008-169">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="bc008-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="bc008-170">Instale a visualização mais recente do canal 2.0 no local especificado:</span><span class="sxs-lookup"><span data-stu-id="bc008-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="bc008-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="bc008-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="bc008-172">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="bc008-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="bc008-173">Instale a versão 1.1.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="bc008-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="bc008-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="bc008-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="bc008-175">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="bc008-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="bc008-176">Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bc008-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="bc008-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="bc008-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="bc008-178">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="bc008-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="bc008-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc008-179">See also</span></span>

<span data-ttu-id="bc008-180">[Versões do .NET Core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="bc008-180">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="bc008-181">Arquivo de download de tempo de execução e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc008-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
