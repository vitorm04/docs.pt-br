---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858576"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="33970-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="33970-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="33970-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="33970-102">Details</span></span>|<span data-ttu-id="33970-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="33970-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="33970-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="33970-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="33970-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="33970-105">Suggestion</span></span>|<span data-ttu-id="33970-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33970-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="33970-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="33970-107">Scope</span></span>|<span data-ttu-id="33970-108">Secundária</span><span class="sxs-lookup"><span data-stu-id="33970-108">Minor</span></span>|
|<span data-ttu-id="33970-109">Versão</span><span class="sxs-lookup"><span data-stu-id="33970-109">Version</span></span>|<span data-ttu-id="33970-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="33970-110">4.5.1</span></span>|
|<span data-ttu-id="33970-111">Type</span><span class="sxs-lookup"><span data-stu-id="33970-111">Type</span></span>|<span data-ttu-id="33970-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="33970-112">Runtime</span></span>|
