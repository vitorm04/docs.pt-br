---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734240"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="fe43b-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="fe43b-103">dotnet help reference</span></span>

<span data-ttu-id="fe43b-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="fe43b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="fe43b-105">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fe43b-105">Name</span></span>

<span data-ttu-id="fe43b-106">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="fe43b-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fe43b-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="fe43b-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="fe43b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe43b-108">Description</span></span>

<span data-ttu-id="fe43b-109">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="fe43b-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="fe43b-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="fe43b-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="fe43b-111">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe43b-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="fe43b-112">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="fe43b-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="fe43b-113">{1&gt;Opções&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fe43b-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="fe43b-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="fe43b-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="fe43b-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fe43b-115">Examples</span></span>

* <span data-ttu-id="fe43b-116">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="fe43b-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
