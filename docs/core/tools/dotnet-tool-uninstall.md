---
title: Comando dotnet tool uninstall
description: O comando dotnet tool uninstall desinstala do computador a Ferramenta Global do .NET Core especificada.
ms.date: 05/29/2018
ms.openlocfilehash: 2ac0046d012fcf4a4be1c9bfa2e942e35b2c7290
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168345"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nome

`dotnet tool uninstall` – desinstala do computador a [Ferramenta Global do .NET Core](global-tools.md) especificada.

## <a name="synopsis"></a>Sinopse

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Descrição

O comando `dotnet tool uninstall` fornece uma maneira de desinstalar do computador as Ferramentas Globais do .NET Core. Para usar o comando, você precisa especificar que deseja remover uma ferramenta de todos os usuários usando a opção `--global` ou especificar um caminho para o local em que a ferramenta está instalada usando a opção `--tool-path`.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Nome/ID do pacote NuGet que contém a Ferramenta Global do .NET Core a ser desinstalada. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

`-g|--global`

Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Se você não especificar essa opção, especifique a opção `--tool-path`.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--tool-path <PATH>`

Especifica o local do qual a Ferramenta Global será desinstalada. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Se você não especificar essa opção, especifique a opção `--global`.

## <a name="examples"></a>Exemplos

Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/):

`dotnet tool uninstall -g dotnetsay`

Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de uma pasta específica do Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de uma pasta específica do Linux/macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Consulte também

* [Ferramentas Globais do .NET Core](global-tools.md)