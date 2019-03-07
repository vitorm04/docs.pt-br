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
ms.openlocfilehash: 658f5b7ede2895eaf774b2ef9cf7ca17f6682ac8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496788"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="b1895-102">Método ICorProfilerCallback9::DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="b1895-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="b1895-103">[Com suporte no .NET Framework 4.7.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="b1895-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="b1895-104">Notifica o criador de perfil sempre que um método dinâmico é lixo coletado e, subsequentemente, foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="b1895-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1895-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1895-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1895-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1895-106">Parameters</span></span>  
<span data-ttu-id="b1895-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="b1895-107">[in] `functionId`</span></span>  
<span data-ttu-id="b1895-108">O identificador da função na memória que tenha sido limpos e descarregado.</span><span class="sxs-lookup"><span data-stu-id="b1895-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="b1895-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1895-109">Requirements</span></span>  
 <span data-ttu-id="b1895-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1895-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1895-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1895-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1895-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1895-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1895-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b1895-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1895-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1895-114">See also</span></span>
- [<span data-ttu-id="b1895-115">Método ICorProfilerCallback8.DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="b1895-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="b1895-116">Método ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="b1895-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="b1895-117">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="b1895-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="b1895-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="b1895-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
