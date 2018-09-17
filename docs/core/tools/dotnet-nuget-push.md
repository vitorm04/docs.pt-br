---
title: Comando dotnet nuget push – CLI do .NET Core
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609972"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet nuget push` – Envia um pacote ao servidor e os publica.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet nuget push` envia um pacote ao servidor e os publica. O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração. Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior). A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.

## <a name="arguments"></a>Arguments

`ROOT`

Especifica o caminho do arquivo para o pacote a ser enviado por push.

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.

`--force-english-output`

Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`-n|--no-symbols`

Não envia símbolos por push (mesmo se estiver presente).

`--no-service-endpoint`

Não acrescenta "api/v2/package" à URL de origem.

`-s|--source <SOURCE>`

Especifica a URL do servidor. Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.

`-sk|--symbol-api-key <API_KEY>`

A chave da API para o servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica a URL do servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica o tempo limite para enviar para um servidor em segundos. O padrão é 300 segundos (5 minutos). Especificar 0 (zero segundos) aplica o valor padrão.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.

`--force-english-output`

Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`-n|--no-symbols`

Não envia símbolos por push (mesmo se estiver presente).

`-s|--source <SOURCE>`

Especifica a URL do servidor. Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.

`-sk|--symbol-api-key <API_KEY>`

A chave da API para o servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica a URL do servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica o tempo limite para enviar para um servidor em segundos. O padrão é 300 segundos (5 minutos). Especificar 0 (zero segundos) aplica o valor padrão.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.

`--force-english-output`

Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`-n|--no-symbols`

Não envia símbolos por push (mesmo se estiver presente).

`-s|--source <SOURCE>`

Especifica a URL do servidor. Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.

`-sk|--symbol-api-key <API_KEY>`

A chave da API para o servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica a URL do servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica o tempo limite para enviar para um servidor em segundos. O padrão é 300 segundos (5 minutos). Especificar 0 (zero segundos) aplica o valor padrão.

---

## <a name="examples"></a>Exemplos

Envia por push *foo.nupkg* à origem de push padrão, especificando uma chave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Envia por push *foo.nupkg* à `http://customsource` de origem de push personalizada, especificando uma chave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Envia por push *foo.nupkg* à origem de push padrão:

`dotnet nuget push foo.nupkg`

Envia por push *foo.nupkg* à origem de símbolos padrão:

`dotnet nuget push foo.symbols.nupkg`

Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:

`dotnet nuget push foo.nupkg --timeout 360`

Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:

`dotnet nuget push *.nupkg`
