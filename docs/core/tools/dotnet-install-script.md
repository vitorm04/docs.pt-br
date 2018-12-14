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
# <a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome

`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.

## <a name="synopsis"></a>Sinopse

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Descrição

O scripts `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.

É recomendável usar a versão estável que está hospedada no [site principal do .NET Core](https://dot.net). Os caminhos diretos para os scripts são:

* <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)

A principal utilidade desses scripts é para cenários de automação e instalações não administrativas. Há dois scripts, um do PowerShell que funciona no Windows e um script bash que funciona no Linux/macOS. Ambos os scripts têm o mesmo comportamento. O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.

Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`. Por padrão, os scripts de instalação baixam o SDK e o instalam. Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`.

Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual. Substitua esse comportamento padrão especificando o argumento `--no-path`.

Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

Você pode instalar uma versão específica usando o argumento `--version`. A versão deve ser especificada como uma versão de três partes (por exemplo, 1.0.0-13232). Se não for fornecida, será usada a versão `latest`.

## <a name="options"></a>Opções

* **`-Channel <CHANNEL>`**

  Especifica o canal de origem da instalação. Os valores possíveis são:

  * `Current`: versão mais atual.
  * `LTS`: canal de suporte de longo prazo (versão mais atual compatível).
  * Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.0` ou `1.0`).
  * Nome do branch. Por exemplo, `release/2.0.0`, `release/2.0.0-preview2` ou `master` (para versões noturnas).

  O valor padrão é `LTS`. Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core).

* **`-Version <VERSION>`**

  Representa uma versão específica do build. Os valores possíveis são:

  * `latest`: build mais recente no canal (usado com a opção `-Channel`).
  * `coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).
  * Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`. Por exemplo: `2.0.0-preview2-006120`.

  Se não for especificada, a `-Version` assumirá o padrão `latest`.

* **`-InstallDir <DIRECTORY>`**

  Especifica o caminho da instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\Microsoft\dotnet*. Os binários são colocados diretamente nesse diretório.

* **`-Architecture <ARCHITECTURE>`**

  Arquitetura dos binários do .NET Core para instalação. Os valores possíveis são `auto`, `x64` e `x86`. O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.

* **`-SharedRuntime`**

  > [!NOTE]
  > Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script. A alternativa recomendada é a opção `Runtime`.

  Instala apenas os bits de tempo de execução compartilhado, não todo o SDK. Isso é equivalente a especificar `-Runtime dotnet`.

* **`-Runtime <RUNTIME>`**

  Instala apenas o tempo de execução compartilhado, não todo o SDK. Os valores possíveis são:

  * `dotnet`: o tempo de execução compartilhado `Microsoft.NETCore.App`.
  * `aspnetcore`: o tempo de execução compartilhado `Microsoft.AspNetCore.App`.

* **`-DryRun`**

  Se definido, o script não executará a instalação. Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core. Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build. Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

* **`-NoPath`**

  Se definida, a pasta de instalação não será exportada para o caminho da sessão atual. Por padrão, o script modifica o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

* **`-Verbose`**

  Exibe informações de diagnóstico.

* **`-AzureFeed`**

  Especifica a URL para o feed do Azure para o instalador. Não recomendamos alterar esse valor. O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.

* **`-UncachedFeed`**

  Permite alterar a URL do feed não armazenado em cache usado por esse instalador. Não recomendamos alterar esse valor.

* **`-NoCdn`**

  Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.

* **`-FeedCredential`**

  Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure. Permite alterar a URL para usar contas de armazenamento de blobs não públicos.

* **`-ProxyAddress`**

  Se for definido, o instalador usará o proxy ao fazer solicitações da Web. (Válido somente para Windows)

* **`ProxyUseDefaultCredentials`**

  Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy. (Válido somente para Windows)

* **`-SkipNonVersionedFiles`**

  Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.

* **`-Help`**

  Imprime a ajuda do script.

## <a name="examples"></a>Exemplos

* Instale a versão LTS (suportada a longo prazo) no local padrão:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* Instale a visualização mais recente do canal 2.0 no local especificado:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* Instale a versão 1.1.0 do tempo de execução compartilhado:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:

  Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Consulte também

* [Versões do .NET Core](https://github.com/dotnet/core/releases)
* [Arquivo de download de tempo de execução e SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
