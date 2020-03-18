---
title: Comando dotnet tool list
description: O comando dotnet tool list lists the .NET Core ferramentas que estão instaladas na sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847866"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool list`- Lista todas as [ferramentas .NET Core](global-tools.md) do tipo especificado atualmente instalados em sua máquina.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a>Descrição

O `dotnet tool list` comando fornece uma maneira de você listar todas as Ferramentas globais, de caminho de ferramentas ou locais do .NET Core instaladas na máquina. O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.  Para usar o comando, você especifica um dos seguintes:

* Uma ferramenta global instalada no local padrão. Use `--global` a opção
* Uma ferramenta global instalada em um local personalizado. Use a opção `--tool-path`.
* Uma ferramenta local. Omita `--global` `--tool-path` as opções.

**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**

## <a name="options"></a>Opções

- **`-g|--global`**

  Lista ferramentas globais de todo o usuário. Não pode ser combinada com a opção `--tool-path`. Omitindo ambos `--global` e `--tool-path` lista ferramentas locais.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica um local personalizado onde encontrar ferramentas globais. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitindo ambos `--global` e `--tool-path` lista ferramentas locais.

## <a name="examples"></a>Exemplos

- **`dotnet tool list -g`**

  Lista todas as ferramentas globais instaladas em todo o usuário em sua máquina (perfil de usuário atual).

- **`dotnet tool list --tool-path c:\global-tools`**

  Lista as ferramentas globais de um diretório específico do Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Lista as ferramentas globais de um diretório específico do Linux/macOS.

- **`dotnet tool list`**

  Lista todas as ferramentas locais disponíveis no diretório atual.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI](global-tools-how-to-use.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
