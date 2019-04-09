---
title: Método ICorProfilerCallback::ThreadAssignedToOSThread
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefcd4436a28fdf52cbe55da5d4bb7eea4449463
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158451"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="a479f-102">Método ICorProfilerCallback::ThreadAssignedToOSThread</span><span class="sxs-lookup"><span data-stu-id="a479f-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="a479f-103">Notifica o criador de perfil que um thread gerenciado está sendo implementado usando um thread de sistema operacional específico.</span><span class="sxs-lookup"><span data-stu-id="a479f-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a479f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a479f-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a479f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a479f-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="a479f-106">[in] O identificador do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a479f-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="a479f-107">[in] O identificador do thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a479f-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a479f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a479f-108">Remarks</span></span>  
 <span data-ttu-id="a479f-109">O `ThreadAssignedToOSThread` retorno de chamada existe para que o criador de perfil pode manter um mapeamento preciso em fibras de threads do sistema operacional para threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a479f-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a479f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a479f-110">Requirements</span></span>  
 <span data-ttu-id="a479f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a479f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a479f-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a479f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a479f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a479f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a479f-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a479f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a479f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a479f-115">See also</span></span>

- [<span data-ttu-id="a479f-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a479f-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
