---
title: Scripts dotnet-install | Microsoft Docs
description: "Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado."
keywords: dotnet-install, dotnet-install scripts, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 99254f84873003496ee00214d55ff908f9fd47d3
ms.openlocfilehash: 6301fb61be27d7dac6ead57159c0d9461b3eacb5
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome

`dotnet-install.ps1` | `dotnet-install.sh` – script usado para instalar as ferramentas da CLI (Interface de Linha de Comando) e o tempo de execução compartilhado do .NET Core.

## <a name="synopsis"></a>Sinopse
Windows:

```
dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture]
    [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]
```

macOS/Linux:

```
dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
```

## <a name="description"></a>Descrição
Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. Você pode baixar os scripts do nosso [repositório GitHub da CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain). 

O caso de uso principal é ajudar em cenários de automação e instalações de não administrador. Há dois scripts, um para PowerShell que funciona no Windows e um script bash que funciona no Linux/OS X. Ambos têm o mesmo comportamento. O script bash também “conhece” comutadores do PowerShell por isso você pode usá-los em todos os segmentos. 

Os scripts de instalação baixarão o arquivo ZIP/tarball dos destinos de build da CLI e prosseguirão com a instalação no local padrão ou em um local especificado por `--install-dir`. Por padrão, o script de instalação baixará e instalará o SDK. Se você deseja obter apenas o tempo de execução compartilhado, especifique o argumento `--shared-runtime`. 

Por padrão, o script adicionará o local de instalação ao $PATH para a sessão atual. Isso pode ser substituído se o argumento `--no-path` for usado. 

Antes de executar o script, instale todas as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

Você pode instalar uma versão específica usando o argumento `--version`. A versão deve ser especificada como uma versão de 3 partes (por exemplo, 1.0.0-13232). Se for omitido, o padrão será o primeiro arquivo [global.json](global-json.md) encontrado na hierarquia acima da pasta em que o script foi invocado, o qual contém a propriedade `version`. Se isso não existir, a versão Mais Recente será usada.

Você também pode usar esse script para obter o SDK ou binários de depuração em tempo de execução compartilhado com símbolos de depuração usando o argumento `--debug`. Se você não fazer isso na primeira instalação e perceber que precisa de símbolos de depuração mais tarde, execute novamente o script com esse argumento e a versão dos bits instalada. 

## <a name="options"></a>Opções
As opções são diferentes entre implementações de script. 

### <a name="powershell-windows"></a>PowerShell (Windows)
`-Channel [CHANNEL]`

Qual canal (por exemplo, `future`, `preview`, `production`) deve ser usado para instalação. O valor padrão é `production`.

`-Version [VERSION]`

A versão da CLI a ser instalada. É necessário especificar a versão como uma versão de 3 partes (por exemplo, 1.0.0-13232). Se isso for omitido, ela usará como padrão o primeiro [global.json](global-json.md) que contém a propriedade `version`. Se isso não existir, a versão Mais Recente será usada.

`-InstallDir [DIR]`

Caminho de instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\.dotnet*.

`-Architecture [ARCH]`

Arquitetura dos binários do .NET Core a ser instalada. Os possíveis valores são &lt;auto&gt;, x64 e x86. O valor padrão é &lt;auto&gt;, que representa a arquitetura do sistema operacional em execução no momento.

`-SharedRuntime`

Se for definido, instala apenas os bits do tempo de execução compartilhado, não todo o SDK.

`-DebugSymbols`

Se for definido, o instalador incluirá símbolos de depuração na instalação.

> [!NOTE]
> Essa opção ainda não funciona.

`-DryRun`

Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET. Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.
Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

`-NoPath`

Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual. Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

`-AzureFeed`

A URL para o feed do Azure a ser usada por esse instalador. Não recomendada a alteração. O padrão é `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Se for definido, o instalador usará o proxy ao fazer solicitações da Web.

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
`

`--channel [CHANNEL]`

O canal (por exemplo “futura”, “desenvolvimento”, “produção”) do qual instalar. O valor padrão é “Produção”.

`--version [VERSION]`

A versão da CLI a ser instalada. É necessário especificar a versão como uma versão de 3 partes (por exemplo, 1.0.0-13232). Se isso for omitido, ela usará como padrão o primeiro [global.json](global-json.md) que contém a propriedade `version`. Se isso não existir, a versão Mais Recente será usada.

`--install-dir [DIR]`

Caminho de instalação. O diretório será criado se não existir. O valor padrão é `$HOME/.dotnet`.

`--architecture [ARCH]`

Arquitetura dos binários do .NET a ser instalada. Os possíveis valores são &lt;auto&gt;, x64 e amd64. O valor padrão é &lt;auto&gt;, que representa a arquitetura do sistema operacional em execução no momento.

`--shared-runtime`

Se for definido, instala apenas os bits do tempo de execução compartilhado, não todo o SDK.

`--debug-symbols`

Se for definido, o instalador incluirá símbolos de depuração na instalação.

> [!NOTE]
> Essa opção ainda não funciona.

`--dry-run`

Se for definido, o script não executará a instalação, mas exibirá qual linha de comando será usada para instalar de forma consistente a versão atualmente solicitada da CLI do .NET. Por exemplo, se você especificar a versão `latest`, ele exibirá um link com a versão específica, para que este comando possa ser usado de forma determinista em um script de build.
Ele também exibirá o local dos binários, caso você prefira instalá-lo ou baixá-lo por conta própria.

`--no-path`

Se for definido, o prefixo/installdir não será exportado para o caminho da sessão atual. Por padrão, o script modificará o PATH, o que torna as ferramentas da CLI disponíveis imediatamente após a instalação.

`--verbose`

Exiba informações de diagnóstico.

`--azure-feed`

A URL para o feed do Azure a ser usada por esse instalador. Não recomendada a alteração. O padrão é `https://dotnetcli.azureedge.net/dotnet`.

`--help`

Imprime a ajuda do script.

## <a name="examples"></a>Exemplos

Instale a versão mais recente de desenvolvimento no local padrão:

Windows:

`./dotnet-install.ps1 -Channel Future`

macOS/Linux:

`./dotnet-install.sh --channel Future`

Instale a visualização mais recente no local especificado:

Windows:

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux:

`./dotnet-install.sh --channel preview --install-dir ~/cli`
