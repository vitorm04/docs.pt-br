---
title: Método ICorProfilerCallback::ExceptionThrown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3358150754fd039d6e6107efd61c8d950fd02f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="48e2a-102">Método ICorProfilerCallback::ExceptionThrown</span><span class="sxs-lookup"><span data-stu-id="48e2a-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="48e2a-103">Notifica o criador de perfil que uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="48e2a-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48e2a-104">Essa função é chamada somente se a exceção atinge o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="48e2a-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e2a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48e2a-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48e2a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48e2a-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="48e2a-107">[in] A ID do objeto que causou a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="48e2a-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48e2a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="48e2a-108">Remarks</span></span>  
 <span data-ttu-id="48e2a-109">O criador de perfil não deve bloquear em sua implementação deste método porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="48e2a-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="48e2a-110">Se o criador de perfil bloqueia aqui e uma tentativa de coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="48e2a-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="48e2a-111">A implementação do criador de perfil do método não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="48e2a-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e2a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48e2a-112">Requirements</span></span>  
 <span data-ttu-id="48e2a-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e2a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e2a-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48e2a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48e2a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e2a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e2a-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e2a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48e2a-117">See Also</span></span>  
 [<span data-ttu-id="48e2a-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="48e2a-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
