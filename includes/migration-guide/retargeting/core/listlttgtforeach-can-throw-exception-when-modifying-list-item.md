---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617110"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="ac576-101">List&lt;T&gt;.ForEach agora gera exceção durante a modificação de item de lista</span><span class="sxs-lookup"><span data-stu-id="ac576-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="ac576-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ac576-102">Details</span></span>

<span data-ttu-id="ac576-103">Começando no .NET Framework 4.5, um enumerador <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> gerará uma exceção <xref:System.InvalidOperationException?displayProperty=fullName> se um elemento na coleção de chamada for modificado.</span><span class="sxs-lookup"><span data-stu-id="ac576-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="ac576-104">Anteriormente, isso não geraria uma exceção, mas podia levar a condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="ac576-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ac576-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ac576-105">Suggestion</span></span>

<span data-ttu-id="ac576-106">De modo ideal, o código deve ser corrigido para não modificar listas durante a enumeração de seus elementos, pois essa nunca é uma operação segura.</span><span class="sxs-lookup"><span data-stu-id="ac576-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="ac576-107">Porém, para reverter para o comportamento anterior, um aplicativo pode ser direcionado ao .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="ac576-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="ac576-108">Name</span><span class="sxs-lookup"><span data-stu-id="ac576-108">Name</span></span>    | <span data-ttu-id="ac576-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ac576-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ac576-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="ac576-110">Scope</span></span>   | <span data-ttu-id="ac576-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ac576-111">Edge</span></span>        |
| <span data-ttu-id="ac576-112">Versão</span><span class="sxs-lookup"><span data-stu-id="ac576-112">Version</span></span> | <span data-ttu-id="ac576-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ac576-113">4.5</span></span>         |
| <span data-ttu-id="ac576-114">Type</span><span class="sxs-lookup"><span data-stu-id="ac576-114">Type</span></span>    | <span data-ttu-id="ac576-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ac576-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ac576-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ac576-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
