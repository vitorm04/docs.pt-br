---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts dotnet-install para instalar o SDK do .NET Core e o tempo de execução compartilhado.
ms.date: 04/30/2020
ms.openlocfilehash: cecfbb86c4a2863161d3df7c78201fa8057abfe5
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415923"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="6be2e-103">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="6be2e-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="6be2e-104">Nome</span><span class="sxs-lookup"><span data-stu-id="6be2e-104">Name</span></span>

<span data-ttu-id="6be2e-105">`dotnet-install.ps1` | `dotnet-install.sh`-Script usado para instalar o SDK do .NET Core e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="6be2e-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6be2e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="6be2e-106">Synopsis</span></span>

<span data-ttu-id="6be2e-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="6be2e-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="6be2e-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="6be2e-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="6be2e-109">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="6be2e-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="6be2e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6be2e-110">Description</span></span>

<span data-ttu-id="6be2e-111">Os `dotnet-install` scripts executam uma instalação não administrativa do SDK do .NET Core, que inclui o CLI do .NET Core e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="6be2e-111">The `dotnet-install` scripts perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span> <span data-ttu-id="6be2e-112">Há dois scripts:</span><span class="sxs-lookup"><span data-stu-id="6be2e-112">There are two scripts:</span></span>

* <span data-ttu-id="6be2e-113">Um script do PowerShell que funciona no Windows.</span><span class="sxs-lookup"><span data-stu-id="6be2e-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="6be2e-114">Um script bash que funciona no Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="6be2e-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="6be2e-115">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6be2e-115">Purpose</span></span>

 <span data-ttu-id="6be2e-116">O uso pretendido dos scripts é para cenários de CI (integração contínua), em que:</span><span class="sxs-lookup"><span data-stu-id="6be2e-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="6be2e-117">O SDK precisa ser instalado sem interação do usuário e sem direitos de administrador.</span><span class="sxs-lookup"><span data-stu-id="6be2e-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="6be2e-118">A instalação do SDK não precisa persistir em várias execuções de CI.</span><span class="sxs-lookup"><span data-stu-id="6be2e-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="6be2e-119">A sequência típica de eventos:</span><span class="sxs-lookup"><span data-stu-id="6be2e-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="6be2e-120">CI é disparado.</span><span class="sxs-lookup"><span data-stu-id="6be2e-120">CI is triggered.</span></span>
  * <span data-ttu-id="6be2e-121">O CI instala o SDK usando um desses scripts.</span><span class="sxs-lookup"><span data-stu-id="6be2e-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="6be2e-122">O CI conclui seu trabalho e limpa os dados temporários, incluindo a instalação do SDK.</span><span class="sxs-lookup"><span data-stu-id="6be2e-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="6be2e-123">Para configurar um ambiente de desenvolvimento ou executar aplicativos, use os instaladores em vez desses scripts.</span><span class="sxs-lookup"><span data-stu-id="6be2e-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="6be2e-124">Versão recomendada</span><span class="sxs-lookup"><span data-stu-id="6be2e-124">Recommended version</span></span>

<span data-ttu-id="6be2e-125">Recomendamos que você use a versão estável dos scripts:</span><span class="sxs-lookup"><span data-stu-id="6be2e-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="6be2e-126">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="6be2e-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="6be2e-127">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="6be2e-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="6be2e-128">Comportamento do script</span><span class="sxs-lookup"><span data-stu-id="6be2e-128">Script behavior</span></span>

