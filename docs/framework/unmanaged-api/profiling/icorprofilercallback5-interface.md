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
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865019"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="da648-102">Interface ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="da648-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="da648-103">Complementa as informações para ajudar um criador de perfil a identificar o fechamento completo de objetos dinâmicos, quando usado com o método [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) junto com os métodos [ICorProfilerCallback:: objectreferenciations](icorprofilercallback-objectreferences-method.md) e [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="da648-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="da648-104">O `ICorProfilerCallback5` deve ser implementado por um criador de perfil de memória gerenciada para assinar as notificações relacionadas aos identificadores dependentes.</span><span class="sxs-lookup"><span data-stu-id="da648-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da648-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="da648-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da648-106">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="da648-106">Methods</span></span>  
  
|<span data-ttu-id="da648-107">Método</span><span class="sxs-lookup"><span data-stu-id="da648-107">Method</span></span>|<span data-ttu-id="da648-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="da648-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da648-109">Método ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="da648-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="da648-110">Identifica o fechamento transitivo de objetos referenciados por estas raízes por meio de referências diretas do campo de membro e de dependências `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="da648-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da648-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="da648-111">Requirements</span></span>  
 <span data-ttu-id="da648-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da648-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da648-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="da648-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da648-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da648-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da648-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="da648-115">See also</span></span>

- [<span data-ttu-id="da648-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="da648-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="da648-117">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="da648-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
