---
title: "Método ICorProfilerCallback::ThreadAssignedToOSThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c70de2b53fd428361d5404aa406d2b2be67d0914
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="e5f66-102">Método ICorProfilerCallback::ThreadAssignedToOSThread</span><span class="sxs-lookup"><span data-stu-id="e5f66-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="e5f66-103">Notifica o criador de perfil que um thread gerenciado está sendo implementado usando um thread de sistema operacional específico.</span><span class="sxs-lookup"><span data-stu-id="e5f66-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5f66-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5f66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5f66-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="e5f66-106">[in] O identificador do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e5f66-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="e5f66-107">[in] O identificador de thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e5f66-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5f66-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5f66-108">Remarks</span></span>  
 <span data-ttu-id="e5f66-109">O `ThreadAssignedToOSThread` retorno de chamada existe para que o criador de perfil pode manter um mapeamento preciso em fibras de threads do sistema operacional para threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e5f66-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f66-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5f66-110">Requirements</span></span>  
 <span data-ttu-id="e5f66-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5f66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f66-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5f66-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5f66-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5f66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5f66-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f66-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5f66-115">See Also</span></span>  
 [<span data-ttu-id="e5f66-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e5f66-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
