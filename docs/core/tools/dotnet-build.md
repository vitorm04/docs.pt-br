---
title: Comando dotnet-build - CLI do .NET Core | Microsoft Docs
description: "O comando dotnet-build compila um projeto e todas as suas dependências."
keywords: dotnet-build, CLI, comando de CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: e5deac8a7b8faac97ccf8b801f274a2c03268d64
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>Nome

`dotnet-build` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários. Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*. Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo. O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.

Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto. Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução. Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado. Para obter uma experiência semelhante no .NET Core, use o comando [dotnet publish](dotnet-publish.md). Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md). 

A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo. O arquivo é criado quando você executa [`dotnet restore`](dotnet-restore.md) antes de compilar o projeto. Sem o arquivo de ativos as ferramentas não conseguem resolver os assemblies de referência, o que resultará em erros.

O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais. Para saber mais, veja [Compilações incrementais](https://docs.microsoft.com/visualstudio/msbuild/incremental-builds). 

Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `/p` para configurar propriedades ou `/l` para definir um agente. Saiba mais sobre essas opções na [Referência de linha de comando do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference). 

O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto. O seguinte exemplo mostra um projeto que produzirá um código executável:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Para produzir uma biblioteca, omita a propriedade `<OutputType>`. A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada. 

## <a name="arguments"></a>Arguments

`PROJECT`

O arquivo de projeto a ser compilado. Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção.

`-f|--framework <FRAMEWORK>`

Compila para uma [estrutura](../../standard/frameworks.md) específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`-c|--configuration <CONFIGURATION>`

Define a configuração da compilação. Se for omitido, a configuração da compilação assumirá o padrão de `Debug`. Use a compilação `Release` para uma configuração de Versão.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica o tempo de execução de destino. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

`--version-suffix <VERSION_SUFFIX>`

Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto. O formato segue as diretrizes de versão do NuGet.

`--no-incremental`

Marca o build como não segura para build incremental. Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.

`--no-dependencies`

Ignora as referências projeto a projeto (P2P) e só compila o projeto raiz especificado para o build.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet build`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet build --configuration Release`

Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`

