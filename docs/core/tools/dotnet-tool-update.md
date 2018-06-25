---
title: Comando dotnet tool update – CLI do .NET Core
description: O comando dotnet tool update atualiza a Ferramenta Global do .NET Core especificada no computador.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696683"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nome

`dotnet tool update` – atualiza a [Ferramenta Global do .NET Core](global-tools.md) especificada no computador.

## <a name="synopsis"></a>Sinopse

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Descrição

O comando `dotnet tool update` fornece uma maneira de atualizar as Ferramentas Globais do .NET Core no computador para a última versão estável do pacote. O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente. Para usar o comando, você precisa especificar que deseja atualizar uma ferramenta de uma instalação de todos os usuários usando a opção `--global` ou especificar um caminho para o local em que a ferramenta está instalada usando a opção `--tool-path`.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Nome/ID do pacote NuGet que contém a Ferramenta Global do .NET Core a ser atualizada. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

`--add-source <SOURCE>`

Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

`--configfile <FILE>`

O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

`--framework <FRAMEWORK>`

Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.

`-g|--global`

Especifica que a atualização destina-se a uma ferramenta de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Se você não especificar essa opção, especifique a opção `--tool-path`.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--tool-path <PATH>`

Especifica o local no qual a Ferramenta Global é instalada. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Se você não especificar essa opção, especifique a opção `--global`.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Atualiza a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/):

`dotnet tool update -g dotnetsay`

Atualiza a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em uma pasta específica do Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Atualiza a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em uma pasta específica do Linux/macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Consulte também

[Ferramentas Globais do .NET Core](global-tools.md)