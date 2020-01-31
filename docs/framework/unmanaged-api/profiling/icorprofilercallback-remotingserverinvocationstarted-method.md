---
title: Método ICorProfilerCallback::RemotingServerInvocationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 3571b429c3733a07a74d50f69ecf8987d75b034f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865981"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="e428e-102">Método ICorProfilerCallback::RemotingServerInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="e428e-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="e428e-103">Notifica o criador de perfil de que o processo está invocando um método em resposta a uma solicitação de invocação de método remoto.</span><span class="sxs-lookup"><span data-stu-id="e428e-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e428e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e428e-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e428e-105">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e428e-105">Requirements</span></span>  
 <span data-ttu-id="e428e-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e428e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e428e-107">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e428e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e428e-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e428e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e428e-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e428e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e428e-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="e428e-110">See also</span></span>

- [<span data-ttu-id="e428e-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e428e-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