<span data-ttu-id="6be2e-129">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="6be2e-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="6be2e-130">Eles baixam o arquivo ZIP/tarball da CLI Build Descartes e prosseguem para instalá-lo no local padrão ou em um local especificado por `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="6be2e-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="6be2e-131">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="6be2e-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="6be2e-132">Se você quiser obter somente o runtime compartilhado, especifique o argumento `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="6be2e-133">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="6be2e-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="6be2e-134">Substitua esse comportamento padrão especificando o argumento `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="6be2e-135">O script não define a `DOTNET_ROOT` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="6be2e-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="6be2e-136">Antes de executar o script, instale as [dependências](../install/windows.md#dependencies) necessárias.</span><span class="sxs-lookup"><span data-stu-id="6be2e-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="6be2e-137">Você pode instalar uma versão específica usando o argumento `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="6be2e-138">A versão deve ser especificada como um número de versão de três partes, como `2.1.0` .</span><span class="sxs-lookup"><span data-stu-id="6be2e-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="6be2e-139">Se a versão não for especificada, o script instalará a `latest` versão.</span><span class="sxs-lookup"><span data-stu-id="6be2e-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="6be2e-140">Os scripts de instalação não atualizam o registro no Windows.</span><span class="sxs-lookup"><span data-stu-id="6be2e-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="6be2e-141">Eles apenas baixam os binários zipados e os copiam para uma pasta.</span><span class="sxs-lookup"><span data-stu-id="6be2e-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="6be2e-142">Se você quiser que os valores de chave do registro sejam atualizados, use os instaladores do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6be2e-142">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="6be2e-143">Opções</span><span class="sxs-lookup"><span data-stu-id="6be2e-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="6be2e-144">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="6be2e-144">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="6be2e-145">Os valores possíveis são `<auto>`, `amd64`, `x64`, `x86`, `arm64` e `arm`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="6be2e-146">O valor padrão é `<auto>`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="6be2e-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="6be2e-147">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="6be2e-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="6be2e-148">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="6be2e-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="6be2e-149">O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="6be2e-150">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="6be2e-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="6be2e-151">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6be2e-151">The possible values are:</span></span>

  - <span data-ttu-id="6be2e-152">`Current`: versão mais atual.</span><span class="sxs-lookup"><span data-stu-id="6be2e-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="6be2e-153">`LTS`: canal de suporte de longo prazo (versão mais atual compatível).</span><span class="sxs-lookup"><span data-stu-id="6be2e-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="6be2e-154">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.1` ou `3.0`).</span><span class="sxs-lookup"><span data-stu-id="6be2e-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="6be2e-155">Nome do Branch: por exemplo, `release/3.1.1xx` ou `master` (para versões noturnas).</span><span class="sxs-lookup"><span data-stu-id="6be2e-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="6be2e-156">Use esta opção para instalar uma versão de um canal de visualização.</span><span class="sxs-lookup"><span data-stu-id="6be2e-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="6be2e-157">Use o nome do canal, conforme listado em [instaladores e binários](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="6be2e-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="6be2e-158">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-158">The default value is `LTS`.</span></span> <span data-ttu-id="6be2e-159">Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6be2e-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="6be2e-160">Se definido, o script não executará a instalação.</span><span class="sxs-lookup"><span data-stu-id="6be2e-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="6be2e-161">Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6be2e-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="6be2e-162">Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="6be2e-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="6be2e-163">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="6be2e-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="6be2e-164">Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure.</span><span class="sxs-lookup"><span data-stu-id="6be2e-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="6be2e-165">Permite alterar a URL para usar contas de armazenamento de blobs não públicos.</span><span class="sxs-lookup"><span data-stu-id="6be2e-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="6be2e-166">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="6be2e-166">Prints out help for the script.</span></span> <span data-ttu-id="6be2e-167">Aplica-se somente ao script bash.</span><span class="sxs-lookup"><span data-stu-id="6be2e-167">Applies only to bash script.</span></span> <span data-ttu-id="6be2e-168">Para o PowerShell, use `Get-Help ./dotnet-install.ps1` .</span><span class="sxs-lookup"><span data-stu-id="6be2e-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="6be2e-169">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="6be2e-169">Specifies the installation path.</span></span> <span data-ttu-id="6be2e-170">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="6be2e-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="6be2e-171">O valor padrão é *%LocalAppData%\Microsoft\dotnet* no Windows e no */usr/share/dotnet* no linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="6be2e-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="6be2e-172">Os binários são colocados diretamente nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="6be2e-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="6be2e-173">Especifica um caminho para um [global.jsno](global-json.md) arquivo que será usado para determinar a versão do SDK.</span><span class="sxs-lookup"><span data-stu-id="6be2e-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="6be2e-174">O *global.jsno* arquivo deve ter um valor para `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="6be2e-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="6be2e-175">Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.</span><span class="sxs-lookup"><span data-stu-id="6be2e-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="6be2e-176">Se definida, a pasta de instalação não será exportada para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="6be2e-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="6be2e-177">Por padrão, o script modifica o caminho, o que torna o CLI do .NET Core disponível imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="6be2e-177">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="6be2e-178">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="6be2e-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="6be2e-179">(Válido somente para Windows.)</span><span class="sxs-lookup"><span data-stu-id="6be2e-179">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="6be2e-180">Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy.</span><span class="sxs-lookup"><span data-stu-id="6be2e-180">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="6be2e-181">(Válido somente para Windows.)</span><span class="sxs-lookup"><span data-stu-id="6be2e-181">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="6be2e-182">Instala apenas o runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="6be2e-182">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="6be2e-183">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6be2e-183">The possible values are:</span></span>

  - <span data-ttu-id="6be2e-184">`dotnet`: o runtime compartilhado `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-184">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="6be2e-185">`aspnetcore`: o runtime compartilhado `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-185">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="6be2e-186">`windowsdesktop`: o runtime compartilhado `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-186">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="6be2e-187">Especifica o [identificador de tempo de execução](../rid-catalog.md) para o qual as ferramentas estão sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="6be2e-187">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="6be2e-188">Use `linux-x64` para Linux portátil.</span><span class="sxs-lookup"><span data-stu-id="6be2e-188">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="6be2e-189">(Válido somente para Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="6be2e-189">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="6be2e-190">Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script.</span><span class="sxs-lookup"><span data-stu-id="6be2e-190">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="6be2e-191">A alternativa recomendada é a opção `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-191">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="6be2e-192">Instala apenas os bits de runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="6be2e-192">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="6be2e-193">Essa opção é equivalente a especificar `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="6be2e-193">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="6be2e-194">Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.</span><span class="sxs-lookup"><span data-stu-id="6be2e-194">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="6be2e-195">Permite alterar a URL do feed não armazenado em cache usado por esse instalador.</span><span class="sxs-lookup"><span data-stu-id="6be2e-195">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="6be2e-196">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="6be2e-196">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="6be2e-197">Exibe informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="6be2e-197">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="6be2e-198">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="6be2e-198">Represents a specific build version.</span></span> <span data-ttu-id="6be2e-199">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6be2e-199">The possible values are:</span></span>

  - <span data-ttu-id="6be2e-200">`latest`: build mais recente no canal (usado com a opção `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="6be2e-200">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="6be2e-201">`coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).</span><span class="sxs-lookup"><span data-stu-id="6be2e-201">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="6be2e-202">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-202">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="6be2e-203">Por exemplo: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-203">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="6be2e-204">Se não for especificada, a `-Version` assumirá o padrão `latest`.</span><span class="sxs-lookup"><span data-stu-id="6be2e-204">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="6be2e-205">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6be2e-205">Examples</span></span>

- <span data-ttu-id="6be2e-206">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="6be2e-206">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="6be2e-207">Windows:</span><span class="sxs-lookup"><span data-stu-id="6be2e-207">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="6be2e-208">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6be2e-208">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="6be2e-209">Instale a versão mais recente do canal 3,1 no local especificado:</span><span class="sxs-lookup"><span data-stu-id="6be2e-209">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="6be2e-210">Windows:</span><span class="sxs-lookup"><span data-stu-id="6be2e-210">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="6be2e-211">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6be2e-211">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="6be2e-212">Instale a versão 3.0.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="6be2e-212">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="6be2e-213">Windows:</span><span class="sxs-lookup"><span data-stu-id="6be2e-213">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="6be2e-214">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6be2e-214">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="6be2e-215">Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):</span><span class="sxs-lookup"><span data-stu-id="6be2e-215">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="6be2e-216">Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="6be2e-216">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="6be2e-217">Windows:</span><span class="sxs-lookup"><span data-stu-id="6be2e-217">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="6be2e-218">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6be2e-218">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="6be2e-219">Confira também</span><span class="sxs-lookup"><span data-stu-id="6be2e-219">See also</span></span>

- [<span data-ttu-id="6be2e-220">Versões do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6be2e-220">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="6be2e-221">Arquivo de download de runtime e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6be2e-221">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
