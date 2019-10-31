---
title: 'ICorProfilerCallback9: método ynamicMethodUnloaded de:D'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 05a788179ff40a6889ed613b5f8659dd3f8e066f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196326"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="0982d-102">ICorProfilerCallback9: método ynamicMethodUnloaded de:D</span><span class="sxs-lookup"><span data-stu-id="0982d-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="0982d-103">[Com suporte no .NET Framework 4.7.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="0982d-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="0982d-104">Notifica o criador de perfil sempre que um método dinâmico é lixo coletado e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="0982d-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0982d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0982d-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0982d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0982d-106">Parameters</span></span>  
<span data-ttu-id="0982d-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="0982d-107">[in] `functionId`</span></span>  
<span data-ttu-id="0982d-108">O identificador da função na memória que foi coletada pelo lixo e descarregada.</span><span class="sxs-lookup"><span data-stu-id="0982d-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="0982d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0982d-109">Requirements</span></span>  
 <span data-ttu-id="0982d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0982d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0982d-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0982d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0982d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0982d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0982d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0982d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0982d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0982d-114">See also</span></span>

- [<span data-ttu-id="0982d-115">Método ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="0982d-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="0982d-116">Método ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="0982d-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="0982d-117">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="0982d-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="0982d-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="0982d-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
