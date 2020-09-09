---
title: Alterações significativas na análise de código
description: Lista as alterações significativas nos analisadores de código-fonte do .NET.
ms.date: 09/02/2020
ms.openlocfilehash: f1e89c90e6d91b9b3555542a0c7adf2607a76a01
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598042"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="e60c8-103">Alterações significativas na análise de código</span><span class="sxs-lookup"><span data-stu-id="e60c8-103">Code analysis breaking changes</span></span>

<span data-ttu-id="e60c8-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="e60c8-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e60c8-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="e60c8-105">Breaking change</span></span> | <span data-ttu-id="e60c8-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e60c8-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e60c8-107">CA1417: OutAttribute no parâmetro de cadeia de caracteres para P/Invoke</span><span class="sxs-lookup"><span data-stu-id="e60c8-107">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="e60c8-108">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-108">5.0</span></span> |
| [<span data-ttu-id="e60c8-109">CA1831: usar asspan em vez de indexadores baseados em intervalo para cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e60c8-109">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="e60c8-110">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-110">5.0</span></span> |
| [<span data-ttu-id="e60c8-111">CA2013: Não usar ReferenceEquals com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="e60c8-111">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="e60c8-112">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-112">5.0</span></span> |
| [<span data-ttu-id="e60c8-113">CA2014: Não usar stackalloc em loops</span><span class="sxs-lookup"><span data-stu-id="e60c8-113">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="e60c8-114">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-114">5.0</span></span> |
| [<span data-ttu-id="e60c8-115">CA2015: não definir finalizadores para tipos derivados de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="e60c8-115">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="e60c8-116">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-116">5.0</span></span> |
| [<span data-ttu-id="e60c8-117">CA2247: o argumento para o Construtor TaskCompletionSource deve ser um valor TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="e60c8-117">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="e60c8-118">5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e60c8-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e60c8-119">.NET 5.0</span></span>

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
