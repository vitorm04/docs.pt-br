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
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499071"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="b230a-102">ICorProfilerCallback8: método ynamicMethodJITCompilationFinished de:D</span><span class="sxs-lookup"><span data-stu-id="b230a-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="b230a-103">[Com suporte no .NET Framework 4,7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="b230a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="b230a-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for concluída.</span><span class="sxs-lookup"><span data-stu-id="b230a-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b230a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b230a-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b230a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b230a-106">Parameters</span></span>  
<span data-ttu-id="b230a-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="b230a-107">[in] `functionId`</span></span>  
<span data-ttu-id="b230a-108">O identificador da função na memória para a qual a compilação JIT é iniciada.</span><span class="sxs-lookup"><span data-stu-id="b230a-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="b230a-109">[in] `hrStatus` Um valor que indica se a compilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b230a-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="b230a-110">[in] `fIsSafeToBlock` 
 `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; `false`para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b230a-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="b230a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b230a-111">Remarks</span></span>  

<span data-ttu-id="b230a-112">Esse retorno de chamada é disparado sempre que a compilação JIT de um método dinâmico é concluída.</span><span class="sxs-lookup"><span data-stu-id="b230a-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="b230a-113">Isso inclui vários stubs IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="b230a-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="b230a-114">Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="b230a-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="b230a-115">`functionId`os valores não podem ser usados para resolver seus tokens de metadados, pois os métodos dinâmicos não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="b230a-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="b230a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b230a-116">Requirements</span></span>  
 <span data-ttu-id="b230a-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b230a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b230a-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b230a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b230a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b230a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b230a-120">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b230a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b230a-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="b230a-121">See also</span></span>

- [<span data-ttu-id="b230a-122">Método DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="b230a-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="b230a-123">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="b230a-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
