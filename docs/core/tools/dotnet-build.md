---
title: "Comando dotnet build – CLI do .NET Core"
description: "O comando dotnet build compila um projeto e todas as suas dependências."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b2b625729b5db22bc7b69194f20963857004e3e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-build"></a>dotnet-build

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet build` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários. Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*. Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo. O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.

Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto. Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução. Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado. Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md). Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).

A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo. O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado. Sem o arquivo de ativos, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros. Com o SDK do .NET Core 1.x, era necessário executar explicitamente o `dotnet restore` antes de executar `dotnet build`. Começando com o SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente ao executar `dotnet build`. Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais. Para saber mais, veja [Compilações incrementais](/visualstudio/msbuild/incremental-builds).

Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `/p` para configurar propriedades ou `/l` para definir um agente. Saiba mais sobre essas opções na [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). 

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

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila para uma [estrutura](../../standard/frameworks.md) específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`--force`

 Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. Isso é equivalente a excluir o arquivo *project.assets.json*.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--no-dependencies`

Ignora as referências projeto a projeto (P2P) e só compila o projeto raiz especificado para o build.

`--no-incremental`

Marca o build como não segura para build incremental. Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.

`--no-restore`

Não executa uma restauração implícita durante o build.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica o tempo de execução de destino. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto. O formato segue as diretrizes de versão do NuGet.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila para uma [estrutura](../../standard/frameworks.md) específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`--no-dependencies`

Ignora as referências projeto a projeto (P2P) e só compila o projeto raiz especificado para o build.

`--no-incremental`

Marca o build como não segura para build incremental. Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica o tempo de execução de destino. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto. O formato segue as diretrizes de versão do NuGet.

---

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet build`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet build --configuration Release`

Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`