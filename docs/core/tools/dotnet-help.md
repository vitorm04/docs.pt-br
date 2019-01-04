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
# <a name="dotnet-help-reference"></a><span data-ttu-id="b0949-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="b0949-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="b0949-104">Nome</span><span class="sxs-lookup"><span data-stu-id="b0949-104">Name</span></span>

<span data-ttu-id="b0949-105">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="b0949-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0949-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b0949-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="b0949-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0949-107">Description</span></span>

<span data-ttu-id="b0949-108">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="b0949-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="b0949-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0949-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="b0949-110">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0949-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="b0949-111">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="b0949-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="b0949-112">Opções</span><span class="sxs-lookup"><span data-stu-id="b0949-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="b0949-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="b0949-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="b0949-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b0949-114">Examples</span></span>

* <span data-ttu-id="b0949-115">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="b0949-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```