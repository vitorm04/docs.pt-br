---
title: Método ICorProfilerCallback3::ProfilerAttachComplete
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 4c5b8f18424ba54d9e8e14ba0a518a89e0d54796
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439470"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="03782-102">Método ICorProfilerCallback3::ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="03782-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="03782-103">Chamado pelo Common Language Runtime (CLR) para indicar que o criador de perfil agora pode chamar os métodos de atualização [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) e [ICorProfilerInfo3:: EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="03782-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03782-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03782-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="03782-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="03782-105">Remarks</span></span>  
 <span data-ttu-id="03782-106">O retorno de chamada `ProfilerAttachComplete` é emitido depois que o método [ICorProfilerCallback3:: InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) é chamado.</span><span class="sxs-lookup"><span data-stu-id="03782-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="03782-107">Isso indica o seguinte:</span><span class="sxs-lookup"><span data-stu-id="03782-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="03782-108">Os retornos de chamada que foram solicitados pelo criador de perfil no `InitializeForAttach` foram ativados.</span><span class="sxs-lookup"><span data-stu-id="03782-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="03782-109">O criador de perfil agora pode realizar a atualização nas IDs associadas sem se preocupar com notificações ausentes.</span><span class="sxs-lookup"><span data-stu-id="03782-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="03782-110">O CLR ignora o valor de retorno deste retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="03782-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03782-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03782-111">Requirements</span></span>  
 <span data-ttu-id="03782-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03782-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03782-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="03782-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03782-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03782-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03782-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03782-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03782-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03782-116">See also</span></span>

- [<span data-ttu-id="03782-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="03782-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="03782-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="03782-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="03782-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="03782-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="03782-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="03782-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
