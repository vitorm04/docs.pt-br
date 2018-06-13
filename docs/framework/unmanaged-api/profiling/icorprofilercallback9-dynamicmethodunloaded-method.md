---
title: Método ICorProfilerCallback9::DynamicMethodUnloaded
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452397"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="47087-102">Método ICorProfilerCallback9::DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="47087-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="47087-103">[Com suporte nas versões posteriores e 4.7.2 do .NET Framework]</span><span class="sxs-lookup"><span data-stu-id="47087-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="47087-104">Notifica o criador de perfil sempre que um método dinâmico é lixo coletado e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="47087-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47087-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47087-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47087-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47087-106">Parameters</span></span>  
<span data-ttu-id="47087-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="47087-107">[in] `functionId`</span></span>  
<span data-ttu-id="47087-108">O identificador da função na memória que foram limpos e descarregado.</span><span class="sxs-lookup"><span data-stu-id="47087-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="47087-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47087-109">Requirements</span></span>  
 <span data-ttu-id="47087-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47087-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47087-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47087-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47087-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47087-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47087-113">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="47087-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47087-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47087-114">See Also</span></span>  
[<span data-ttu-id="47087-115">Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="47087-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[<span data-ttu-id="47087-116">Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="47087-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
<span data-ttu-id="47087-117">[Interface ICorProfilerCallback9](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="47087-117">[ICorProfilerCallback9 Interface](icorprofilercallback9-interface.md) </span></span>  
[<span data-ttu-id="47087-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="47087-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
