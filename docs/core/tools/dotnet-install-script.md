---
title: Scripts dotnet-install
description: Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: ea14424297dcf1dab8711197bee1d3b3e19879c1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837070"
---
# <a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome

`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.

## <a name="synopsis"></a>Sinopse

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Descrição

O scripts `dotnet-install` são usados para executar uma instalação não administrativa do SDK do .NET Core, que inclui as ferramentas de CLI e o tempo de execução compartilhado do .NET Core.

É recomendável usar a versão estável que está hospedada no [site principal do .NET Core](https://dot.net). Os caminhos diretos para os scripts são:

* <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)

A principal utilidade desses scripts é para cenários de automação e instalações não administrativas. Há dois scripts: um é um script do PowerShell que funciona no Windows. O outro script é um script de bash que funciona em Linux/macOS. Ambos os scripts têm o mesmo comportamento. O script de bash também lê comutadores do PowerShell. Portanto, você pode usar comutadores do PowerShell com o script nos sistemas Linux/macOS.

Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`. Por padrão, os scripts de instalação baixam o SDK e o instalam. Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`.

Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual. Substitua esse comportamento padrão especificando o argumento `--no-path`.

Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

Você pode instalar uma versão específica usando o argumento `--version`. A versão deve ser especificada como uma versão de terceiros (por exemplo, 1.0.0-13232). Se omitida, será usada a versão `latest`.

## <a name="options"></a>Opções

`-Channel <CHANNEL>`

Especifica o canal de origem da instalação. Os valores possíveis são:

- `Current` – versão atual
- `LTS` – canal de suporte de longo prazo (versão atual com suporte)
- Versão de duas partes no formato X.Y que representa uma versão específica (por exemplo, `2.0` ou `1.0`)
- O nome do branch [por exemplo, `release/2.0.0`, `release/2.0.0-preview2` ou `master` para a versão mais recente do branch `master` (versões noturnas "mais avançadas")]

O valor padrão é `LTS`. Para saber mais sobre os canais de suporte do .NET, veja o tópico [Ciclo de vida de suporte do .NET Core](https://www.microsoft.com/net/core/support).

`-Version <VERSION>`

Representa uma versão específica do build. Os valores possíveis são:

- `latest` – build mais recente no canal (usado com a opção `-Channel`)
- `coherent` – build coerente mais recente no canal; usa a última combinação de pacotes estáveis (usado com as opções `-Channel` do nome do Branch)
- Versão de três partes no formato X.Y.Z que representa uma determinada versão do build; substitui a opção `-Channel`. Por exemplo: `2.0.0-preview2-006120`

Se omitida, `-Version` será padronizada para `latest`.

`-InstallDir <DIRECTORY>`

Especifica o caminho da instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\.dotnet*. Observe que os binários são colocados diretamente no diretório.

`-Architecture <ARCHITECTURE>`

Arquitetura dos binários do .NET Core para instalação. Os valores possíveis são `auto`, `x64` e `x86`. O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.

`-SharedRuntime`

Se for definida, essa opção limitará a instalação para o tempo de execução compartilhado. Não ocorre a instalação completa do SDK.

`-DryRun`

Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET Core. Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build. Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

`-NoPath`

Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual. Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

`-AzureFeed`

Especifica a URL para o feed do Azure para o instalador. Não recomendamos a alteração desse valor. O padrão é `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Se for definido, o instalador usará o proxy ao fazer solicitações da Web. (Válido somente para Windows)

`--verbose`

Exiba informações de diagnóstico.

`--help`

Imprime a ajuda do script.

## <a name="examples"></a>Exemplos

Instale a versão LTS (suportada a longo prazo) no local padrão:

Windows:

`./dotnet-install.ps1 -Channel LTS`

macOS/Linux:

`./dotnet-install.sh --channel LTS`

Instale a visualização mais recente do canal 2.0 no local especificado:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Instale a versão 1.1.0 do tempo de execução compartilhado:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Obtenha o script e instale exemplos de uma linha da CLI do .NET Core:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Consulte também

* [Versões do .NET Core](https://github.com/dotnet/core/releases)
* [Arquivo de download de tempo de execução e SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
