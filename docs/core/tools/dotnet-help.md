---
title: Comando dotnet help – CLI do .NET Core
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
author: mairaw
ms.author: mairaw
ms.date: 08/17/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 189eeea87babbce16751c5875f62c990ebecc10a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
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

`COMMAND_NAME`

Nome do comando da CLI do .NET Core. Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Abre a página de documentação do comando [dotnet new](dotnet-new.md):

`dotnet help new`
