---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734383"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Name

`dotnet build-server` – interage com servidores iniciados por um build.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Comandos

- **`shutdown`**

  Desliga servidores de build iniciados por meio do dotnet. Por padrão, todos os servidores estão desligados.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--msbuild`**

  Desliga o servidor de build do MSBuild.

- **`--razor`**

  Desliga o servidor de build do Razor.

- **`--vbcscompiler`**

  Desliga o servidor de build do compilador do VB/C#.
