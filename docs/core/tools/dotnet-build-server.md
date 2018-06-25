---
title: Comando dotnet build-server – CLI do .NET Core
description: O comando dotnet build-server interage com servidores iniciados por um build.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696248"
---
# <a name="dotnet-build"></a>dotnet-build

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

`shutdown`

Desliga servidores de build iniciados por meio do dotnet. Por padrão, todos os servidores estão desligados.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`--msbuild`

Desliga o servidor de build do MSBuild.

`--razor`

Desliga o servidor de build do Razor.

`--vbcscompiler`

Desliga o servidor de build do compilador do VB/C#.
