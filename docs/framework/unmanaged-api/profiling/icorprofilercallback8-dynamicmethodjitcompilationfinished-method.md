---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cb54a714b9da72e8620b39690b4dcc9a3c21c2e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496853"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="8b769-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span><span class="sxs-lookup"><span data-stu-id="8b769-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="8b769-103">[Com suporte no .NET Framework 4.7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8b769-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="8b769-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi concluída.</span><span class="sxs-lookup"><span data-stu-id="8b769-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b769-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b769-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b769-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b769-106">Parameters</span></span>  
<span data-ttu-id="8b769-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8b769-107">[in] `functionId`</span></span>  
<span data-ttu-id="8b769-108">O identificador da função na memória para o qual JIT compilação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="8b769-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="8b769-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="8b769-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="8b769-110">Um valor que indica se a compilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8b769-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="8b769-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="8b769-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="8b769-112">`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8b769-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="8b769-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b769-113">Remarks</span></span>  

<span data-ttu-id="8b769-114">Esse retorno de chamada é acionado sempre que a compilação JIT de um método dinâmico foi concluída.</span><span class="sxs-lookup"><span data-stu-id="8b769-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="8b769-115">Isso inclui várias stubs de IL e os métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="8b769-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="8b769-116">Sua meta é fornecer os gravadores de criador de perfil com informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="8b769-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="8b769-117">`functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos não têm nenhum metadado.</span><span class="sxs-lookup"><span data-stu-id="8b769-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b769-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b769-118">Requirements</span></span>  
 <span data-ttu-id="8b769-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b769-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b769-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b769-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b769-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b769-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b769-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8b769-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b769-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b769-123">See also</span></span>
- [<span data-ttu-id="8b769-124">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="8b769-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8b769-125">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="8b769-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
