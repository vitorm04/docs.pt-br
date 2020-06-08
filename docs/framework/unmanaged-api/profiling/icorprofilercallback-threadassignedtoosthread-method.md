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
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503166"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="2c0e2-102">Método ICorProfilerCallback::ThreadAssignedToOSThread</span><span class="sxs-lookup"><span data-stu-id="2c0e2-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="2c0e2-103">Notifica o criador de perfil de que um thread gerenciado está sendo implementado usando um determinado thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2c0e2-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c0e2-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c0e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c0e2-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="2c0e2-106">no O identificador do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2c0e2-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="2c0e2-107">no O identificador do thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2c0e2-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c0e2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c0e2-108">Remarks</span></span>  
 <span data-ttu-id="2c0e2-109">O `ThreadAssignedToOSThread` retorno de chamada existe para que o criador de perfil possa manter um mapeamento preciso entre fibras de threads do sistema operacional para threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2c0e2-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c0e2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c0e2-110">Requirements</span></span>  
 <span data-ttu-id="2c0e2-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0e2-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c0e2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c0e2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c0e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c0e2-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0e2-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c0e2-115">See also</span></span>

- [<span data-ttu-id="2c0e2-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2c0e2-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
