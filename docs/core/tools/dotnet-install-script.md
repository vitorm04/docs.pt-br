---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts dotnet-install para instalar o SDK do .NET Core e o tempo de execução compartilhado.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092857"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="5de24-103">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="5de24-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="5de24-104">Nome</span><span class="sxs-lookup"><span data-stu-id="5de24-104">Name</span></span>

<span data-ttu-id="5de24-105">`dotnet-install.ps1` | `dotnet-install.sh`-script usado para instalar o SDK do .NET Core e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="5de24-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5de24-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5de24-106">Synopsis</span></span>

<span data-ttu-id="5de24-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="5de24-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="5de24-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="5de24-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="5de24-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="5de24-109">Description</span></span>

<span data-ttu-id="5de24-110">Os scripts de `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui o CLI do .NET Core e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="5de24-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="5de24-111">Recomendamos que você use a versão estável dos scripts:</span><span class="sxs-lookup"><span data-stu-id="5de24-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="5de24-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="5de24-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="5de24-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="5de24-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="5de24-114">A principal utilidade desses scripts é para cenários de automação e instalações não administrativas.</span><span class="sxs-lookup"><span data-stu-id="5de24-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="5de24-115">Há dois scripts, um do PowerShell que funciona no Windows e um script bash que funciona no Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5de24-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="5de24-116">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="5de24-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="5de24-117">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5de24-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="5de24-118">Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="5de24-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="5de24-119">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="5de24-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="5de24-120">Se você quiser obter somente o runtime compartilhado, especifique o argumento `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="5de24-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="5de24-121">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="5de24-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="5de24-122">Substitua esse comportamento padrão especificando o argumento `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="5de24-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="5de24-123">Antes de executar o script, instale as [dependências](../install/dependencies.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="5de24-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="5de24-124">Você pode instalar uma versão específica usando o argumento `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="5de24-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="5de24-125">A versão deve ser especificada como uma versão de três partes (por exemplo, `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="5de24-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="5de24-126">Se não for fornecida, será usada a versão `latest`.</span><span class="sxs-lookup"><span data-stu-id="5de24-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="5de24-127">Opções</span><span class="sxs-lookup"><span data-stu-id="5de24-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="5de24-128">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="5de24-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="5de24-129">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5de24-129">The possible values are:</span></span>

  - <span data-ttu-id="5de24-130">`Current`: versão mais atual.</span><span class="sxs-lookup"><span data-stu-id="5de24-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="5de24-131">`LTS`: canal de suporte de longo prazo (versão mais atual compatível).</span><span class="sxs-lookup"><span data-stu-id="5de24-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="5de24-132">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.1` ou `3.0`).</span><span class="sxs-lookup"><span data-stu-id="5de24-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="5de24-133">Nome do Branch: por exemplo, `release/3.1.1xx` ou `master` (para versões noturnas).</span><span class="sxs-lookup"><span data-stu-id="5de24-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="5de24-134">Use esta opção para instalar uma versão de um canal de visualização.</span><span class="sxs-lookup"><span data-stu-id="5de24-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="5de24-135">Use o nome do canal, conforme listado em [instaladores e binários](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="5de24-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="5de24-136">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="5de24-136">The default value is `LTS`.</span></span> <span data-ttu-id="5de24-137">Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5de24-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="5de24-138">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="5de24-138">Represents a specific build version.</span></span> <span data-ttu-id="5de24-139">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5de24-139">The possible values are:</span></span>

  - <span data-ttu-id="5de24-140">`latest`: build mais recente no canal (usado com a opção `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="5de24-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="5de24-141">`coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).</span><span class="sxs-lookup"><span data-stu-id="5de24-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="5de24-142">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="5de24-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="5de24-143">Por exemplo: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="5de24-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="5de24-144">Se não for especificada, a `-Version` assumirá o padrão `latest`.</span><span class="sxs-lookup"><span data-stu-id="5de24-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="5de24-145">Especifica um caminho para um arquivo [global. JSON](global-json.md) que será usado para determinar a versão do SDK.</span><span class="sxs-lookup"><span data-stu-id="5de24-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="5de24-146">O arquivo *global. JSON* deve ter um valor para `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="5de24-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="5de24-147">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="5de24-147">Specifies the installation path.</span></span> <span data-ttu-id="5de24-148">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="5de24-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="5de24-149">O valor padrão é *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="5de24-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="5de24-150">Os binários são colocados diretamente nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="5de24-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="5de24-151">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="5de24-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="5de24-152">Os valores possíveis são `<auto>`, `amd64`, `x64`, `x86`, `arm64` e `arm`.</span><span class="sxs-lookup"><span data-stu-id="5de24-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="5de24-153">O valor padrão é `<auto>`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5de24-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="5de24-154">Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script.</span><span class="sxs-lookup"><span data-stu-id="5de24-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="5de24-155">A alternativa recomendada é a opção `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="5de24-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="5de24-156">Instala apenas os bits de runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="5de24-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="5de24-157">Essa opção é equivalente a especificar `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5de24-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="5de24-158">Instala apenas o runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="5de24-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="5de24-159">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="5de24-159">The possible values are:</span></span>

  - <span data-ttu-id="5de24-160">`dotnet`: o runtime compartilhado `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="5de24-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="5de24-161">`aspnetcore`: o runtime compartilhado `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="5de24-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="5de24-162">`windowsdesktop`: o runtime compartilhado `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="5de24-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="5de24-163">Se definido, o script não executará a instalação.</span><span class="sxs-lookup"><span data-stu-id="5de24-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="5de24-164">Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5de24-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="5de24-165">Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="5de24-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="5de24-166">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="5de24-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="5de24-167">Se definida, a pasta de instalação não será exportada para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="5de24-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="5de24-168">Por padrão, o script modifica o caminho, o que torna o CLI do .NET Core disponível imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="5de24-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="5de24-169">Exibe informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5de24-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="5de24-170">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="5de24-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="5de24-171">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="5de24-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="5de24-172">O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5de24-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="5de24-173">Permite alterar a URL do feed não armazenado em cache usado por esse instalador.</span><span class="sxs-lookup"><span data-stu-id="5de24-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="5de24-174">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="5de24-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="5de24-175">Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.</span><span class="sxs-lookup"><span data-stu-id="5de24-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="5de24-176">Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure.</span><span class="sxs-lookup"><span data-stu-id="5de24-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="5de24-177">Permite alterar a URL para usar contas de armazenamento de blobs não públicos.</span><span class="sxs-lookup"><span data-stu-id="5de24-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="5de24-178">Especifica o [identificador de tempo de execução](../rid-catalog.md) para o qual as ferramentas estão sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="5de24-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="5de24-179">Use `linux-x64` para Linux portátil.</span><span class="sxs-lookup"><span data-stu-id="5de24-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="5de24-180">(Válido somente para Linux/macOS)</span><span class="sxs-lookup"><span data-stu-id="5de24-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="5de24-181">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="5de24-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="5de24-182">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="5de24-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="5de24-183">Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy.</span><span class="sxs-lookup"><span data-stu-id="5de24-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="5de24-184">(Válido somente para Windows)</span><span class="sxs-lookup"><span data-stu-id="5de24-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="5de24-185">Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.</span><span class="sxs-lookup"><span data-stu-id="5de24-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="5de24-186">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="5de24-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="5de24-187">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5de24-187">Examples</span></span>

- <span data-ttu-id="5de24-188">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="5de24-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="5de24-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="5de24-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="5de24-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5de24-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="5de24-191">Instale a versão mais recente do canal 3,1 no local especificado:</span><span class="sxs-lookup"><span data-stu-id="5de24-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="5de24-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="5de24-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="5de24-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5de24-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="5de24-194">Instale a versão 3.0.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="5de24-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="5de24-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="5de24-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="5de24-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5de24-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="5de24-197">Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):</span><span class="sxs-lookup"><span data-stu-id="5de24-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="5de24-198">Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="5de24-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="5de24-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="5de24-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="5de24-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5de24-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="5de24-201">Confira também</span><span class="sxs-lookup"><span data-stu-id="5de24-201">See also</span></span>

- [<span data-ttu-id="5de24-202">Versões do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5de24-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="5de24-203">Arquivo de download de runtime e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5de24-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
