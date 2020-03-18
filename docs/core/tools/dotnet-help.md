---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503723"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.

## <a name="synopsis"></a>Sinopse

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.

## <a name="arguments"></a>Argumentos

- **`COMMAND_NAME`**

  Nome do comando da CLI do .NET Core. Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

- Abre a página de documentação do comando [dotnet new](dotnet-new.md):

  ```dotnetcli
  dotnet help new
  ```
