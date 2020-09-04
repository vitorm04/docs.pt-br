---
title: Alterações significativas na análise de código
description: Lista as alterações significativas nos analisadores de código-fonte do .NET.
ms.date: 08/22/2020
ms.openlocfilehash: 8b2b50c5f03a3ca971aefd0f2cf53624dfa82274
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465553"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="d0c4d-103">Alterações significativas na análise de código</span><span class="sxs-lookup"><span data-stu-id="d0c4d-103">Code analysis breaking changes</span></span>

<span data-ttu-id="d0c4d-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="d0c4d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d0c4d-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="d0c4d-105">Breaking change</span></span> | <span data-ttu-id="d0c4d-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d0c4d-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d0c4d-107">CA1831: usar asspan ou asmemory em vez de indexador baseado em intervalo</span><span class="sxs-lookup"><span data-stu-id="d0c4d-107">CA1831: Use AsSpan or AsMemory instead of Range-based indexer</span></span>](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | <span data-ttu-id="d0c4d-108">5,0</span><span class="sxs-lookup"><span data-stu-id="d0c4d-108">5.0</span></span> |
| [<span data-ttu-id="d0c4d-109">CA2014: Não usar stackalloc em loops</span><span class="sxs-lookup"><span data-stu-id="d0c4d-109">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="d0c4d-110">5,0</span><span class="sxs-lookup"><span data-stu-id="d0c4d-110">5.0</span></span> |
| [<span data-ttu-id="d0c4d-111">CA2015: não definir finalizadores para tipos derivados de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="d0c4d-111">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="d0c4d-112">5,0</span><span class="sxs-lookup"><span data-stu-id="d0c4d-112">5.0</span></span> |
| [<span data-ttu-id="d0c4d-113">CA2247: o argumento para o Construtor TaskCompletionSource deve ser um valor TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="d0c4d-113">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="d0c4d-114">5,0</span><span class="sxs-lookup"><span data-stu-id="d0c4d-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d0c4d-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d0c4d-115">.NET 5.0</span></span>

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
