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
ms.openlocfilehash: dc0d0e6094d5c4668126714b36915cfa4512c1b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517624"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="a889e-102">Método ICorProfilerCallback::RuntimeResumeStarted</span><span class="sxs-lookup"><span data-stu-id="a889e-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="a889e-103">Notifica o criador de perfil que o tempo de execução está continuando todos os threads de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a889e-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a889e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a889e-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a889e-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a889e-105">Requirements</span></span>  
 <span data-ttu-id="a889e-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a889e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a889e-107">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a889e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a889e-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a889e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a889e-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a889e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a889e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a889e-110">See also</span></span>
- [<span data-ttu-id="a889e-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a889e-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a889e-112">Método RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="a889e-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
