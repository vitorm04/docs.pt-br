---
title: Comando dotnet tool install
description: O comando dotnet tool install instala no computador a Ferramenta Global do .NET Core especificada.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117475"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nome

`dotnet tool install` – instala a [Ferramenta Global do .NET Core](global-tools.md) especificada no computador.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Descrição

O comando `dotnet tool install` fornece uma maneira de instalar no computador as Ferramentas Globais do .NET Core. Para usar o comando, você precisa especificar que deseja uma instalação de todos os usuários usando a opção `--global` ou especificar um caminho para instalá-la usando a opção `--tool-path`.

As Ferramentas Globais são instaladas nos seguintes diretórios por padrão quando você especifica a opção `-g` (ou `--global`):

| Sistema operacional          | Caminho                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Nome/ID do pacote NuGet que contém a Ferramenta Global do .NET Core a ser instalada.

## <a name="options"></a>Opções

`--add-source <SOURCE>`

Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

`--configfile <FILE>`

O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

`--framework <FRAMEWORK>`

Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta. Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.

`-g|--global`

Especifica que a instalação é de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Se você não especificar essa opção, especifique a opção `--tool-path`.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--tool-path <PATH>`

Especifica o local do qual a Ferramenta Global será instalada. PATH pode ser absoluto ou relativo. Se PATH não existir, o comando tentará criá-lo. Não pode ser combinada com a opção `--global`. Se você não especificar essa opção, especifique a opção `--global`.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`--version <VERSION_NUMBER>`

A versão da ferramenta a ser instalada. Por padrão, a última versão estável do pacote é instalada. Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.

## <a name="examples"></a>Exemplos

Instala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) na localização padrão:

`dotnet tool install -g dotnetsay`

Instala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) em uma pasta específica do Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Instala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) em uma pasta específica do Linux/macOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Instala a versão 2.0.0 da Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/):

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Consulte também

- [Ferramentas Globais do .NET Core](global-tools.md)
