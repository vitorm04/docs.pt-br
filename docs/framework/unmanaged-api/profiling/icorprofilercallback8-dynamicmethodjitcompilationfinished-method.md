---
title: 'ICorProfilerCallback8: método ynamicMethodJITCompilationFinished de:D'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136578"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="daf1d-102">ICorProfilerCallback8: método ynamicMethodJITCompilationFinished de:D</span><span class="sxs-lookup"><span data-stu-id="daf1d-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="daf1d-103">[Com suporte no .NET Framework 4,7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="daf1d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="daf1d-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for concluída.</span><span class="sxs-lookup"><span data-stu-id="daf1d-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf1d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daf1d-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daf1d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="daf1d-106">Parameters</span></span>  
<span data-ttu-id="daf1d-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="daf1d-107">[in] `functionId`</span></span>  
<span data-ttu-id="daf1d-108">O identificador da função na memória para a qual a compilação JIT é iniciada.</span><span class="sxs-lookup"><span data-stu-id="daf1d-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="daf1d-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="daf1d-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="daf1d-110">Um valor que indica se a compilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="daf1d-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="daf1d-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="daf1d-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="daf1d-112">`true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="daf1d-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="daf1d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="daf1d-113">Remarks</span></span>  

<span data-ttu-id="daf1d-114">Esse retorno de chamada é disparado sempre que a compilação JIT de um método dinâmico é concluída.</span><span class="sxs-lookup"><span data-stu-id="daf1d-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="daf1d-115">Isso inclui vários stubs IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="daf1d-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="daf1d-116">Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="daf1d-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="daf1d-117">`functionId` valores não podem ser usados para resolver seus tokens de metadados, porque métodos dinâmicos não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="daf1d-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="daf1d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="daf1d-118">Requirements</span></span>  
 <span data-ttu-id="daf1d-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daf1d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daf1d-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="daf1d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="daf1d-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daf1d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daf1d-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="daf1d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf1d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="daf1d-123">See also</span></span>

- [<span data-ttu-id="daf1d-124">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="daf1d-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="daf1d-125">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="daf1d-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
