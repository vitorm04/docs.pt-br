---
title: Método ICorProfilerCallback::RuntimeResumeStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b163d41280c8ea49554cecb845c4be757f55dfc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168084"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="64fbd-102">Método ICorProfilerCallback::RuntimeResumeStarted</span><span class="sxs-lookup"><span data-stu-id="64fbd-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="64fbd-103">Notifica o criador de perfil que o tempo de execução está continuando todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="64fbd-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64fbd-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="64fbd-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64fbd-105">Requirements</span></span>  
 <span data-ttu-id="64fbd-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64fbd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64fbd-107">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64fbd-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64fbd-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64fbd-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="64fbd-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="64fbd-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64fbd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64fbd-110">See also</span></span>

- [<span data-ttu-id="64fbd-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="64fbd-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="64fbd-112">Método RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="64fbd-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
