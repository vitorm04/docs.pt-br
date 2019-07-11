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
ms.openlocfilehash: cb95c11900b84b78a3f862bcb73f0700aaabeeaa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755983"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="337ca-102">Método ICorProfilerCallback::ExceptionThrown</span><span class="sxs-lookup"><span data-stu-id="337ca-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="337ca-103">Notifica o criador de perfil que foi lançada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="337ca-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="337ca-104">Essa função é chamada somente se a exceção atingir o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="337ca-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="337ca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="337ca-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="337ca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="337ca-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="337ca-107">[in] A ID do objeto que causou a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="337ca-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="337ca-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="337ca-108">Remarks</span></span>  
 <span data-ttu-id="337ca-109">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="337ca-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="337ca-110">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="337ca-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="337ca-111">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="337ca-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="337ca-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="337ca-112">Requirements</span></span>  
 <span data-ttu-id="337ca-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="337ca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="337ca-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="337ca-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="337ca-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="337ca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="337ca-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="337ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337ca-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="337ca-117">See also</span></span>

- [<span data-ttu-id="337ca-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="337ca-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
