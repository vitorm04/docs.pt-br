---
title: comando de execução de ferramenta dotnet
description: O comando dotnet tool run invoca uma ferramenta local.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847840"
---
# <a name="dotnet-tool-run"></a>dotnet ferramenta executar

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool run`- Invoca uma ferramenta local.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a>Descrição

O `dotnet tool run` comando pesquisa arquivos manifestos de ferramenta que estão no escopo para o diretório atual. Quando encontra uma referência à ferramenta especificada, ela executa a ferramenta. Para obter mais informações, consulte [Invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumentos

- **`COMMAND_NAME`**

  O nome de comando da ferramenta para executar.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="example"></a>Exemplo

- **`dotnet tool run dotnetsay`**

  Executa `dotnetsay` a ferramenta local.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
