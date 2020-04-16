---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463684"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="dd5a2-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="dd5a2-103">dotnet help reference</span></span>

<span data-ttu-id="dd5a2-104">**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="dd5a2-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dd5a2-105">Nome</span><span class="sxs-lookup"><span data-stu-id="dd5a2-105">Name</span></span>

<span data-ttu-id="dd5a2-106">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd5a2-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="dd5a2-107">Synopsis</span></span>

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="dd5a2-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd5a2-108">Description</span></span>

<span data-ttu-id="dd5a2-109">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="dd5a2-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="dd5a2-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="dd5a2-111">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="dd5a2-112">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="dd5a2-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="dd5a2-113">Opções</span><span class="sxs-lookup"><span data-stu-id="dd5a2-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="dd5a2-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="dd5a2-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dd5a2-115">Examples</span></span>

- <span data-ttu-id="dd5a2-116">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="dd5a2-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
