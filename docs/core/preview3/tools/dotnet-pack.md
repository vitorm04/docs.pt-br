---
title: Comando dotnet-pack | Microsoft Docs
description: O comando dotnet-pack cria pacotes NuGet para seu projeto .NET Core.
keywords: dotnet-pack, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 8e266f9b34923b0ab69140d78a20afeca00e0b7c

---

#<a name="dotnet-pack-net-core-tools-rc4"></a>dotnet-pack (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [dotnet-pack](../../tools/dotnet-pack.md).

## <a name="name"></a>Nome

`dotnet-pack` – Empacota o código em um pacote NuGet.

## <a name="synopsis"></a>Sinopse

`dotnet pack [--help] [--output]  
    [--no-build] [--include-symbols]
    [--include-source] [--servicable]
    [--configuration]  [--version-suffix]
    [project]`  

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado desse comando é um pacote do NuGet. Se a opção `--include-symbols` estiver presente, outro pacote que contém os símbolos de depuração será criado. 

As dependências do NuGet do projeto que está sendo empacotado são adicionadas ao arquivo `nuspec` para que possam ser resolvidas quando o pacote for instalado. Referências de projeto a projeto não são empacotadas dentro do projeto. No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.

`dotnet pack` compila primeiro o projeto por padrão. Se você quiser evitar isso, passe a opção `--no-build`. Isso pode ser útil em cenários de build de CI (Integração Contínua) em que você sabe que o código acabou de ser criado anteriormente, por exemplo. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`[project]` 
    
O projeto a ser empacotado. Ele pode ser um caminho para um [arquivo csproj](csproj.md) ou para um diretório. Se omitido, o padrão será o diretório atual. 

`-o|--output <OUTPUT_DIRECTORY>`

Coloca os pacotes compilados no diretório especificado. 

`--no-build`

Não compila o projeto antes do empacotamento. 

`--include-source`

Inclui os arquivos de origem no pacote do NuGet. Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`. 

`--include-symbols`

Gera os símbolos nupkg. 

`-c|--configuration <Debug|Release>`

Configuração a ser usada ao compilar o projeto. Se não for especificado, o padrão será `Debug`.

`--version-suffix`

Atualiza a estrela no sufixo da versão do pacote `-*` com uma cadeia de caracteres especificada.

## <a name="examples"></a>Exemplos

Empacota o projeto no diretório atual:

`dotnet pack`

Empacote o projeto app1:

`dotnet pack ~/projects/app1/project.csproj`
    
Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta especificada:

`dotnet pack --output nupkgs`

Empacote o projeto no diretório atual para a pasta especificada e ignore a etapa de build:

`dotnet pack --no-build --output nupkgs`

Empacote o projeto atual e atualize a versão dos pacotes resultantes com o sufixo fornecido. Por exemplo, a versão `1.0.0-*` será atualizada para `1.0.0-ci-1234`.

`dotnet pack --version-suffix "ci-1234"`


<!--HONumber=Feb17_HO2-->


