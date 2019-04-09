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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9b47e1d1bfa1d8f6c970e95fe25f62a690d3b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143854"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="d9ae5-102">Método ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="d9ae5-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="d9ae5-103">Notifica o criador de perfil que o controle está sendo passado para o apropriada `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ae5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9ae5-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ae5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9ae5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d9ae5-106">[in] O identificador da função que contém o `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="d9ae5-107">[in] O identificador da exceção que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9ae5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9ae5-108">Remarks</span></span>  
 <span data-ttu-id="d9ae5-109">O `ExceptionCatcherEnter` método é chamado somente se o ponto de captura está no código compilado com o compilador just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d9ae5-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="d9ae5-110">Uma exceção que é detectada em código não gerenciado ou no código interno do tempo de execução não chamará essa notificação.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="d9ae5-111">O `objectId` valor é passado novamente, pois uma coleta de lixo poderia ter movido o objeto desde o `ExceptionThrown` notificação.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="d9ae5-112">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d9ae5-113">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d9ae5-114">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="d9ae5-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ae5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9ae5-115">Requirements</span></span>  
 <span data-ttu-id="d9ae5-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ae5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ae5-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9ae5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9ae5-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9ae5-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d9ae5-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d9ae5-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9ae5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9ae5-120">See also</span></span>

- [<span data-ttu-id="d9ae5-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d9ae5-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d9ae5-122">Método ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="d9ae5-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
