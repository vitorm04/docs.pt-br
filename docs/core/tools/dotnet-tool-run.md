---
title: comando de execução da ferramenta dotnet
description: O comando dotnet ferramenta de execução invoca uma ferramenta local.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543876"
---
# <a name="dotnet-tool-run"></a>execução da ferramenta dotnet

**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores

## <a name="name"></a>Nome

`dotnet tool run`-invoca uma ferramenta local.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet tool run` pesquisa os arquivos de manifesto da ferramenta que estão no escopo do diretório atual. Quando ele encontra uma referência à ferramenta especificada, ele executa a ferramenta. Para obter mais informações, consulte [invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumentos

- **`COMMAND_NAME`**

  O nome do comando da ferramenta a ser executada.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="example"></a>Exemplo

- **`dotnet tool run dotnetsay`**

  Executa a ferramenta local `dotnetsay`.

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Core](global-tools.md)
