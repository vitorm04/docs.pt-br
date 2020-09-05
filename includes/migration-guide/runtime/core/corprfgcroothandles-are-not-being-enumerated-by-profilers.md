---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497798"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="9a34b-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="9a34b-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="9a34b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9a34b-102">Details</span></span>

<span data-ttu-id="9a34b-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="9a34b-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="9a34b-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="9a34b-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9a34b-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9a34b-105">Suggestion</span></span>

<span data-ttu-id="9a34b-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a34b-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="9a34b-107">Nome</span><span class="sxs-lookup"><span data-stu-id="9a34b-107">Name</span></span>    | <span data-ttu-id="9a34b-108">Valor</span><span class="sxs-lookup"><span data-stu-id="9a34b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a34b-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="9a34b-109">Scope</span></span>   |<span data-ttu-id="9a34b-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="9a34b-110">Minor</span></span>|
|<span data-ttu-id="9a34b-111">Versão</span><span class="sxs-lookup"><span data-stu-id="9a34b-111">Version</span></span>|<span data-ttu-id="9a34b-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="9a34b-112">4.5.1</span></span>|
|<span data-ttu-id="9a34b-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="9a34b-113">Type</span></span>|<span data-ttu-id="9a34b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="9a34b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9a34b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9a34b-115">Affected APIs</span></span>

<span data-ttu-id="9a34b-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="9a34b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
