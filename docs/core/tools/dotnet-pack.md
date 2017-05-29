---
title: Comando dotnet-pack - CLI do .NET Core | Microsoft Docs
description: O comando dotnet-pack cria pacotes NuGet para seu projeto .NET Core.
keywords: dotnet-pack, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
ms.translationtype: Human Translation
ms.sourcegitcommit: 14c2e01ab0c30c9f1cbfdcc53ea85fe51a4d8c2e
ms.openlocfilehash: 5a2ea69825fa336b1d8ce2283e214d02c16347e3
ms.contentlocale: pt-br
ms.lasthandoff: 05/01/2017

---

# <a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>Nome

`dotnet-pack` – Empacota o código em um pacote NuGet.

## <a name="synopsis"></a>Sinopse

`dotnet pack [<PROJECT>] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix <VERSION_SUFFIX>] [-s|--serviceable] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado desse comando é um pacote do NuGet. Se a opção `--include-symbols` estiver presente, outro pacote que contém os símbolos de depuração será criado. 

As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado. As referências de projeto a projeto não são empacotadas dentro do projeto. No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.

Por padrão, `dotnet pack` compila primeiro o projeto. Se você quiser evitar esse comportamento, passe a opção `--no-build`. Com frequência, isso é útil em cenários de criação de CI (Integração Contínua) nos quais você sabe que o código foi compilado anteriormente.

Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento. Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="arguments"></a>Arguments

`PROJECT` 
    
O projeto a ser empacotado. Pode ser um caminho para um [arquivo csproj](csproj.md) ou para um diretório. Se for omitido, o padrão será o diretório atual. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-o|--output <OUTPUT_DIRECTORY>`

Coloca os pacotes compilados no diretório especificado. 

`--no-build`

Não compile o projeto antes do empacotamento. 

`--include-symbols`

Gera os símbolos `nupkg`. 

`--include-source`

Inclui os arquivos de origem no pacote do NuGet. Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`. 

`-c|--configuration <CONFIGURATION>`

Configuração a ser usada ao compilar o projeto. Se não for especificado, a configuração assumirá o padrão de `Debug`.

`--version-suffix <VERSION_SUFFIX>`

Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.

`-s|--serviceable`

Define o sinalizador operacional no pacote. Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).

`--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Empacota o projeto no diretório atual:

`dotnet pack`

Empacote o projeto `app1`:

`dotnet pack ~/projects/app1/project.csproj`
    
Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:

`dotnet pack --output nupkgs`

Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:

`dotnet pack --no-build --output nupkgs`

Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:

`dotnet pack --version-suffix "ci-1234"`

Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:

`dotnet pack /p:PackageVersion=2.1.0`

