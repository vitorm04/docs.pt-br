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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a181ca2da8385107d63cd94ea832846c4211ad5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650380"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="07cf4-102">Método ICorProfilerCallback3::ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="07cf4-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="07cf4-103">Chamado pelo common language runtime (CLR) para indicar que o criador de perfil agora pode chamar o [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) e [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) métodos de recuperação do atraso.</span><span class="sxs-lookup"><span data-stu-id="07cf4-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cf4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07cf4-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="07cf4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="07cf4-105">Remarks</span></span>  
 <span data-ttu-id="07cf4-106">O `ProfilerAttachComplete` retorno de chamada é emitido após o [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="07cf4-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="07cf4-107">Ele indica o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07cf4-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="07cf4-108">Os retornos de chamada que foram solicitados pelo criador de perfil em `InitializeForAttach` foram ativadas.</span><span class="sxs-lookup"><span data-stu-id="07cf4-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="07cf4-109">O criador de perfil agora pode executar o ajuste os IDs associados sem estar preocupado com as notificações ausentes.</span><span class="sxs-lookup"><span data-stu-id="07cf4-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="07cf4-110">O CLR ignora o valor de retorno desse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="07cf4-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cf4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07cf4-111">Requirements</span></span>  
 <span data-ttu-id="07cf4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07cf4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07cf4-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07cf4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07cf4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07cf4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07cf4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cf4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cf4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07cf4-116">See also</span></span>

- [<span data-ttu-id="07cf4-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="07cf4-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="07cf4-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="07cf4-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="07cf4-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="07cf4-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="07cf4-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="07cf4-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
