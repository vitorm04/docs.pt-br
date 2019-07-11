---
title: Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a60f074ce0081df07a61d0b832d542c8873776f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757987"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="3b212-102">Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="3b212-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="3b212-103">[Com suporte no .NET Framework 4.7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="3b212-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="3b212-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="3b212-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b212-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b212-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b212-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b212-106">Parameters</span></span>  
<span data-ttu-id="3b212-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="3b212-107">[in] `functionId`</span></span>  
<span data-ttu-id="3b212-108">O identificador da função na memória para o qual JIT compilação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="3b212-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="3b212-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="3b212-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="3b212-110">`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b212-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="3b212-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="3b212-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="3b212-112">Um ponteiro para o primeiro byte de cabeçalho de IL do método.</span><span class="sxs-lookup"><span data-stu-id="3b212-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="3b212-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="3b212-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="3b212-114">O número de bytes no cabeçalho de IL.</span><span class="sxs-lookup"><span data-stu-id="3b212-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="3b212-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b212-115">Remarks</span></span>  

<span data-ttu-id="3b212-116">Esse retorno de chamada é acionado sempre que um método dinâmico é compilado em JIT.</span><span class="sxs-lookup"><span data-stu-id="3b212-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="3b212-117">Isso inclui várias stubs de IL e os métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="3b212-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="3b212-118">Sua meta é fornecer os gravadores de criador de perfil com informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="3b212-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="3b212-119">`functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos não têm nenhum metadado.</span><span class="sxs-lookup"><span data-stu-id="3b212-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="3b212-120">O `pILHeader` ponteiro só é válido durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3b212-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b212-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b212-121">Requirements</span></span>  
 <span data-ttu-id="3b212-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b212-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b212-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b212-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b212-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b212-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b212-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3b212-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b212-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b212-126">See also</span></span>

- [<span data-ttu-id="3b212-127">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="3b212-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="3b212-128">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="3b212-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
