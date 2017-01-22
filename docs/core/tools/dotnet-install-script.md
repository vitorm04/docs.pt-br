---
title: Scripts dotnet-install | SDK do .NET Core
description: "Saiba mais sobre os scripts dotnet-install para instalar as ferramentas da CLI do .NET Core e o tempo de execução compartilhado."
keywords: dotnet-install, dotnet-install scripts, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 59b9c456-2bfd-4adc-8202-a1c6a0a6c787
translationtype: Human Translation
ms.sourcegitcommit: ae23d83d5ca03d1a9a248e375bc092e0d9d0cde0
ms.openlocfilehash: d6a420fa29107952020ddfa58ce0256fd8829890

---

#<a name="dotnet-install-scripts-reference"></a>referência de scripts dotnet-install

## <a name="name"></a>Nome
`dotnet-install.ps1` | `dotnet-install.sh` – Script usado para instalar as ferramentas de CLI (Interface de Linha de Comando) e o tempo de execução compartilhado.

## <a name="synopsis"></a>Sinopse
Windows:

`dotnet-install.ps1 [-Channel] [-Version]
    [-InstallDir] [-Debug] [-NoPath] 
    [-SharedRuntime]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version]
    [--install-dir] [--debug] [--no-path] 
    [--shared-runtime]`

## <a name="description"></a>Descrição
Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. Você pode baixar os scripts do nosso [repositório GitHub da CLI](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain). 

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

Qual versão da CLI deve ser instalada. Você precisa especificar a versão de 3 partes (por exemplo, 1.0.0-13232). Se for omitido, o padrão será o primeiro [global.json](global-json.md) que contém a propriedade `version`; se isso não existir, a versão Mais Recente será usada.     

`-InstallDir [DIR]`

Caminho de instalação. O diretório será criado se não existir. O valor padrão é *%LocalAppData%\Microsoft\dotnet*.

`-Debug`

`true` para indicar que os pacotes grandes que contêm símbolos de depuração devem ser usados; caso contrário, `false`. O valor padrão é `false`.

`-NoPath`

`true` para indicar que o prefixo/installdir não são exportados para o caminho para a sessão atual; caso contrário, `false`. O valor padrão é `false`, ou seja, o PATH é modificado. Isso disponibiliza as ferramentas de CLI imediatamente após a instalação. 

`-SharedRuntime`

`true` para instalar apenas os bits de tempo de execução compartilhado; `false` para instalar todo o SDK. O valor padrão é `false`.

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)
`--channel [CHANNEL]`

Qual canal (por exemplo “futura”, “visualização”, “produção”) deve ser usado para instalação. O valor padrão é “Produção”.

`--version [VERSION]`

Qual versão da CLI deve ser instalada. Você precisa especificar a versão de 3 partes (por exemplo, 1.0.0-13232). Se for omitido, o padrão será o primeiro [global.json](global-json.md) que contém a propriedade `version`; se isso não existir, a versão Mais Recente será usada.     

`--install-dir [DIR]`

Caminho de instalação. O diretório será criado se não existir. O valor padrão é `$HOME/.dotnet`.

`--debug`

`true` para indicar que os pacotes grandes que contêm símbolos de depuração devem ser usados; caso contrário, `false`. O valor padrão é `false`.

`--no-path`

`true` para indicar que o prefixo/installdir não são exportados para o caminho para a sessão atual; caso contrário, `false`. O valor padrão é `false`, ou seja, o PATH é modificado. Isso disponibiliza as ferramentas de CLI imediatamente após a instalação.  

`--shared-runtime`

`true` para instalar apenas os bits de tempo de execução compartilhado; `false` para instalar todo o SDK. O valor padrão é `false`.

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



<!--HONumber=Jan17_HO3-->


