---
title: 'ICorProfilerCallback8: método ynamicMethodJITCompilationStarted de:D'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136457"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="8fda3-102">ICorProfilerCallback8: método ynamicMethodJITCompilationStarted de:D</span><span class="sxs-lookup"><span data-stu-id="8fda3-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="8fda3-103">[Com suporte no .NET Framework 4,7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8fda3-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="8fda3-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for iniciada.</span><span class="sxs-lookup"><span data-stu-id="8fda3-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fda3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fda3-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fda3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fda3-106">Parameters</span></span>  
<span data-ttu-id="8fda3-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8fda3-107">[in] `functionId`</span></span>  
<span data-ttu-id="8fda3-108">O identificador da função na memória para a qual a compilação JIT é iniciada.</span><span class="sxs-lookup"><span data-stu-id="8fda3-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="8fda3-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="8fda3-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="8fda3-110">`true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8fda3-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="8fda3-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="8fda3-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="8fda3-112">Um ponteiro para o primeiro byte do cabeçalho IL do método.</span><span class="sxs-lookup"><span data-stu-id="8fda3-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="8fda3-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="8fda3-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="8fda3-114">O número de bytes no cabeçalho IL.</span><span class="sxs-lookup"><span data-stu-id="8fda3-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="8fda3-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8fda3-115">Remarks</span></span>  

<span data-ttu-id="8fda3-116">Esse retorno de chamada é disparado sempre que um método dinâmico é compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="8fda3-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="8fda3-117">Isso inclui vários stubs IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="8fda3-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="8fda3-118">Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="8fda3-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="8fda3-119">`functionId` valores não podem ser usados para resolver seus tokens de metadados, porque métodos dinâmicos não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="8fda3-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="8fda3-120">O ponteiro de `pILHeader` só é válido durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8fda3-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="8fda3-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8fda3-121">Requirements</span></span>  
 <span data-ttu-id="8fda3-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fda3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fda3-123">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8fda3-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fda3-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fda3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fda3-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8fda3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fda3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fda3-126">See also</span></span>

- [<span data-ttu-id="8fda3-127">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="8fda3-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="8fda3-128">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="8fda3-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
