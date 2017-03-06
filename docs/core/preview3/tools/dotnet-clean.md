---
title: Comando dotnet-clean | Microsoft Docs
description: "O comando dotnet-clean limpa o diretório atual."
keywords: dotnet-clean, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 01/31/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 12144def2095246bb6611522b3dbc2d7e441135a

---

#<a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nome 
`dotnet-clean` -- limpa a saída de um projeto. 

## <a name="synopsis"></a>Sinopse

`dotnet clean [--help] [--output]  [--framework]  
    [--configuration]  [--verbosity]
    [<project>]`

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

`-v|--verbosity [Quiet|Minimal|Normal|Diag]`

Define o detalhamento a ser usado para invocar o comando `dotnet clean`. Os níveis de detalhamento são os [níveis de detalhamento do MSBuild](https://msdn.microsoft.com/en-us/library/ms164311.aspx) padrão. 


## <a name="examples"></a>Exemplos

Limpe uma compilação padrão do projeto:

`dotnet clean`

Limpe um projeto compilado usando a configuração da Versão:

`dotnet clean --configuration Release`



<!--HONumber=Feb17_HO2-->


