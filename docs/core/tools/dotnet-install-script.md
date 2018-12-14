---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado.
ms.date: 11/15/2018
ms.openlocfilehash: 0f565fee3e4ff4bec65bd196f635e9e9601485c2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148308"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="5a019-103">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="5a019-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="5a019-104">Nome</span><span class="sxs-lookup"><span data-stu-id="5a019-104">Name</span></span>

<span data-ttu-id="5a019-105">`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a019-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a019-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5a019-106">Synopsis</span></span>

<span data-ttu-id="5a019-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="5a019-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="5a019-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5a019-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="5a019-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a019-109">Description</span></span>

<span data-ttu-id="5a019-110">O scripts `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a019-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="5a019-111">É recomendável usar a versão estável que está hospedada no [site principal do .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="5a019-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="5a019-112">Os caminhos diretos para os scripts são:</span><span class="sxs-lookup"><span data-stu-id="5a019-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="5a019-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="5a019-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="5a019-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="5a019-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="5a019-115">A principal utilidade desses scripts é para cenários de automação e instalações não administrativas.</span><span class="sxs-lookup"><span data-stu-id="5a019-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="5a019-116">Há dois scripts, um do PowerShell que funciona no Windows e um script bash que funciona no Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5a019-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="5a019-117">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="5a019-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="5a019-118">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5a019-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="5a019-119">Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="5a019-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="5a019-120">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="5a019-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="5a019-121">Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`.</span><span class="sxs-lookup"><span data-stu-id="5a019-121">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="5a019-122">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="5a019-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="5a019-123">Substitua esse comportamento padrão especificando o argumento `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="5a019-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="5a019-124">Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="5a019-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="5a019-125">Você pode instalar uma versão específica usando o argumento `--version`.</span><span class="sxs-lookup"><span data-stu-id="5a019-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="5a019-126">A versão deve ser especificada como uma versão de três partes (por exemplo, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="5a019-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="5a019-127">Se não for fornecida, será usada a versão `latest`.</span><span class="sxs-lookup"><span data-stu-id="5a019-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="5a019-128">Opções</span><span class="sxs-lookup"><span data-stu-id="5a019-128">Options</span></span>

* **`-Channel <CHANNEL>`**

  <span data-ttu-id="5a019-129">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="5a019-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="5a019-130">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5a019-130">The possible values are:</span></span>

  * <span data-ttu-id="5a019-131">`Current`: versão mais atual.</span><span class="sxs-lookup"><span data-stu-id="5a019-131">`Current` - Most current release.</span></span>
  * <span data-ttu-id="5a019-132">`LTS`: canal de suporte de longo prazo (versão mais atual compatível).</span><span class="sxs-lookup"><span data-stu-id="5a019-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  * <span data-ttu-id="5a019-133">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.0` ou `1.0`).</span><span class="sxs-lookup"><span data-stu-id="5a019-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  * <span data-ttu-id="5a019-134">Nome do branch.</span><span class="sxs-lookup"><span data-stu-id="5a019-134">Branch name.</span></span> <span data-ttu-id="5a019-135">Por exemplo, `release/2.0.0`, `release/2.0.0-preview2` ou `master` (para versões noturnas).</span><span class="sxs-lookup"><span data-stu-id="5a019-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="5a019-136">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="5a019-136">The default value is `LTS`.</span></span> <span data-ttu-id="5a019-137">Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5a019-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

* **`-Version <VERSION>`**

  <span data-ttu-id="5a019-138">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="5a019-138">Represents a specific build version.</span></span> <span data-ttu-id="5a019-139">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5a019-139">The possible values are:</span></span>

  * <span data-ttu-id="5a019-140">`latest`: build mais recente no canal (usado com a opção `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="5a019-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  * <span data-ttu-id="5a019-141">`coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).</span><span class="sxs-lookup"><span data-stu-id="5a019-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  * <span data-ttu-id="5a019-142">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="5a019-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="5a019-143">Por exemplo: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="5a019-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="5a019-144">Se não for especificada, a `-Version` assumirá o padrão `latest`.</span><span class="sxs-lookup"><span data-stu-id="5a019-144">If not specified, `-Version` defaults to `latest`.</span></span>

* **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="5a019-145">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="5a019-145">Specifies the installation path.</span></span> <span data-ttu-id="5a019-146">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="5a019-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="5a019-147">O valor padrão é *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="5a019-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="5a019-148">Os binários são colocados diretamente nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="5a019-148">Binaries are placed directly in this directory.</span></span>

* **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="5a019-149">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="5a019-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="5a019-150">Os valores possíveis são `auto`, `x64` e `x86`.</span><span class="sxs-lookup"><span data-stu-id="5a019-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="5a019-151">O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5a019-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

* **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="5a019-152">Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script.</span><span class="sxs-lookup"><span data-stu-id="5a019-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="5a019-153">A alternativa recomendada é a opção `Runtime`.</span><span class="sxs-lookup"><span data-stu-id="5a019-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="5a019-154">Instala apenas os bits de tempo de execução compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="5a019-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="5a019-155">Isso é equivalente a especificar `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5a019-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

* **`-Runtime <RUNTIME>`**

  <span data-ttu-id="5a019-156">Instala apenas o tempo de execução compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="5a019-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="5a019-157">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5a019-157">The possible values are:</span></span>

  * <span data-ttu-id="5a019-158">`dotnet`: o tempo de execução compartilhado `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="5a019-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  * <span data-ttu-id="5a019-159">`aspnetcore`: o tempo de execução compartilhado `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="5a019-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

* **`-DryRun`**

  <span data-ttu-id="5a019-160">Se definido, o script não executará a instalação.</span><span class="sxs-lookup"><span data-stu-id="5a019-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="5a019-161">Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a019-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="5a019-162">Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="5a019-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="5a019-163">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="5a019-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

* **`-NoPath`**

  <span data-ttu-id="5a019-164">Se definida, a pasta de instalação não será exportada para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="5a019-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="5a019-165">Por padrão, o script modifica o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="5a019-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

* **`-Verbose`**

  <span data-ttu-id="5a019-166">Exibe informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5a019-166">Displays diagnostics information.</span></span>

* **`-AzureFeed`**

  <span data-ttu-id="5a019-167">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="5a019-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="5a019-168">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="5a019-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="5a019-169">O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5a019-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

* **`-UncachedFeed`**

  <span data-ttu-id="5a019-170">Permite alterar a URL do feed não armazenado em cache usado por esse instalador.</span><span class="sxs-lookup"><span data-stu-id="5a019-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="5a019-171">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="5a019-171">We recommended that you don't change this value.</span></span>

* **`-NoCdn`**

  <span data-ttu-id="5a019-172">Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.</span><span class="sxs-lookup"><span data-stu-id="5a019-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

* **`-FeedCredential`**

  <span data-ttu-id="5a019-173">Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure.</span><span class="sxs-lookup"><span data-stu-id="5a019-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="5a019-174">Permite alterar a URL para usar contas de armazenamento de blobs não públicos.</span><span class="sxs-lookup"><span data-stu-id="5a019-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

* **`-ProxyAddress`**

  <span data-ttu-id="5a019-175">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="5a019-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="5a019-176">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="5a019-176">(Only valid for Windows)</span></span>

* **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="5a019-177">Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy.</span><span class="sxs-lookup"><span data-stu-id="5a019-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="5a019-178">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="5a019-178">(Only valid for Windows)</span></span>

* **`-SkipNonVersionedFiles`**

  <span data-ttu-id="5a019-179">Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.</span><span class="sxs-lookup"><span data-stu-id="5a019-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

* **`-Help`**

  <span data-ttu-id="5a019-180">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="5a019-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="5a019-181">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5a019-181">Examples</span></span>

* <span data-ttu-id="5a019-182">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="5a019-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="5a019-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="5a019-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="5a019-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5a019-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* <span data-ttu-id="5a019-185">Instale a visualização mais recente do canal 2.0 no local especificado:</span><span class="sxs-lookup"><span data-stu-id="5a019-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="5a019-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="5a019-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="5a019-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5a019-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* <span data-ttu-id="5a019-188">Instale a versão 1.1.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="5a019-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="5a019-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="5a019-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  <span data-ttu-id="5a019-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5a019-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* <span data-ttu-id="5a019-191">Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):</span><span class="sxs-lookup"><span data-stu-id="5a019-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* <span data-ttu-id="5a019-192">Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="5a019-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="5a019-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="5a019-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="5a019-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5a019-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="5a019-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a019-195">See also</span></span>

* [<span data-ttu-id="5a019-196">Versões do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a019-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
* [<span data-ttu-id="5a019-197">Arquivo de download de tempo de execução e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a019-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
