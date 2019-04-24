---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774280"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="f2fd3-101">List\<T>.ForEach agora gera exceção durante a modificação de item de lista</span><span class="sxs-lookup"><span data-stu-id="f2fd3-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f2fd3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f2fd3-102">Details</span></span>|<span data-ttu-id="f2fd3-103">Começando no .NET Framework 4.5, um enumerador <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> gerará uma exceção <xref:System.InvalidOperationException?displayProperty=name> se um elemento na coleção de chamada for modificado.</span><span class="sxs-lookup"><span data-stu-id="f2fd3-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="f2fd3-104">Anteriormente, isso não geraria uma exceção, mas podia levar a condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="f2fd3-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="f2fd3-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f2fd3-105">Suggestion</span></span>|<span data-ttu-id="f2fd3-106">De modo ideal, o código deve ser corrigido para não modificar listas durante a enumeração de seus elementos, pois essa nunca é uma operação segura.</span><span class="sxs-lookup"><span data-stu-id="f2fd3-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="f2fd3-107">Porém, para reverter para o comportamento anterior, um aplicativo pode ser direcionado ao .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="f2fd3-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="f2fd3-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="f2fd3-108">Scope</span></span>|<span data-ttu-id="f2fd3-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f2fd3-109">Edge</span></span>|
|<span data-ttu-id="f2fd3-110">Versão</span><span class="sxs-lookup"><span data-stu-id="f2fd3-110">Version</span></span>|<span data-ttu-id="f2fd3-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f2fd3-111">4.5</span></span>|
|<span data-ttu-id="f2fd3-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="f2fd3-112">Type</span></span>|<span data-ttu-id="f2fd3-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="f2fd3-113">Retargeting</span></span>|
|<span data-ttu-id="f2fd3-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f2fd3-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
