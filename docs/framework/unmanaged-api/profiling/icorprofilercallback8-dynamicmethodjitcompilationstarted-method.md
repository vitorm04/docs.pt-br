---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177040"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="a8554-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span><span class="sxs-lookup"><span data-stu-id="a8554-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="a8554-103">[Suportado nas versões .NET Framework 4.7 e posteriores]</span><span class="sxs-lookup"><span data-stu-id="a8554-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a8554-104">Notifica o profiler sempre que a compilação JIT de um método dinâmico foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="a8554-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8554-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8554-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8554-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8554-106">Parameters</span></span>  
<span data-ttu-id="a8554-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a8554-107">[in] `functionId`</span></span>  
<span data-ttu-id="a8554-108">O identificador da função in-memory para a qual a compilação JIT é iniciada.</span><span class="sxs-lookup"><span data-stu-id="a8554-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="a8554-109">[em] `fIsSafeToBlock` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o retorno do segmento de chamada a partir deste retorno de 
 `true` chamada; `false` para indicar que o bloqueio não afetará o funcionamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a8554-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="a8554-110">[em] `pILHeader` Um ponteiro para o primeiro byte do cabeçalho IL do método.</span><span class="sxs-lookup"><span data-stu-id="a8554-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="a8554-111">[em] `cbILHeader` O número de bytes no cabeçalho IL.</span><span class="sxs-lookup"><span data-stu-id="a8554-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8554-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8554-112">Remarks</span></span>  

<span data-ttu-id="a8554-113">Esse retorno de chamada é acionado sempre que um método dinâmico é compilado pelo JIT.</span><span class="sxs-lookup"><span data-stu-id="a8554-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="a8554-114">Isso inclui vários stubs IL e métodos LCG.</span><span class="sxs-lookup"><span data-stu-id="a8554-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a8554-115">Seu objetivo é fornecer aos escritores de profiler informações suficientes para identificar o método compilado aos usuários.</span><span class="sxs-lookup"><span data-stu-id="a8554-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a8554-116">`functionId`os valores não podem ser usados para resolver seus tokens de metadados, porque os métodos dinâmicos não têm metadados.</span><span class="sxs-lookup"><span data-stu-id="a8554-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="a8554-117">O `pILHeader` ponteiro só é válido durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a8554-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8554-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8554-118">Requirements</span></span>  
 <span data-ttu-id="a8554-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8554-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8554-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8554-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8554-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8554-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8554-122">**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8554-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8554-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8554-123">See also</span></span>

- [<span data-ttu-id="a8554-124">Método DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="a8554-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a8554-125">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="a8554-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
