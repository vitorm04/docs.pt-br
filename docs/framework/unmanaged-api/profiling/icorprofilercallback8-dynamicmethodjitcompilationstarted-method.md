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
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498993"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="9129d-102">ICorProfilerCallback8: método ynamicMethodJITCompilationStarted de:D</span><span class="sxs-lookup"><span data-stu-id="9129d-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="9129d-103">[Com suporte no .NET Framework 4,7 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="9129d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="9129d-104">Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for iniciada.</span><span class="sxs-lookup"><span data-stu-id="9129d-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9129d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9129d-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9129d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9129d-106">Parameters</span></span>  
<span data-ttu-id="9129d-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="9129d-107">[in] `functionId`</span></span>  
<span data-ttu-id="9129d-108">O identificador da função na memória para a qual a compilação JIT é iniciada.</span><span class="sxs-lookup"><span data-stu-id="9129d-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="9129d-109">[in] `fIsSafeToBlock` 
 `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; `false`para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9129d-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="9129d-110">[in] `pILHeader` Um ponteiro para o primeiro byte do cabeçalho IL do método.</span><span class="sxs-lookup"><span data-stu-id="9129d-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="9129d-111">[in] `cbILHeader` O número de bytes no cabeçalho IL.</span><span class="sxs-lookup"><span data-stu-id="9129d-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="9129d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9129d-112">Remarks</span></span>  

<span data-ttu-id="9129d-113">Esse retorno de chamada é disparado sempre que um método dinâmico é compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="9129d-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="9129d-114">Isso inclui vários stubs IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="9129d-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="9129d-115">Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.</span><span class="sxs-lookup"><span data-stu-id="9129d-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="9129d-116">`functionId`os valores não podem ser usados para resolver seus tokens de metadados, pois os métodos dinâmicos não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="9129d-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="9129d-117">O `pILHeader` ponteiro só é válido durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9129d-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="9129d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9129d-118">Requirements</span></span>  
 <span data-ttu-id="9129d-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9129d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9129d-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9129d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9129d-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9129d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9129d-122">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9129d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9129d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="9129d-123">See also</span></span>

- [<span data-ttu-id="9129d-124">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="9129d-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="9129d-125">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="9129d-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
