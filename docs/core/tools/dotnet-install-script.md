---
title: Scripts dotnet-install | Microsoft Docs
description: "Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado."
keywords: dotnet-install, dotnet-install scripts, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 4a1f0c88fb1ccd6694f8d4f5687431646adbe000
ms.openlocfilehash: fbc1ce8d864a5c2150c61f4b8bf7cb8544921634
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome

`dotnet-install.ps1` | `dotnet-install.sh` – Script usado para instalar as ferramentas da CLI (Interface de Linha de Comando) e o tempo de execução compartilhado do .NET Core.

## <a name="synopsis"></a>Sinopse

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

## <a name="description"></a>Descrição

Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. Baixe os scripts no [repositório GitHub da CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain). 

A principal utilidade desses scripts é para cenários de automação e instalações não administrativas. Há dois scripts: um é um script do PowerShell que funciona no Windows. O outro script é um script bash que funciona no Linux/OS X. Os dois scripts têm o mesmo comportamento. O script bash também lê comutadores do PowerShell, portanto, use comutadores do PowerShell com o script nos sistemas Linux/OS X. 

Os scripts de instalação baixam o arquivo ZIP/tarball dos destinos de build da CLI e o instalam no local padrão ou em um local especificado por `-InstallDir|--install-dir`. Por padrão, os scripts de instalação baixam o SDK e o instalam. Se você quiser obter somente o tempo de execução compartilhado, especifique o argumento `--shared-runtime`. 

Por padrão, o script adiciona o local de instalação ao $PATH da sessão atual. Substitua esse comportamento padrão especificando o argumento `--no-path`. 

Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

Você pode instalar uma versão específica usando o argumento `--version`. A versão deve ser especificada como uma versão de terceiros (por exemplo, 1.0.0-13232). Se for omitido, o padrão será o primeiro arquivo [global.json](global-json.md) encontrado na hierarquia acima da pasta na qual o script foi invocado, a qual contém a propriedade `version`. Se isso não estiver presente, ele usará a versão mais recente.

Você também pode usar esse script para obter o SDK ou binários de depuração em tempo de execução compartilhado com símbolos de depuração usando o argumento `--debug`. Se você não conseguir fazer isso na primeira instalação, e perceber depois que você precisa dos símbolos de depuração, execute novamente o script com o argumento `--debug` e a versão do SDK instalado para obter os símbolos de depuração. 

## <a name="options"></a>Opções

Observação: as opções são diferentes entre implementações de script. 

### <a name="powershell-windows"></a>PowerShell (Windows)

`-Channel <CHANNEL>`

Especifica o canal de origem da instalação. Os valores são: `future`, `preview` e `production`. O valor padrão é `production`.

`-Version <VERSION>`

Especifica a versão da CLI a ser instalada. É necessário especificar a versão como uma versão de terceiros (por exemplo, 1.0.0-13232). Se isso for omitido, será usado como padrão o primeiro [global.json](global-json.md) que contém a propriedade `version`. Se isso não estiver presente, ele usará a versão mais recente.

`-InstallDir <DIRECTORY>`

Especifica o caminho da instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\.dotnet*.

`-Architecture <ARCHITECTURE>`

Arquitetura dos binários do .NET Core para instalação. Os valores possíveis são `auto`, `x64` e `x86`. O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.

`-SharedRuntime`

Se for definida, essa opção limitará a instalação para o tempo de execução compartilhado. Não ocorre a instalação completa do SDK.

`-DebugSymbols` (veja a OBSERVAÇÃO)

Se for definido, o instalador incluirá símbolos de depuração na instalação.

> [!NOTE]
> A opção `-DebugSymbols` não está disponível no momento, mas é planejada para uma versão futura.

`-DryRun`

Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET. Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build. Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

`-NoPath`

Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual. Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

`-AzureFeed`

Especifica a URL para o feed do Azure para o instalador. Não recomendamos a alteração desse valor. O padrão é `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Se for definido, o instalador usará o proxy ao fazer solicitações da Web.

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

`--channel <CHANNEL>`

Especifica o canal de origem da instalação. Os valores são: `future`, `dev` e `production`. O valor padrão é `production`.

`--version <VERSION>`

Especifica a versão da CLI a ser instalada. É necessário especificar a versão como uma versão de terceiros (por exemplo, 1.0.0-13232). Se isso for omitido, será usado como padrão o primeiro [global.json](global-json.md) que contém a propriedade `version`. Se isso não estiver presente, ele usará a versão mais recente.

`--install-dir <DIRECTORY>`

Especifica o caminho da instalação. O diretório será criado se não existir. O valor padrão é `$HOME/.dotnet`.

`--architecture <ARCHITECTURE>`

Arquitetura dos binários do .NET Core para instalação. Os valores possíveis são `auto`, `x64`e `amd64`. O valor padrão é `auto`, que representa a arquitetura do sistema operacional em execução no momento.

`--shared-runtime`

Se for definida, essa opção limitará a instalação para o tempo de execução compartilhado. Não ocorre a instalação completa do SDK.

`--debug-symbols`

Se for definido, o instalador incluirá símbolos de depuração na instalação.

> [!NOTE]
> Essa opção não está disponível no momento, mas é planejada para uma versão futura.

`--dry-run`

Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET. Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build. Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

`--no-path`

Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual. Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

`--verbose`

Exiba informações de diagnóstico.

`--azure-feed`

Especifica a URL para o feed do Azure para o instalador. Não recomendamos a alteração desse valor. O padrão é `https://dotnetcli.azureedge.net/dotnet`.

`--help`

Imprime a ajuda do script.

## <a name="examples"></a>Exemplos

Instale a versão de desenvolvimento mais recente no local padrão:

Windows:

`./dotnet-install.ps1 -Channel Future`

macOS/Linux:

`./dotnet-install.sh --channel Future`

Instale a visualização mais recente no local especificado:

Windows:

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux:

`./dotnet-install.sh --channel preview --install-dir ~/cli`
