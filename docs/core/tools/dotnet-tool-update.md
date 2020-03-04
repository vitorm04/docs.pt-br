---
title: Comando dotnet tool update
description: O comando dotnet ferramenta de atualização atualiza a ferramenta .NET Core especificada em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156940"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet tool update`-atualiza a [ferramenta .NET Core](global-tools.md) especificada em seu computador.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet tool update` fornece uma maneira de atualizar as ferramentas do .NET Core em seu computador para a versão estável mais recente do pacote. O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente. Para usar o comando, especifique uma das seguintes opções:

* Para atualizar uma ferramenta global que foi instalada no local padrão, use a opção `--global`
* Para atualizar uma ferramenta global que foi instalada em um local personalizado, use a opção `--tool-path`.
* Para atualizar uma ferramenta local, omita as opções `--global` e `--tool-path`.

**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta global .NET Core a ser atualizada. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

- **`--add-source <SOURCE>`**

  Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

- **`--configfile <FILE>`**

  O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

- **`--framework <FRAMEWORK>`**

  Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.

- **`-g|--global`**

  Especifica que a atualização destina-se a uma ferramenta de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica o local onde a ferramenta global está instalada. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitir `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

- **`dotnet tool update -g dotnetsay`**

  Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do linux/MacOS.

- **`dotnet tool update dotnetsay`**

  Atualiza a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) instalada para o diretório atual.

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Core](global-tools.md)
