---
title: Interface ICorProfilerCallback3
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66e6a67ce022365fa8c9e1005dfecbe4b23abd10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158373"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="99150-102">Interface ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="99150-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="99150-103">Fornece métodos de retorno de chamada que o common language runtime (CLR) usa para comunicar anexação e desanexação de informações de estado para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="99150-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99150-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="99150-104">Methods</span></span>  
  
|<span data-ttu-id="99150-105">Método</span><span class="sxs-lookup"><span data-stu-id="99150-105">Method</span></span>|<span data-ttu-id="99150-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="99150-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99150-107">Método InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="99150-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="99150-108">Chamado pelo CLR para dar uma oportunidade de inicializar seu estado após uma operação de anexação de criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="99150-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="99150-109">Método ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="99150-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="99150-110">Chamado pelo CLR para indicar que o criador de perfil agora pode chamar os métodos de recuperação do atraso.</span><span class="sxs-lookup"><span data-stu-id="99150-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="99150-111">Método ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="99150-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="99150-112">Notifica o criador de perfil que o common language runtime (CLR) está prestes a descarregar a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="99150-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99150-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="99150-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99150-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99150-114">Requirements</span></span>  
 <span data-ttu-id="99150-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99150-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99150-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="99150-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99150-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99150-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="99150-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="99150-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99150-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99150-119">See also</span></span>

- [<span data-ttu-id="99150-120">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="99150-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="99150-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="99150-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="99150-122">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="99150-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="99150-123">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="99150-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
