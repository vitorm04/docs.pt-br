---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619776"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="ef17f-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="ef17f-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="ef17f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ef17f-102">Details</span></span>

<span data-ttu-id="ef17f-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="ef17f-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="ef17f-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="ef17f-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ef17f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ef17f-105">Suggestion</span></span>

<span data-ttu-id="ef17f-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef17f-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="ef17f-107">Name</span><span class="sxs-lookup"><span data-stu-id="ef17f-107">Name</span></span>    | <span data-ttu-id="ef17f-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ef17f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef17f-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ef17f-109">Scope</span></span>   |<span data-ttu-id="ef17f-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="ef17f-110">Minor</span></span>|
|<span data-ttu-id="ef17f-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ef17f-111">Version</span></span>|<span data-ttu-id="ef17f-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ef17f-112">4.5.1</span></span>|
|<span data-ttu-id="ef17f-113">Type</span><span class="sxs-lookup"><span data-stu-id="ef17f-113">Type</span></span>|<span data-ttu-id="ef17f-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ef17f-114">Runtime</span></span>|
