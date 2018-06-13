---
title: Método ICorProfilerCallback8::DynamicMethodJITCompilationFinished
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
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454991"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="f807a-102">Método ICorProfilerCallback8::DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="f807a-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="f807a-103">[Com suporte nas versões posteriores e 4.7 do .NET Framework]</span><span class="sxs-lookup"><span data-stu-id="f807a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="f807a-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f807a-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f807a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f807a-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f807a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f807a-106">Parameters</span></span>  
<span data-ttu-id="f807a-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="f807a-107">[in] `functionId`</span></span>  
<span data-ttu-id="f807a-108">O identificador da função na memória para o qual JIT compilação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="f807a-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="f807a-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="f807a-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="f807a-110">Um valor que indica se a compilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f807a-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="f807a-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="f807a-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="f807a-112">`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; `false` para indicar que a bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f807a-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f807a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f807a-113">Remarks</span></span>  

<span data-ttu-id="f807a-114">Esse retorno de chamada é disparado sempre que a compilação JIT de um método dinâmico foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f807a-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="f807a-115">Isso inclui várias stubs de IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="f807a-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="f807a-116">Sua meta é fornecer informações suficientes para identificar o método compilado para usuários gravadores de criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f807a-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="f807a-117">`functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos têm sem metadados.</span><span class="sxs-lookup"><span data-stu-id="f807a-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f807a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f807a-118">Requirements</span></span>  
 <span data-ttu-id="f807a-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f807a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f807a-120">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f807a-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f807a-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f807a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f807a-122">**Versões do .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f807a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f807a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f807a-123">See Also</span></span>  
 [<span data-ttu-id="f807a-124">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="f807a-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [<span data-ttu-id="f807a-125">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="f807a-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
