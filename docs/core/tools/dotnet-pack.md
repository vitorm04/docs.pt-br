---
title: Comando dotnet-pack | SDK do .NET Core
description: O comando dotnet-pack cria pacotes NuGet para seu projeto .NET Core.
keywords: dotnet-pack, CLI, comando da CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8b4b8cef-f56c-4a10-aa01-fde8bfaae53e
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: e83c8ad302590bcd77129c3ff325e498da751e69

---

#<a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>Nome

`dotnet-pack` – Empacota o código em um pacote NuGet

## <a name="synopsis"></a>Sinopse

`dotnet pack [--help] [--output]  
    [--no-build] [--build-base-path]  
    [--configuration]  [--version-suffix]
    [project]`  

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado dessa operação são dois pacotes com a extensão `nupkg`. Um pacote contém o código e o outro contém os símbolos de depuração. 

As dependências do NuGet do projeto que está sendo empacotado são adicionadas ao arquivo nuspec para que possam ser resolvidas quando o pacote for instalado. Referências de projeto a projeto não são empacotadas dentro do projeto. No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.

`dotnet pack` compila primeiro o projeto por padrão. Se você quiser evitar isso, passe a opção `--no-build`. Isso pode ser útil em cenários de build de CI (Integração Contínua) em que você sabe que o código acabou de ser criado anteriormente, por exemplo. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`[project]` 
    
O projeto a ser empacotado. Ele pode ser um caminho para um arquivo [project.json](project-json.md) ou para um diretório. Se omitido, o padrão será o diretório atual. 

`-o|--output <OUTPUT_DIRECTORY>`

Coloca os pacotes compilados no diretório especificado. 

`--no-build`

Não compila o projeto antes do empacotamento. 

`--build-base-path`

Coloca os artefatos de build temporários no diretório especificado. Por padrão, eles vão para o diretório `obj` no diretório atual. 

`-c|--configuration <Debug|Release>`

Configuração a ser usada ao compilar o projeto. Se não for especificado, o padrão será `Debug`.

`--version-suffix`

Atualiza a estrela no sufixo da versão do pacote `-*` com uma cadeia de caracteres especificada.

## <a name="examples"></a>Exemplos

Empacota o projeto no diretório atual:

`dotnet pack`

Empacote o projeto app1:

`dotnet pack ~/projects/app1/project.json`
    
Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta especificada:

`dotnet pack --output nupkgs`

Empacote o projeto no diretório atual para a pasta especificada e ignore a etapa de build:

`dotnet pack --no-build --output nupkgs`

Empacote o projeto atual e atualize a versão dos pacotes resultantes com o sufixo fornecido. Por exemplo, a versão `1.0.0-*` será atualizada para `1.0.0-ci-1234`.

`dotnet pack --version-suffix "ci-1234"`


<!--HONumber=Nov16_HO1-->


