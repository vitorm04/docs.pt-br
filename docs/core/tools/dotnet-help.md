---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168943"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nome

`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.

## <a name="synopsis"></a>Sinopse

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  Nome do comando da CLI do .NET Core. Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).

## <a name="options"></a>Opções

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

* Abre a página de documentação do comando [dotnet new](dotnet-new.md):

  ```console
  dotnet help new
  ```