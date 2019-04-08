---
title: Interface ICorProfilerCallback5
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 114d97e02b0a6b80c46f971ed74a24dc3c397f1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072643"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="ffd1d-102">Interface ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="ffd1d-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="ffd1d-103">Complementa informações para ajudar um criador de perfil a identificar o fechamento de objetos dinâmicos, quando usado com o a [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)método junto com o [ICorProfilerCallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) e [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="ffd1d-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 `ICorProfilerCallback5` <span data-ttu-id="ffd1d-104">deve ser implementada por um criador de perfil de memória gerenciada para assinar as notificações relacionadas aos identificadores dependentes.</span><span class="sxs-lookup"><span data-stu-id="ffd1d-104">must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffd1d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffd1d-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffd1d-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="ffd1d-106">Methods</span></span>  
  
|<span data-ttu-id="ffd1d-107">Método</span><span class="sxs-lookup"><span data-stu-id="ffd1d-107">Method</span></span>|<span data-ttu-id="ffd1d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffd1d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffd1d-109">Método ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="ffd1d-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="ffd1d-110">Identifica o fechamento transitivo de objetos referenciados por estas raízes por meio de referências diretas do campo de membro e de dependências `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="ffd1d-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffd1d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffd1d-111">Requirements</span></span>  
 <span data-ttu-id="ffd1d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffd1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffd1d-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffd1d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="ffd1d-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ffd1d-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ffd1d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffd1d-115">See also</span></span>

- [<span data-ttu-id="ffd1d-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="ffd1d-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ffd1d-117">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="ffd1d-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
