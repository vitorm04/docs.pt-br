---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235037"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="c7227-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="c7227-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c7227-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c7227-102">Details</span></span>|<span data-ttu-id="c7227-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="c7227-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="c7227-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="c7227-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="c7227-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c7227-105">Suggestion</span></span>|<span data-ttu-id="c7227-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7227-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="c7227-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="c7227-107">Scope</span></span>|<span data-ttu-id="c7227-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="c7227-108">Minor</span></span>|
|<span data-ttu-id="c7227-109">Versão</span><span class="sxs-lookup"><span data-stu-id="c7227-109">Version</span></span>|<span data-ttu-id="c7227-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c7227-110">4.5.1</span></span>|
|<span data-ttu-id="c7227-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="c7227-111">Type</span></span>|<span data-ttu-id="c7227-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c7227-112">Runtime</span></span>|
