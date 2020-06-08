---
title: Método ICorProfilerCallback::ExceptionCatcherEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 9d0ef4da4ba6c8db49bcb0b40911756f7d9db66d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500306"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="42e7e-102">Método ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="42e7e-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="42e7e-103">Notifica o criador de perfil que o controle está sendo passado para o `catch` bloco apropriado.</span><span class="sxs-lookup"><span data-stu-id="42e7e-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42e7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42e7e-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="42e7e-106">\[in] o identificador da função que contém o `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="42e7e-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="42e7e-107">\[in] o identificador da exceção que está sendo manipulada.</span><span class="sxs-lookup"><span data-stu-id="42e7e-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="42e7e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="42e7e-108">Remarks</span></span>  
 <span data-ttu-id="42e7e-109">O `ExceptionCatcherEnter` método será chamado somente se o ponto de captura estiver no código compilado com o compilador JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="42e7e-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="42e7e-110">Uma exceção que é capturada no código não gerenciado ou no código interno do tempo de execução não chamará essa notificação.</span><span class="sxs-lookup"><span data-stu-id="42e7e-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="42e7e-111">O `objectId` valor é passado novamente, pois uma coleta de lixo pode ter movido o objeto desde a `ExceptionThrown` notificação.</span><span class="sxs-lookup"><span data-stu-id="42e7e-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="42e7e-112">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="42e7e-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="42e7e-113">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="42e7e-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="42e7e-114">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="42e7e-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42e7e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42e7e-115">Requirements</span></span>  
 <span data-ttu-id="42e7e-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42e7e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42e7e-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="42e7e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42e7e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42e7e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42e7e-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42e7e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e7e-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="42e7e-120">See also</span></span>

- [<span data-ttu-id="42e7e-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="42e7e-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="42e7e-122">Método ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="42e7e-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
