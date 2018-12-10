---
title: Comando dotnet help – CLI do .NET Core
description: O comando dotnet help mostra uma documentação mais detalhada online para o comando especificado.
ms.date: 12/04/2018
ms.openlocfilehash: 60d1cc706ca5c78fa3be877bd679888181213e88
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152169"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="91bfe-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="91bfe-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="91bfe-104">Nome</span><span class="sxs-lookup"><span data-stu-id="91bfe-104">Name</span></span>

<span data-ttu-id="91bfe-105">`dotnet help` – mostra uma documentação mais detalhada online para o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="91bfe-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91bfe-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="91bfe-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="91bfe-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="91bfe-107">Description</span></span>

<span data-ttu-id="91bfe-108">O comando `dotnet help` abre a página de referência para oferecer informações mais detalhadas sobre o comando especificado em docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="91bfe-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="91bfe-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="91bfe-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="91bfe-110">Nome do comando da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91bfe-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="91bfe-111">Para obter uma lista dos comandos válidos da CLI, consulte [CLI commands](index.md#cli-commands) (Comandos da CLI).</span><span class="sxs-lookup"><span data-stu-id="91bfe-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="91bfe-112">Opções</span><span class="sxs-lookup"><span data-stu-id="91bfe-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="91bfe-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="91bfe-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="91bfe-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91bfe-114">Examples</span></span>

* <span data-ttu-id="91bfe-115">Abre a página de documentação do comando [dotnet new](dotnet-new.md):</span><span class="sxs-lookup"><span data-stu-id="91bfe-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```