---
title: "Comando dotnet nuget push – CLI do .NET Core"
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: a0f872ae930d17638e018cdd204cc08a773a3df5
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet nuget push` – Envia um pacote ao servidor e os publica.

## <a name="synopsis"></a>Sinopse

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet nuget push` envia um pacote ao servidor e os publica. O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração. Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior). A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.

## <a name="arguments"></a>Arguments

`ROOT`

Especifica o caminho do arquivo para o pacote a ser enviado por push.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--source <SOURCE>`

Especifica a URL do servidor. Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.

`--symbol-source <SOURCE>`

Especifica a URL do servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica o tempo limite para enviar para um servidor em segundos. O padrão é 300 segundos (5 minutos). Especificar 0 (zero segundos) aplica o valor padrão.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--symbol-api-key <API_KEY>`

A chave da API para o servidor de símbolos.

`-d|--disable-buffering`

Desabilita o armazenamento em buffer ao enviar a um servidor HTTP(S) para diminuir o uso de memória.

`-n|--no-symbols`

Não envia símbolos por push (mesmo se estiver presente).

`--force-english-output`

Força todas as saídas registradas em inglês.

## <a name="examples"></a>Exemplos

Envia por push *foo.nupkg* à origem de push padrão, fornecendo uma chave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Envia por push *foo.nupkg* à origem de push personalizada `http://customsource`, fornecendo uma chave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Envia por push *foo.nupkg* à origem de push padrão:

`dotnet nuget push foo.nupkg`

Envia por push *foo.nupkg* à origem de símbolos padrão:

`dotnet nuget push foo.symbols.nupkg`

Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:

`dotnet nuget push foo.nupkg --timeout 360`

Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:

`dotnet nuget push *.nupkg`

Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão, especificando um arquivo de configuração personalizado *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
