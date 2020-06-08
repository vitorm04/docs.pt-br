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
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498967"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="15b74-102">ICorProfilerCallback9: método ynamicMethodUnloaded de:D</span><span class="sxs-lookup"><span data-stu-id="15b74-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="15b74-103">[Com suporte no .NET Framework 4.7.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="15b74-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="15b74-104">Notifica o criador de perfil sempre que um método dinâmico é lixo coletado e subsequentemente descarregado.</span><span class="sxs-lookup"><span data-stu-id="15b74-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b74-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15b74-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15b74-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15b74-106">Parameters</span></span>  
<span data-ttu-id="15b74-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="15b74-107">[in] `functionId`</span></span>  
<span data-ttu-id="15b74-108">O identificador da função na memória que foi coletada pelo lixo e descarregada.</span><span class="sxs-lookup"><span data-stu-id="15b74-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="15b74-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15b74-109">Requirements</span></span>  
 <span data-ttu-id="15b74-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b74-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b74-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15b74-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15b74-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15b74-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15b74-113">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15b74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b74-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="15b74-114">See also</span></span>

- [<span data-ttu-id="15b74-115">Método ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="15b74-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="15b74-116">Método ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="15b74-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="15b74-117">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="15b74-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="15b74-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="15b74-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
