---
title: Método ICorProfilerCallback::RemotingServerInvocationReturned
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3f32b9ab9b4e29dd101729dc43cde03985f5994
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="28d47-102">Método ICorProfilerCallback::RemotingServerInvocationReturned</span><span class="sxs-lookup"><span data-stu-id="28d47-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="28d47-103">Notifica o criador de perfil que o processo foi concluído invocando um método em resposta a uma solicitação de invocação de método remoto.</span><span class="sxs-lookup"><span data-stu-id="28d47-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28d47-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="28d47-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28d47-105">Requirements</span></span>  
 <span data-ttu-id="28d47-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d47-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d47-107">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28d47-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28d47-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28d47-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d47-109">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d47-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d47-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28d47-110">See Also</span></span>  
 [<span data-ttu-id="28d47-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="28d47-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
