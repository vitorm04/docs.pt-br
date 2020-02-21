---
title: Comando dotnet tool uninstall
description: O comando dotnet ferramenta de desinstalação desinstala a ferramenta .NET Core especificada do seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543437"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet tool uninstall`-desinstala a [ferramenta .NET Core](global-tools.md) especificada do seu computador.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet tool uninstall` fornece uma maneira de desinstalar as ferramentas do .NET Core do seu computador. Para usar o comando, especifique uma das seguintes opções:

* Para desinstalar uma ferramenta global que foi instalada no local padrão, use a opção `--global`.
* Para desinstalar uma ferramenta global que foi instalada em um local personalizado, use a opção `--tool-path`.
* Para desinstalar uma ferramenta local, omita as opções `--global` e `--tool-path`.

**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser desinstalada. Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opções

- **`-g|--global`**

  Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir `--global` e `--tool-path` especifica que a ferramenta a ser removida é uma ferramenta local. 

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica o local onde a ferramenta será desinstalada. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitir `--global` e `--tool-path` especifica que a ferramenta a ser removida é uma ferramenta local. 

## <a name="examples"></a>Exemplos

- **`dotnet tool uninstall -g dotnetsay`**

  Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do linux/MacOS.

- **`dotnet tool uninstall dotnetsay`**

  Desinstala a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do diretório atual.

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Core](global-tools.md)
