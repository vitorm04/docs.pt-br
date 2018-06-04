---
title: Comando dotnet clean – CLI do .NET Core
description: O comando dotnet clean limpa o diretório atual.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697025"
---
# <a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet clean` – limpa a saída de um projeto.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet clean` limpará a saída da compilação anterior. Ele é implementado como um [destino de MSBuild](/visualstudio/msbuild/msbuild-targets), para que o projeto seja avaliado durante a execução do comando. Apenas as saídas criadas durante a compilação são limpas. As pastas de saídas intermediária (*obj*) e final (*bin*) serão limpas.

## <a name="arguments"></a>Arguments

`PROJECT`

O projeto do MSBuild a ser limpo. Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.

## <a name="options"></a>Opções

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`. Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.

`-f|--framework <FRAMEWORK>`

A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação. A estrutura precisa ser definida no [arquivo de projeto](csproj.md). Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-o|--output <OUTPUT_DIRECTORY>`

O diretório no qual as saídas compiladas são colocadas. Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Limpa a pasta de saída do tempo de execução especificado. Isso é usado quando uma [implantação autocontida](../deploying/index.md#self-contained-deployments-scd) foi criada.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`. Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.

`-f|--framework <FRAMEWORK>`

A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação. A estrutura precisa ser definida no [arquivo de projeto](csproj.md). Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-o|--output <OUTPUT_DIRECTORY>`

O diretório no qual as saídas compiladas são colocadas. Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].

---

## <a name="examples"></a>Exemplos

Limpe uma compilação padrão do projeto:

`dotnet clean`

Limpe um projeto compilado usando a configuração da Versão:

`dotnet clean --configuration Release`
