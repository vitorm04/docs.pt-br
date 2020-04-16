---
title: comando de execução de ferramenta dotnet
description: O comando dotnet tool run invoca uma ferramenta local.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463320"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool run`- Invoca uma ferramenta local.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
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
