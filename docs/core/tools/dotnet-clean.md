---
title: Comando dotnet-clean - CLI do .NET Core | Microsoft Docs
description: "O comando dotnet-clean limpa o diretório atual."
keywords: dotnet-clean, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 0bdd8b9ab133ca92e414618412d95d8136d6234a
ms.contentlocale: pt-br
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>Nome

`dotnet-clean` – limpa a saída de um projeto. 

## <a name="synopsis"></a>Sinopse

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet clean` limpará a saída da compilação anterior. Ele é implementado como um [destino de MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-targets), para que o projeto seja avaliado durante a execução do comando. Apenas as saídas criadas durante a compilação são limpas. As pastas de saídas intermediária (*obj*) e final (*bin*) serão limpas.

## <a name="arguments"></a>Arguments

`PROJECT`

O projeto do MSBuild a ser limpo. Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-o|--output <OUTPUT_DIRECTORY>`

O diretório no qual as saídas compiladas são colocadas. Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.

`-f|--framework <FRAMEWORK>`

A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação. A estrutura precisa ser definida no [arquivo de projeto](csproj.md). Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.

`-c|--configuration <CONFIGURATION>`

Define a configuração. Se omitido, o padrão é `Debug`. Essa propriedade só será exigida na limpeza se você especificá-la durante o momento de compilação.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].

## <a name="examples"></a>Exemplos

Limpe uma compilação padrão do projeto:

`dotnet clean`

Limpe um projeto compilado usando a configuração da Versão:

`dotnet clean --configuration Release`

