---
title: Comando dotnet nuget locals – CLI do .NET Core
description: O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: d0c900a06b00fd5e6b7ad66527c6582483222c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.

## <a name="synopsis"></a>Sinopse

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Um dos seguintes valores:

* `all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.
* `http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http. Outros locais de cache não são afetados.
* `global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais. Outros locais de cache não são afetados.
* `temp` – Indica que a operação especificada aplica-se apenas ao cache temporário. Outros locais de cache não são afetados.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-c|--clear`

A opção clear executa uma operação de limpeza no tipo de cache especificado. O conteúdo dos diretórios de cache é excluído recursivamente. O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache. Se não tiver, um erro será exibido indicando que os arquivos/pastas que não foram limpos.

`-l|--list`

A opção de lista é usada para exibir a localização do tipo de cache especificado. 

`--force-english-output`

Força a saída da linha de comando em inglês.

## <a name="examples"></a>Exemplos

Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

`dotnet nuget locals –l all`

Exibe o caminho para o diretório local do cache de http:

`dotnet nuget locals --list http-cache`

Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

`dotnet nuget locals --clear all`

Limpa todos os arquivos no diretório local de cache de pacotes globais:

`dotnet nuget locals -c global-packages`

Limpa todos os arquivos no diretório local de cache temporário:

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Solução de problemas

Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).