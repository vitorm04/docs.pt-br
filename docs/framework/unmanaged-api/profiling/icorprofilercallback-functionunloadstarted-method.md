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
ms.openlocfilehash: 320aaf074452fd02cd8ee8e80194a4c35b831eb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503374"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="d2d8a-102">Método ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="d2d8a-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="d2d8a-103">Notifica o criador de perfil de que o tempo de execução começou a descarregar uma função.</span><span class="sxs-lookup"><span data-stu-id="d2d8a-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2d8a-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="d2d8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2d8a-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="d2d8a-106">\[in] a ID da função que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="d2d8a-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2d8a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2d8a-107">Remarks</span></span>  
 <span data-ttu-id="d2d8a-108">O valor do `functionId` parâmetro não é mais válido depois que esse método retorna ao chamador.</span><span class="sxs-lookup"><span data-stu-id="d2d8a-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d8a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2d8a-109">Requirements</span></span>  
 <span data-ttu-id="d2d8a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d8a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d8a-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d2d8a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2d8a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2d8a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2d8a-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d8a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2d8a-114">See also</span></span>

- [<span data-ttu-id="d2d8a-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d2d8a-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
