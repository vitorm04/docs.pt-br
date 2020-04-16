---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts de instalação dotnet para instalar o .NET Core SDK e o tempo de execução compartilhado.
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463672"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="55f86-103">referência de scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="55f86-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="55f86-104">Nome</span><span class="sxs-lookup"><span data-stu-id="55f86-104">Name</span></span>

<span data-ttu-id="55f86-105">`dotnet-install.ps1` | `dotnet-install.sh`- Script usado para instalar o .NET Core SDK e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="55f86-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55f86-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="55f86-106">Synopsis</span></span>

<span data-ttu-id="55f86-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="55f86-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="55f86-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="55f86-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="55f86-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="55f86-109">Description</span></span>

<span data-ttu-id="55f86-110">Os `dotnet-install` scripts são usados para executar uma instalação não-admin do .NET Core SDK, que inclui o .NET Core CLI e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="55f86-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="55f86-111">Recomendamos que você use a versão estável dos scripts:</span><span class="sxs-lookup"><span data-stu-id="55f86-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="55f86-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="55f86-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="55f86-113">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="55f86-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="55f86-114">A principal utilidade desses scripts é para cenários de automação e instalações não administrativas.</span><span class="sxs-lookup"><span data-stu-id="55f86-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="55f86-115">Há dois scripts, um do PowerShell que funciona no Windows e um script bash que funciona no Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="55f86-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="55f86-116">Ambos os scripts têm o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="55f86-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="55f86-117">O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="55f86-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="55f86-118">Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="55f86-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="55f86-119">Por padrão, os scripts de instalação baixam o SDK e o instalam.</span><span class="sxs-lookup"><span data-stu-id="55f86-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="55f86-120">Se você quiser obter somente o runtime compartilhado, especifique o argumento `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="55f86-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="55f86-121">Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="55f86-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="55f86-122">Substitua esse comportamento padrão especificando o argumento `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="55f86-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="55f86-123">Antes de executar o script, instale as [dependências](../install/dependencies.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="55f86-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="55f86-124">Você pode instalar uma versão específica usando o argumento `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="55f86-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="55f86-125">A versão deve ser especificada como uma versão `2.1.0`de três partes (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="55f86-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="55f86-126">Se não for fornecida, será usada a versão `latest`.</span><span class="sxs-lookup"><span data-stu-id="55f86-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="55f86-127">Opções</span><span class="sxs-lookup"><span data-stu-id="55f86-127">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="55f86-128">Arquitetura dos binários do .NET Core para instalação.</span><span class="sxs-lookup"><span data-stu-id="55f86-128">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="55f86-129">Os valores possíveis são `<auto>`, `amd64`, `x64`, `x86`, `arm64` e `arm`.</span><span class="sxs-lookup"><span data-stu-id="55f86-129">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="55f86-130">O valor padrão é `<auto>`, que representa a arquitetura do sistema operacional em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="55f86-130">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="55f86-131">Especifica a URL para o feed do Azure para o instalador.</span><span class="sxs-lookup"><span data-stu-id="55f86-131">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="55f86-132">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="55f86-132">We recommended that you don't change this value.</span></span> <span data-ttu-id="55f86-133">O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="55f86-133">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="55f86-134">Especifica o canal de origem da instalação.</span><span class="sxs-lookup"><span data-stu-id="55f86-134">Specifies the source channel for the installation.</span></span> <span data-ttu-id="55f86-135">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="55f86-135">The possible values are:</span></span>

  - <span data-ttu-id="55f86-136">`Current`: versão mais atual.</span><span class="sxs-lookup"><span data-stu-id="55f86-136">`Current` - Most current release.</span></span>
  - <span data-ttu-id="55f86-137">`LTS`: canal de suporte de longo prazo (versão mais atual compatível).</span><span class="sxs-lookup"><span data-stu-id="55f86-137">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="55f86-138">Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.1` ou `3.0`).</span><span class="sxs-lookup"><span data-stu-id="55f86-138">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="55f86-139">Nome da filial: `release/3.1.1xx` `master` por exemplo, ou (para lançamentos noturnos).</span><span class="sxs-lookup"><span data-stu-id="55f86-139">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="55f86-140">Use esta opção para instalar uma versão de um canal de visualização.</span><span class="sxs-lookup"><span data-stu-id="55f86-140">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="55f86-141">Use o nome do canal conforme listado em [Instaladores e Binários](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="55f86-141">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="55f86-142">O valor padrão é `LTS`.</span><span class="sxs-lookup"><span data-stu-id="55f86-142">The default value is `LTS`.</span></span> <span data-ttu-id="55f86-143">Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="55f86-143">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="55f86-144">Se definido, o script não executará a instalação.</span><span class="sxs-lookup"><span data-stu-id="55f86-144">If set, the script won't perform the installation.</span></span> <span data-ttu-id="55f86-145">Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55f86-145">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="55f86-146">Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.</span><span class="sxs-lookup"><span data-stu-id="55f86-146">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="55f86-147">Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="55f86-147">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="55f86-148">Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure.</span><span class="sxs-lookup"><span data-stu-id="55f86-148">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="55f86-149">Permite alterar a URL para usar contas de armazenamento de blobs não públicos.</span><span class="sxs-lookup"><span data-stu-id="55f86-149">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="55f86-150">Imprime a ajuda do script.</span><span class="sxs-lookup"><span data-stu-id="55f86-150">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="55f86-151">Especifica o caminho da instalação.</span><span class="sxs-lookup"><span data-stu-id="55f86-151">Specifies the installation path.</span></span> <span data-ttu-id="55f86-152">O diretório será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="55f86-152">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="55f86-153">O valor padrão é *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="55f86-153">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="55f86-154">Os binários são colocados diretamente nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="55f86-154">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="55f86-155">Especifica um caminho para um arquivo [global.json](global-json.md) que será usado para determinar a versão SDK.</span><span class="sxs-lookup"><span data-stu-id="55f86-155">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="55f86-156">O arquivo *global.json* deve `sdk:version`ter um valor para .</span><span class="sxs-lookup"><span data-stu-id="55f86-156">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="55f86-157">Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.</span><span class="sxs-lookup"><span data-stu-id="55f86-157">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="55f86-158">Se definida, a pasta de instalação não será exportada para o caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="55f86-158">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="55f86-159">Por padrão, o script modifica o PATH, que disponibiliza o .NET Core CLI imediatamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="55f86-159">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="55f86-160">Se for definido, o instalador usará o proxy ao fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="55f86-160">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="55f86-161">(Válido apenas para Windows.)</span><span class="sxs-lookup"><span data-stu-id="55f86-161">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="55f86-162">Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy.</span><span class="sxs-lookup"><span data-stu-id="55f86-162">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="55f86-163">(Válido apenas para Windows.)</span><span class="sxs-lookup"><span data-stu-id="55f86-163">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="55f86-164">Instala apenas o runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="55f86-164">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="55f86-165">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="55f86-165">The possible values are:</span></span>

  - <span data-ttu-id="55f86-166">`dotnet`: o runtime compartilhado `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="55f86-166">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="55f86-167">`aspnetcore`: o runtime compartilhado `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="55f86-167">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="55f86-168">`windowsdesktop`: o runtime compartilhado `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="55f86-168">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="55f86-169">Especifica o [identificador de tempo de execução](../rid-catalog.md) para o qual as ferramentas estão sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="55f86-169">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="55f86-170">Use `linux-x64` para Linux portátil.</span><span class="sxs-lookup"><span data-stu-id="55f86-170">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="55f86-171">(Válido apenas para Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="55f86-171">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="55f86-172">Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script.</span><span class="sxs-lookup"><span data-stu-id="55f86-172">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="55f86-173">A alternativa recomendada é a opção `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="55f86-173">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="55f86-174">Instala apenas os bits de runtime compartilhado, não todo o SDK.</span><span class="sxs-lookup"><span data-stu-id="55f86-174">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="55f86-175">Esta opção é equivalente `-Runtime|--runtime dotnet`a especificar .</span><span class="sxs-lookup"><span data-stu-id="55f86-175">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="55f86-176">Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.</span><span class="sxs-lookup"><span data-stu-id="55f86-176">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="55f86-177">Permite alterar a URL do feed não armazenado em cache usado por esse instalador.</span><span class="sxs-lookup"><span data-stu-id="55f86-177">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="55f86-178">Não recomendamos alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="55f86-178">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="55f86-179">Exibe informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="55f86-179">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="55f86-180">Representa uma versão específica do build.</span><span class="sxs-lookup"><span data-stu-id="55f86-180">Represents a specific build version.</span></span> <span data-ttu-id="55f86-181">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="55f86-181">The possible values are:</span></span>

  - <span data-ttu-id="55f86-182">`latest`: build mais recente no canal (usado com a opção `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="55f86-182">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="55f86-183">`coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).</span><span class="sxs-lookup"><span data-stu-id="55f86-183">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="55f86-184">Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="55f86-184">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="55f86-185">Por exemplo: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="55f86-185">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="55f86-186">Se não for especificada, a `-Version` assumirá o padrão `latest`.</span><span class="sxs-lookup"><span data-stu-id="55f86-186">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="55f86-187">Exemplos</span><span class="sxs-lookup"><span data-stu-id="55f86-187">Examples</span></span>

- <span data-ttu-id="55f86-188">Instale a versão LTS (suportada a longo prazo) no local padrão:</span><span class="sxs-lookup"><span data-stu-id="55f86-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="55f86-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="55f86-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="55f86-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="55f86-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="55f86-191">Instale a versão mais recente do canal 3.1 para o local especificado:</span><span class="sxs-lookup"><span data-stu-id="55f86-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="55f86-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="55f86-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="55f86-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="55f86-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="55f86-194">Instale a versão 3.0.0 do tempo de execução compartilhado:</span><span class="sxs-lookup"><span data-stu-id="55f86-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="55f86-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="55f86-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="55f86-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="55f86-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="55f86-197">Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):</span><span class="sxs-lookup"><span data-stu-id="55f86-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="55f86-198">Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="55f86-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="55f86-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="55f86-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="55f86-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="55f86-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="55f86-201">Confira também</span><span class="sxs-lookup"><span data-stu-id="55f86-201">See also</span></span>

- [<span data-ttu-id="55f86-202">Versões do .NET Core</span><span class="sxs-lookup"><span data-stu-id="55f86-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="55f86-203">Arquivo de download de runtime e SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="55f86-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
