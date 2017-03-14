---
title: Comando dotnet-build | Microsoft Docs
description: "O comando dotnet-build compila um projeto e todas as suas dependências."
keywords: dotnet-build, CLI, comando de CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 17c2db54f871795c370a6475c21e36736a6b46c3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>Nome

`dotnet-build` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

```
dotnet build [project] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity]
dotnet build [--help]
```

## <a name="description"></a>Descrição
O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários. Os binários são os arquivos de símbolo usados para depuração (que têm uma extensão `*.pdb`), bem como o código do projeto na IL (Linguagem Intermediária) com uma extensão `*.dll`. Além disso, será produzido um arquivo JSON que lista as dependências do aplicativo com a extensão `*.deps.json`. Por fim, um arquivo `runtime.config.json` também será produzido. Esse arquivo especifica em qual tempo de execução compartilhado e versão o código compilado será executado. 

Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto. Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução. Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produzirá uma saída que é possível executar em qualquer computador que tem o .NET Framework instalado. Para obter uma experiência semelhante no .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md). Mais informações sobre isso podem ser encontradas no documento [Implantação de aplicativos .NET Core](../deploying/index.md). 

Compilar exige a existência de um arquivo *assets.json* (um arquivo que lista todas as dependências do aplicativo), o que significa que é necessário executar [`dotnet restore`](dotnet-restore.md) antes de compilar o projeto. A ausência do arquivo de ativos se manifesta como a incapacidade das ferramentas de resolver assemblies de referência que resultarão em erros. 

O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais. Consulte a [documentação do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild) para obter mais informações sobre esses tópicos. 

Além de suas opções, o comando `dotnet build` também aceitará opções do MSBuild, como `/p` para configurar propriedades ou `/l` para definir um agente. É possível encontrar mais informações sobre essas opções na documentação dos comandos [`dotnet msbuild`](dotnet-msbuild.md). Se desejar saber quando 

O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto. O seguinte exemplo mostra um projeto que produzirá um código executável: 


```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Para produzir uma biblioteca, basta omitir essa propriedade. A principal diferença na saída é que a DLL da IL de uma biblioteca não conterá nenhum ponto de entrada e não será possível executá-la. 

## <a name="arguments"></a>Arguments

`project`

O arquivo de projeto a ser compilado.
Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em `proj` e que usa esse arquivo.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção.

`-f|--framework <FRAMEWORK>`

Compila para uma estrutura específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`-c|--configuration [Debug|Release]`

Define uma configuração de build. Se omitido, o padrão é `Debug`.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Tempo de execução de destino para a compilação. Para obter uma lista de RIDs (Identificadores de Tempo de Execução) que podem ser usados, consulte o [Catálogo de RIDs](../rid-catalog.md).

`--version-suffix [VERSION_SUFFIX]`

Define qual `*` deve ser substituído no campo de versão no arquivo de projeto. O formato segue as diretrizes de versão do NuGet.

`--no-incremental`

Marca o build como não segura para build incremental. Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.

`--no-dependencies`

Ignora as referências projeto a projeto e só compila o projeto raiz especificado para build.

`-v|--verbosity`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet build`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet build --configuration Release`

Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`
