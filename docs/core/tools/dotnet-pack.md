---
title: Comando dotnet-pack | Microsoft Docs
description: O comando dotnet-pack cria pacotes NuGet para seu projeto .NET Core.
keywords: dotnet-pack, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 88289a09a22bf20ec9089ec6a74269cd682a305b
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>Nome

`dotnet-pack` – Empacota o código em um pacote NuGet.

## <a name="synopsis"></a>Sinopse

```
dotnet pack [project] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix] [-s|--serviceable] [-v|--verbosity]
dotnet pack [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado desse comando é um pacote do NuGet. Se a opção `--include-symbols` estiver presente, outro pacote que contém os símbolos de depuração será criado. 

As dependências do NuGet do projeto que está sendo empacotado são adicionadas ao arquivo `nuspec` para que possam ser resolvidas quando o pacote for instalado. Referências de projeto a projeto não são empacotadas dentro do projeto. No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.

`dotnet pack` compila primeiro o projeto por padrão. Se você quiser evitar isso, passe a opção `--no-build`. Isso pode ser útil em cenários de build de CI (Integração Contínua) em que você sabe que o código acabou de ser criado anteriormente, por exemplo. 

## <a name="arguments"></a>Arguments

`project` 
    
O projeto a ser empacotado. Ele pode ser um caminho para um [arquivo csproj](csproj.md) ou para um diretório. Se omitido, o padrão será o diretório atual. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-o|--output <OUTPUT_DIRECTORY>`

Coloca os pacotes compilados no diretório especificado. 

`--no-build`

Não compila o projeto antes do empacotamento. 

`--include-symbols`

Gera os símbolos nupkg. 

`--include-source`

Inclui os arquivos de origem no pacote do NuGet. Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`. 

`-c|--configuration <Debug|Release>`

Configuração a ser usada ao compilar o projeto. Se não for especificado, o padrão será `Debug`.

`--version-suffix <VERSION_SUFFIX>`

Define o valor da propriedade $(VersionSuffix) do MSBuild no projeto.

`-s|--serviceable`

Define o sinalizador operacional no pacote. Para obter mais informações, consulte https://aka.ms/nupkgservicing.

`--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Empacota o projeto no diretório atual:

`dotnet pack`

Empacote o projeto app1:

`dotnet pack ~/projects/app1/project.csproj`
    
Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta especificada:

`dotnet pack --output nupkgs`

Empacote o projeto no diretório atual para a pasta especificada e ignore a etapa de build:

`dotnet pack --no-build --output nupkgs`

Empacote o projeto atual e atualize a versão do pacote resultante com o sufixo fornecido. O sufixo de versão do projeto é configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*.

`dotnet pack --version-suffix "ci-1234"`
