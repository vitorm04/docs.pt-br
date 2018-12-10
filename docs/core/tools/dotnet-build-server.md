---
title: Comando dotnet build-server – CLI do .NET Core
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 12/04/2018
ms.openlocfilehash: 2746ade12cc819089258483e84a8c0f02a64c755
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125672"
---
# <a name="dotnet-build-server"></a>dotnet build-server

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nome

`dotnet build-server` – interage com servidores iniciados por um build.

## <a name="synopsis"></a>Sinopse

```
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