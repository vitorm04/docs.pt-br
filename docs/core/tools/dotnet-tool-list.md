---
title: Comando dotnet tool list
description: O comando dotnet da lista de ferramentas lista as ferramentas do .NET Core que estão instaladas em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: f231dcfe64a925f75f948d508e7a2d83befd9a00
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156966"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet tool list`-lista todas as [Ferramentas do .NET Core](global-tools.md) do tipo especificado atualmente instalado em seu computador.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet tool list` fornece uma maneira de listar todas as ferramentas globais, caminho-ferramenta ou local do .NET Core instaladas em seu computador. O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.  Para usar o comando, especifique um dos seguintes:

* Uma ferramenta global instalada no local padrão. Usar a opção `--global`
* Uma ferramenta global instalada em um local personalizado. Use a opção `--tool-path`.
* Uma ferramenta local. Omita as opções `--global` e `--tool-path`.

**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**

## <a name="options"></a>Opções

- **`-g|--global`**

  Lista as ferramentas globais em todo o usuário. Não pode ser combinada com a opção `--tool-path`. Omitir `--global` e `--tool-path` lista as ferramentas locais.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--tool-path <PATH>`**

  Especifica um local personalizado onde encontrar ferramentas globais. PATH pode ser absoluto ou relativo. Não pode ser combinada com a opção `--global`. Omitir `--global` e `--tool-path` lista as ferramentas locais.

## <a name="examples"></a>Exemplos

- **`dotnet tool list -g`**

  Lista todas as ferramentas globais instaladas por todo o usuário em seu computador (perfil de usuário atual).

- **`dotnet tool list --tool-path c:\global-tools`**

  Lista as ferramentas globais de um diretório específico do Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Lista as ferramentas globais de um diretório específico do Linux/macOS.

- **`dotnet tool list`**

  Lista todas as ferramentas locais disponíveis no diretório atual.

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Core](global-tools.md)
