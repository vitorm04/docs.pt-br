---
title: Comando dotnet tool update
description: O comando dotnet tool update update atualiza a ferramenta .NET Core especificada em sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847814"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool update`- Atualiza a [ferramenta .NET Core](global-tools.md) especificada em sua máquina.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a>Descrição

O `dotnet tool update` comando fornece uma maneira de atualizar as ferramentas .NET Core em sua máquina para a versão estável mais recente do pacote. O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente. Para usar o comando, você especifica uma das seguintes opções:

* Para atualizar uma ferramenta global que foi instalada `--global` no local padrão, use a opção
* Para atualizar uma ferramenta global que foi instalada `--tool-path` em um local personalizado, use a opção.
* Para atualizar uma ferramenta local, `--global` `--tool-path` omita as opções e opções.

**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta global .NET Core para atualizar. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

- **`--add-source <SOURCE>`**

  Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

- **`--configfile <FILE>`**

  O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

- **`--framework <FRAMEWORK>`**

  Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.

- **`-g|--global`**

  Especifica que a atualização destina-se a uma ferramenta de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser atualizada é uma ferramenta local.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica o local onde a ferramenta global está instalada. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser atualizada é uma ferramenta local.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

- **`dotnet tool update -g dotnetsay`**

  Atualiza a ferramenta global [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Atualiza a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) instalada para o diretório atual.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI](global-tools-how-to-use.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
