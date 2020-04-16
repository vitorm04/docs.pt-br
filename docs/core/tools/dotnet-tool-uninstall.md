---
title: Comando dotnet tool uninstall
description: O comando dotnet desinstalar a ferramenta .NET Core especificada da sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463305"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool uninstall`- Desinstala a [ferramenta .NET Core](global-tools.md) especificada da sua máquina.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>Descrição

O `dotnet tool uninstall` comando fornece uma maneira de você desinstalar ferramentas .NET Core da sua máquina. Para usar o comando, você especifica uma das seguintes opções:

* Para desinstalar uma ferramenta global instalada no local `--global` padrão, use a opção.
* Para desinstalar uma ferramenta global instalada em um `--tool-path` local personalizado, use a opção.
* Para desinstalar uma ferramenta local, omita as `--global` opções e `--tool-path` opções.

**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta .NET Core para desinstalar. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

- **`-g|--global`**

  Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser removida é uma ferramenta local.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica o local onde desinstalar a ferramenta. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser removida é uma ferramenta local.

## <a name="examples"></a>Exemplos

- **`dotnet tool uninstall -g dotnetsay`**

  Desinstala a ferramenta global [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) a partir de um diretório específico do Linux/macOS.

- **`dotnet tool uninstall dotnetsay`**

  Desinstala a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do diretório atual.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI](global-tools-how-to-use.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
