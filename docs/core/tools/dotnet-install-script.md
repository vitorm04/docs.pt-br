---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts de instalação dotnet para instalar o .NET Core SDK e o tempo de execução compartilhado.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092857"
---
# <a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome

`dotnet-install.ps1` | `dotnet-install.sh`- Script usado para instalar o .NET Core SDK e o tempo de execução compartilhado.

## <a name="synopsis"></a>Sinopse

Windows:

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

Linux/macOs:

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a>Descrição

Os `dotnet-install` scripts são usados para executar uma instalação não-admin do .NET Core SDK, que inclui o .NET Core CLI e o tempo de execução compartilhado.

Recomendamos que você use a versão estável dos scripts:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

A principal utilidade desses scripts é para cenários de automação e instalações não administrativas. Há dois scripts, um do PowerShell que funciona no Windows e um script bash que funciona no Linux/macOS. Ambos os scripts têm o mesmo comportamento. O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.

Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`. Por padrão, os scripts de instalação baixam o SDK e o instalam. Se você quiser obter somente o runtime compartilhado, especifique o argumento `-Runtime|--runtime`.

Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual. Substitua esse comportamento padrão especificando o argumento `-NoPath|--no-path`.

Antes de executar o script, instale as [dependências](../install/dependencies.md) necessárias.

Você pode instalar uma versão específica usando o argumento `-Version|--version`. A versão deve ser especificada como uma versão `2.1.0`de três partes (por exemplo, ). Se não for fornecida, será usada a versão `latest`.

## <a name="options"></a>Opções

- **`-Channel|--channel <CHANNEL>`**

  Especifica o canal de origem da instalação. Os valores possíveis são:

  - `Current`: versão mais atual.
  - `LTS`: canal de suporte de longo prazo (versão mais atual compatível).
  - Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.1` ou `3.0`).
  - Nome da filial: `release/3.1.1xx` `master` por exemplo, ou (para lançamentos noturnos). Use esta opção para instalar uma versão de um canal de visualização. Use o nome do canal conforme listado em [Instaladores e Binários](https://github.com/dotnet/core-sdk#installers-and-binaries).

  O valor padrão é `LTS`. Para saber mais sobre os canais de suporte do .NET, consulte a página [Política de suporte do .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

- **`-Version|--version <VERSION>`**

  Representa uma versão específica do build. Os valores possíveis são:

  - `latest`: build mais recente no canal (usado com a opção `-Channel`).
  - `coherent`: build coerente mais recente no canal; usa a combinação de pacotes estáveis mais recente (usado com as opções `-Channel` do nome do Branch).
  - Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`. Por exemplo: `2.0.0-preview2-006120`.

  Se não for especificada, a `-Version` assumirá o padrão `latest`.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Especifica um caminho para um arquivo [global.json](global-json.md) que será usado para determinar a versão SDK. O arquivo *global.json* deve `sdk:version`ter um valor para .

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Especifica o caminho da instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\Microsoft\dotnet*. Os binários são colocados diretamente nesse diretório.

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Arquitetura dos binários do .NET Core para instalação. Os valores possíveis são `<auto>`, `amd64`, `x64`, `x86`, `arm64` e `arm`. O valor padrão é `<auto>`, que representa a arquitetura do sistema operacional em execução no momento.

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Esse parâmetro está obsoleto e pode ser removido em uma versão futura do script. A alternativa recomendada é a opção `-Runtime|--runtime`.

  Instala apenas os bits de runtime compartilhado, não todo o SDK. Esta opção é equivalente `-Runtime|--runtime dotnet`a especificar .

- **`-Runtime|--runtime <RUNTIME>`**

  Instala apenas o runtime compartilhado, não todo o SDK. Os valores possíveis são:

  - `dotnet`: o runtime compartilhado `Microsoft.NETCore.App`.
  - `aspnetcore`: o runtime compartilhado `Microsoft.AspNetCore.App`.
  - `windowsdesktop`: o runtime compartilhado `Microsoft.WindowsDesktop.App`.

- **`-DryRun|--dry-run`**

  Se definido, o script não executará a instalação. Em vez disso, exibirá qual linha de comando deve ser usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core. Por exemplo, se você especificar a versão `latest`, será exibido um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build. Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

- **`-NoPath|--no-path`**

  Se definida, a pasta de instalação não será exportada para o caminho da sessão atual. Por padrão, o script modifica o PATH, que disponibiliza o .NET Core CLI imediatamente após a instalação.

- **`-Verbose|--verbose`**

  Exibe informações de diagnóstico.

- **`-AzureFeed|--azure-feed`**

  Especifica a URL para o feed do Azure para o instalador. Não recomendamos alterar esse valor. O valor padrão é `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed|--uncached-feed`**

  Permite alterar a URL do feed não armazenado em cache usado por esse instalador. Não recomendamos alterar esse valor.

- **`-NoCdn|--no-cdn`**

  Desabilita o download da [Rede de Distribuição de Conteúdo (CDN) Azure](https://docs.microsoft.com/azure/cdn/cdn-overview) e usa o feed não armazenado em cache diretamente.

- **`-FeedCredential|--feed-credential`**

  Usado como uma cadeia de caracteres de consulta para acrescentar ao feed do Azure. Permite alterar a URL para usar contas de armazenamento de blobs não públicos.

- **`--runtime-id`**

  Especifica o [identificador de tempo de execução](../rid-catalog.md) para o qual as ferramentas estão sendo instaladas. Use `linux-x64` para Linux portátil. (Válido apenas para Linux/macOS)

- **`-ProxyAddress`**

  Se for definido, o instalador usará o proxy ao fazer solicitações da Web. (Válido somente para Windows)

- **`ProxyUseDefaultCredentials`**

  Se definido, o instalador usará as credenciais do usuário atual ao usar o endereço de proxy. (Válido somente para Windows)

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Ignora a instalação de arquivos sem controle de versão, como *dotnet.exe*, se já existirem.

- **`-Help|--help`**

  Imprime a ajuda do script.

## <a name="examples"></a>Exemplos

- Instale a versão LTS (suportada a longo prazo) no local padrão:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Instale a versão mais recente do canal 3.1 para o local especificado:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Instale a versão 3.0.0 do tempo de execução compartilhado:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Obtenha o script e instale a versão 2.1.2 atrás de um proxy corporativo (somente Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:

  Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Confira também

- [Versões do .NET Core](https://github.com/dotnet/core/releases)
- [Arquivo de download de runtime e SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
