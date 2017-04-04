---
title: Comando dotnet-publish - CLI do .NET Core | Microsoft Docs
description: "O comando dotnet-publish publica seu projeto .NET Core em um diretório."
keywords: dotnet-publish, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 48bfe6c77ee6c5d905069f47da5512ac63a24b2a
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Nome

`dotnet-publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.

## <a name="synopsis"></a>Sinopse

`dotnet publish [<PROJECT>] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório. A saída conterá o seguinte:

* Código IL (Linguagem Intermediária) em um assembly com uma extensão `*.dll`.
* Arquivo *\*deps.json* que contém todas as dependências do projeto.
* Arquivo *\*.runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).
* As dependências do aplicativo. Elas são copiadas do cache NuGet para a pasta de saída.

A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, PC, Mac, laptop) para execução, e é a única maneira com suporte oficial para preparar o aplicativo para implantação. Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado. Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md). Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](https://docs.microsoft.com/en-us/aspnet/core/hosting/directory-structure).

## <a name="arguments"></a>Arguments

`PROJECT` 

O projeto a ser publicado, cujo padrão será o diretório atual se não for especificado. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-f|--framework <FRAMEWORK>`

Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada. Especifique a estrutura de destino no arquivo de projeto.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publica o aplicativo para um determinado tempo de execução. Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd). Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md). O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).

`-o|--output <OUTPUT_DIRECTORY>`

Especifica o caminho para o diretório de saída. Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.

`-c|--configuration <CONFIGURATION>`

Configuração a ser usada ao compilar o projeto. O valor padrão é `Debug`.

`--version-suffix <VERSION_SUFFIX>`

Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Publique o projeto no diretório atual:

`dotnet publish`

Publicar o aplicativo usando o arquivo de projeto especificado:

`dotnet publish ~/projects/app1/app1.csproj`
    
Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:

`dotnet publish --framework netcoreapp1.1`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>Consulte também

* [Estruturas de destino](../../standard/frameworks.md)
* [Catálogo de RID (Identificador de Tempo de Execução)](../rid-catalog.md)
