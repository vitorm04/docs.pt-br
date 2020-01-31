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
ms.openlocfilehash: c7b52954a6be449de0c3633f0ac648980c6d13f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865916"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="311f8-102">Método ICorProfilerCallback::RuntimeResumeStarted</span><span class="sxs-lookup"><span data-stu-id="311f8-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="311f8-103">Notifica o criador de perfil de que o tempo de execução está retomando todos os threads em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="311f8-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="311f8-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="311f8-105">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="311f8-105">Requirements</span></span>  
 <span data-ttu-id="311f8-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="311f8-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311f8-107">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="311f8-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="311f8-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="311f8-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="311f8-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="311f8-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311f8-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="311f8-110">See also</span></span>

- [<span data-ttu-id="311f8-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="311f8-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="311f8-112">Método RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="311f8-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
