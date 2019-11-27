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
ms.openlocfilehash: f57a3ed70267de65daed85305ad7d623b4ca0337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448022"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="8761d-102">Método ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="8761d-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="8761d-103">Notifica o criador de perfil de que o tempo de execução começou a descarregar uma função.</span><span class="sxs-lookup"><span data-stu-id="8761d-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8761d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8761d-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8761d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8761d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8761d-106">no A ID da função que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="8761d-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8761d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8761d-107">Remarks</span></span>  
 <span data-ttu-id="8761d-108">O valor do parâmetro `functionId` não é mais válido depois que esse método retorna ao chamador.</span><span class="sxs-lookup"><span data-stu-id="8761d-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8761d-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8761d-109">Requirements</span></span>  
 <span data-ttu-id="8761d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8761d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8761d-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8761d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8761d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8761d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8761d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8761d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8761d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8761d-114">See also</span></span>

- [<span data-ttu-id="8761d-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8761d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
