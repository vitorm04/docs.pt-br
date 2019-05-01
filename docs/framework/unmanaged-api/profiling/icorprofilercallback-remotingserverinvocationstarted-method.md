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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c9a4aa165057f1345de2c6f5bda80e4317d06c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992141"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="0d9a7-102">Método ICorProfilerCallback::RemotingServerInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="0d9a7-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="0d9a7-103">Notifica o criador de perfil que o processo está invocando um método em resposta a uma solicitação de invocação de método remoto.</span><span class="sxs-lookup"><span data-stu-id="0d9a7-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d9a7-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0d9a7-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d9a7-105">Requirements</span></span>  
 <span data-ttu-id="0d9a7-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d9a7-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d9a7-107">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d9a7-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d9a7-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d9a7-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d9a7-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d9a7-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9a7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d9a7-110">See also</span></span>

- [<span data-ttu-id="0d9a7-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0d9a7-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
