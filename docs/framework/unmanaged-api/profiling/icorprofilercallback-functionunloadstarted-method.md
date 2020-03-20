---
title: Método ICorProfilerCallback::FunctionUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175155"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="5ca3e-102">Método ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="5ca3e-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="5ca3e-103">Notifica o profiler de que o tempo de execução começou a descarregar uma função.</span><span class="sxs-lookup"><span data-stu-id="5ca3e-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ca3e-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="5ca3e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ca3e-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="5ca3e-106">\[in] O ID da função que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="5ca3e-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ca3e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ca3e-107">Remarks</span></span>  
 <span data-ttu-id="5ca3e-108">O valor `functionId` do parâmetro não é mais válido após o retorno deste método ao chamador.</span><span class="sxs-lookup"><span data-stu-id="5ca3e-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ca3e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ca3e-109">Requirements</span></span>  
 <span data-ttu-id="5ca3e-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ca3e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ca3e-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ca3e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ca3e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ca3e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ca3e-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca3e-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ca3e-114">See also</span></span>

- [<span data-ttu-id="5ca3e-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5ca3e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
