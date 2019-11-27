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
ms.openlocfilehash: ce34d43091cdee0bca88f94711e49072fa4fd08c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430070"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="2b3bb-102">Interface ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="2b3bb-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="2b3bb-103">Complementa as informações para ajudar um criador de perfil a identificar o fechamento completo de objetos dinâmicos, quando usado com o método [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2:: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) junto com os métodos [ICorProfilerCallback:: objectreferenciations](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) e [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2b3bb-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="2b3bb-104">`ICorProfilerCallback5` deve ser implementado por um profiler de memória gerenciada para assinar notificações relacionadas a identificadores dependentes.</span><span class="sxs-lookup"><span data-stu-id="2b3bb-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b3bb-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b3bb-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b3bb-106">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2b3bb-106">Methods</span></span>  
  
|<span data-ttu-id="2b3bb-107">Método</span><span class="sxs-lookup"><span data-stu-id="2b3bb-107">Method</span></span>|<span data-ttu-id="2b3bb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b3bb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b3bb-109">Método ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="2b3bb-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="2b3bb-110">Identifica o fechamento transitivo de objetos referenciados por estas raízes por meio de referências diretas do campo de membro e de dependências `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="2b3bb-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b3bb-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2b3bb-111">Requirements</span></span>  
 <span data-ttu-id="2b3bb-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b3bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b3bb-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2b3bb-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b3bb-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b3bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3bb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b3bb-115">See also</span></span>

- [<span data-ttu-id="2b3bb-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2b3bb-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2b3bb-117">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="2b3bb-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
