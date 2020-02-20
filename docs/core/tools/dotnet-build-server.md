---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503782"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

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
