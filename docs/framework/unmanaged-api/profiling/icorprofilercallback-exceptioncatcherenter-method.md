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
ms.openlocfilehash: 9c9cd0b042dc22f35c38e349ab8881dafc602731
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445021"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="19853-102">Método ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="19853-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="19853-103">Notifica o criador de perfil que o controle está sendo passado para o bloco de `catch` apropriado.</span><span class="sxs-lookup"><span data-stu-id="19853-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19853-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19853-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19853-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19853-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="19853-106">no O identificador da função que contém o bloco de `catch`.</span><span class="sxs-lookup"><span data-stu-id="19853-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="19853-107">no O identificador da exceção que está sendo manipulada.</span><span class="sxs-lookup"><span data-stu-id="19853-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19853-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="19853-108">Remarks</span></span>  
 <span data-ttu-id="19853-109">O método `ExceptionCatcherEnter` será chamado somente se o ponto de captura estiver no código compilado com o compilador JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="19853-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="19853-110">Uma exceção que é capturada no código não gerenciado ou no código interno do tempo de execução não chamará essa notificação.</span><span class="sxs-lookup"><span data-stu-id="19853-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="19853-111">O valor de `objectId` é passado novamente, pois uma coleta de lixo pode ter movido o objeto desde a notificação de `ExceptionThrown`.</span><span class="sxs-lookup"><span data-stu-id="19853-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="19853-112">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="19853-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="19853-113">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="19853-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="19853-114">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="19853-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19853-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="19853-115">Requirements</span></span>  
 <span data-ttu-id="19853-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19853-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19853-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="19853-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19853-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19853-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19853-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19853-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19853-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19853-120">See also</span></span>

- [<span data-ttu-id="19853-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="19853-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="19853-122">Método ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="19853-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
