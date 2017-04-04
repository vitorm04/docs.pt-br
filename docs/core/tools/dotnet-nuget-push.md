---
title: Comando dotnet-nuget-push - CLI do .NET Core | Microsoft Docs
description: O comando dotnet-nuget-push envia um pacote ao servidor e os publica.
keywords: dotnet-nuget-push, CLI, comando da CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 51ecf4b8f26fa7722103065bc060e6ea708d147c
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-nuget-push"></a>dotnet-nuget push

## <a name="name"></a>Nome

`dotnet-nuget push` – Envia um pacote ao servidor e os publica.

## <a name="synopsis"></a>Sinopse

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet nuget push` envia um pacote ao servidor e os publica. O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração. Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior). A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.

## <a name="arguments"></a>Arguments

`ROOT`

Especifique o caminho até o pacote e sua chave de API para enviar o pacote por push para o servidor.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-s|--source <SOURCE>`

Especifica a URL do servidor. Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.

`--symbols-source <SOURCE>`

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

Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão, com detalhamento máximo:

`dotnet nuget push *.nupkg --verbosity detailed`

