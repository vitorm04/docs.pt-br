---
title: Comando dotnet help
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117712"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="8b9b9-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="8b9b9-103">dotnet help reference</span></span>

<span data-ttu-id="8b9b9-104">**Este artigo aplica-se a: ✓ o** SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="8b9b9-104">**This article applies to: ✓** .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="8b9b9-105">Nome</span><span class="sxs-lookup"><span data-stu-id="8b9b9-105">Name</span></span>

<span data-ttu-id="8b9b9-106">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="8b9b9-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b9b9-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="8b9b9-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="8b9b9-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b9b9-108">Description</span></span>

<span data-ttu-id="8b9b9-109">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="8b9b9-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="8b9b9-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b9b9-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="8b9b9-111">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8b9b9-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="8b9b9-112">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="8b9b9-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="8b9b9-113">Opções</span><span class="sxs-lookup"><span data-stu-id="8b9b9-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="8b9b9-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="8b9b9-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="8b9b9-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8b9b9-115">Examples</span></span>

* <span data-ttu-id="8b9b9-116">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="8b9b9-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
