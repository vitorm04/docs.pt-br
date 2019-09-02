---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 04/24/2019
ms.openlocfilehash: b2dfd5f317466f18d9246bd1fb281a92c42f6d9d
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168103"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Este artigo se aplica a: ✓** SDK do .NET Core 2.1 e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Nome

`dotnet build-server` – interage com servidores iniciados por um build.

## <a name="synopsis"></a>Sinopse

```console
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Comandos

* **`shutdown`**

  Desliga servidores de build iniciados por meio do dotnet. Por padrão, todos os servidores estão desligados.

## <a name="options"></a>Opções

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

* **`--msbuild`**

  Desliga o servidor de build do MSBuild.

* **`--razor`**

  Desliga o servidor de build do Razor.

* **`--vbcscompiler`**

  Desliga o servidor de build do compilador do VB/C#.
