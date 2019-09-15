---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 08/08/2019
ms.openlocfilehash: e76f858f2529afc50646473f1aab9d52730cff16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990470"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="118cb-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="118cb-103">dotnet help reference</span></span>

<span data-ttu-id="118cb-104">**Este artigo aplica-se a: ✓ o** SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="118cb-104">**This article applies to: ✓** .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="118cb-105">Nome</span><span class="sxs-lookup"><span data-stu-id="118cb-105">Name</span></span>

<span data-ttu-id="118cb-106">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="118cb-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="118cb-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="118cb-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="118cb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="118cb-108">Description</span></span>

<span data-ttu-id="118cb-109">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="118cb-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="118cb-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="118cb-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="118cb-111">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="118cb-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="118cb-112">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="118cb-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="118cb-113">Opções</span><span class="sxs-lookup"><span data-stu-id="118cb-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="118cb-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="118cb-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="118cb-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="118cb-115">Examples</span></span>

* <span data-ttu-id="118cb-116">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="118cb-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```
