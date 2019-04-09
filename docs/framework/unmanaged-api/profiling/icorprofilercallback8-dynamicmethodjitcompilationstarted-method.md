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
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142240"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="421a4-102">Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="421a4-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="421a4-103">[Com suporte no .NET Framework 4.7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="421a4-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="421a4-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="421a4-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="421a4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="421a4-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="421a4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="421a4-106">Parameters</span></span>  
<span data-ttu-id="421a4-107">[in]</span><span class="sxs-lookup"><span data-stu-id="421a4-107">[in]</span></span> `functionId`  
<span data-ttu-id="421a4-108">O identificador da função na memória para o qual JIT compilação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="421a4-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="421a4-109">[in]</span><span class="sxs-lookup"><span data-stu-id="421a4-109">[in]</span></span> `fIsSafeToBlock`   
`true` <span data-ttu-id="421a4-110">para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="421a4-110">to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="421a4-111">[in]</span><span class="sxs-lookup"><span data-stu-id="421a4-111">[in]</span></span> `pILHeader`    
<span data-ttu-id="421a4-112">Um ponteiro para o primeiro byte de cabeçalho de IL do método.</span><span class="sxs-lookup"><span data-stu-id="421a4-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="421a4-113">[in]</span><span class="sxs-lookup"><span data-stu-id="421a4-113">[in]</span></span> `cbILHeader`    
<span data-ttu-id="421a4-114">O número de bytes no cabeçalho de IL.</span><span class="sxs-lookup"><span data-stu-id="421a4-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="421a4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="421a4-115">Remarks</span></span>  

<span data-ttu-id="421a4-116">Esse retorno de chamada é acionado sempre que um método dinâmico é compilado em JIT.</span><span class="sxs-lookup"><span data-stu-id="421a4-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="421a4-117">Isso inclui várias stubs de IL e os métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="421a4-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="421a4-118">Sua meta é fornecer os gravadores de criador de perfil com informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="421a4-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> `functionId` <span data-ttu-id="421a4-119">valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos não têm nenhum metadado.</span><span class="sxs-lookup"><span data-stu-id="421a4-119">values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="421a4-120">O `pILHeader` ponteiro só é válido durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="421a4-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="421a4-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="421a4-121">Requirements</span></span>  
 <span data-ttu-id="421a4-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="421a4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="421a4-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="421a4-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="421a4-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="421a4-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="421a4-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="421a4-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="421a4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="421a4-126">See also</span></span>

- [<span data-ttu-id="421a4-127">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="421a4-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="421a4-128">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="421a4-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
