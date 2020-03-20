---
title: iCorProfilerCallback9::DynamicMethodDes Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177027"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="ee75c-102">iCorProfilerCallback9::DynamicMethodDes Method</span><span class="sxs-lookup"><span data-stu-id="ee75c-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="ee75c-103">[Suportado nas versões .NET Framework 4.7.2 e posteriores]</span><span class="sxs-lookup"><span data-stu-id="ee75c-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="ee75c-104">Notifica o profiler sempre que um método dinâmico é coletado e posteriormente descarregado.</span><span class="sxs-lookup"><span data-stu-id="ee75c-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee75c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee75c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee75c-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee75c-106">Parameters</span></span>  
<span data-ttu-id="ee75c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="ee75c-107">[in] `functionId`</span></span>  
<span data-ttu-id="ee75c-108">O identificador da função in-memory que foi coletado e descarregado lixo.</span><span class="sxs-lookup"><span data-stu-id="ee75c-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee75c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee75c-109">Requirements</span></span>  
 <span data-ttu-id="ee75c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee75c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee75c-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee75c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee75c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee75c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee75c-113">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee75c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee75c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee75c-114">See also</span></span>

- [<span data-ttu-id="ee75c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="ee75c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="ee75c-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="ee75c-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="ee75c-117">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="ee75c-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="ee75c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="ee75c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
