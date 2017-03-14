---
title: Comando dotnet-clean | Microsoft Docs
description: "O comando dotnet-clean limpa o diretório atual."
keywords: dotnet-clean, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3c00f4616932318b5dc5d77cbdf6c645696a4226
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>Nome

`dotnet-clean` – limpa a saída de um projeto. 

## <a name="synopsis"></a>Sinopse

```
dotnet clean [project] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity]
dotnet clean [--help] 
```

## <a name="description"></a>Descrição

O comando `dotnet clean` limpará a saída da compilação anterior. Ele é implementado como um destino de MSBuild, para que o projeto seja avaliado. Apenas as saídas que foram criadas durante a compilação serão limpas. As pastas de saídas intermediária (`obj`) e final (`bin`) serão limpas. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-o|--output <OUTPUT_DIRECTORY>`

O diretório no qual os binários compilados foram colocados. Você também precisa definir `--framework` ao especificar essa opção. Se você não especificar essa propriedade durante o momento da compilação, você não precisa especificá-la para limpeza.

`-f|--framework <FRAMEWORK>`

A estrutura que foi especificada no momento da compilação. Se você não especificar essa propriedade durante o momento da compilação, você não precisa especificá-la para limpeza. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`-c|--configuration [Debug|Release]`

Define uma configuração em que a compilação estava sendo executada.  Se omitido, o padrão é `Debug`. Se você não especificar essa propriedade durante o momento da compilação, você não precisa especificá-la para limpeza.

`-v|--verbosity <Quiet|Minimal|Normal|Diag>`

Define o detalhamento a ser usado para invocar o comando `dotnet clean`. Os níveis de detalhamento são os [níveis de detalhamento do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) padrão. 

## <a name="examples"></a>Exemplos

Limpe uma compilação padrão do projeto:

`dotnet clean`

Limpe um projeto compilado usando a configuração da Versão:

`dotnet clean --configuration Release`

