---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858576"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="462f2-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="462f2-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="462f2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="462f2-102">Details</span></span>|<span data-ttu-id="462f2-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="462f2-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="462f2-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="462f2-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="462f2-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="462f2-105">Suggestion</span></span>|<span data-ttu-id="462f2-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="462f2-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="462f2-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="462f2-107">Scope</span></span>|<span data-ttu-id="462f2-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="462f2-108">Minor</span></span>|
|<span data-ttu-id="462f2-109">Versão</span><span class="sxs-lookup"><span data-stu-id="462f2-109">Version</span></span>|<span data-ttu-id="462f2-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="462f2-110">4.5.1</span></span>|
|<span data-ttu-id="462f2-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="462f2-111">Type</span></span>|<span data-ttu-id="462f2-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="462f2-112">Runtime</span></span>|

