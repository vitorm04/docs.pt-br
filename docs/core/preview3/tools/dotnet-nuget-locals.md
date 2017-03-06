---
title: Comando dotnet-nuget-locals | Microsoft Docs
description: "O comando nuget-dotnet-locais limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador."
keywords: dotnet-nuget-locals, CLI, comando da CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 11/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 5f8c3be091b515553eb0db0ccfaee6bb8c620cff
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-nuget-locals"></a>dotnet-nuget-locals

[!INCLUDE[preview-warning](../../../includes/warning.md)] 

## <a name="name"></a>Nome 
`dotnet-nuget-locals` – Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador. 

## <a name="synopsis"></a>Sinopse

`dotnet nuget locals <cache_location> [--clear|--list] [--help] [--force-english-output]`

em que `<cache_location>` é um dos valores a seguir: `all`, `http-cache`, `packages-cache`, `global-packages` ou `temp`.

## <a name="description"></a>Descrição

O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.

## <a name="arguments"></a>Arguments

`all`

Indica que a operação especificada deve ser aplicada a todos os tipos cache, ou seja, o cache de solicitação http, cache de pacotes globais e cache temporário.

`http-cache`

Indica que a operação especificada deve ser aplicada apenas ao cache de solicitação de http. Outros locais de cache não são afetados.

`global-packages`

Indica que a operação especificada deve ser aplicada apenas ao cache de pacotes globais. Outros locais de cache não são afetados.

`temp`

Indica que a operação especificada deve ser aplicada apenas ao cache temporário. Outros locais de cache não são afetados.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-c|--clear`

A opção limpar é usada para executar uma operação de limpeza no tipo de cache especificado. O conteúdo dos diretórios de cache é excluído recursivamente. O usuário/grupo que o executa deve ter permissão para os arquivos nos diretórios de cache para que a operação seja bem-sucedida. Se não, um erro será exibido indicando que os arquivos/pastas que não foram limpos.

`-l|--list`

A opção de lista é usada para exibir a localização do tipo de cache especificado. 

`--force-english-output`

Faz com que a saída de linha de comando esteja em inglês.

## <a name="examples"></a>Exemplos

Exibe os caminhos de todos os diretórios de cache local, isto é, diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário.

`dotnet nuget locals –l all`

Exibe o caminho para o diretório local do cache de http:

`dotnet nuget locals --list http-cache`

Limpa todos os arquivos em de todos os diretórios de cache local, isto é, o diretório de cache de http, o diretório de cache de pacotes globais e o diretório de cache temporário.

`dotnet nuget locals --clear all`

Limpa todos os arquivos no diretório local de cache de pacotes globais:

`dotnet nuget locals -c global-packages`

Limpa todos os arquivos no diretório local de cache temporário:

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Solução de problemas

Para obter informações sobre os problemas e erros mais comuns ao usar o comando `dotnet-nuget-locals`, consulte [Gerenciamento do cache do NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache).

