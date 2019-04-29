---
title: Método ICorProfilerCallback::ExceptionCatcherLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7f1b2756dd180cb0a701429978a34ea80447a86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598001"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="87853-102">Método ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="87853-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="87853-103">Notifica o criador de perfil que está sendo passado o controle fora apropriado `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="87853-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87853-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87853-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="87853-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="87853-105">Remarks</span></span>  
 <span data-ttu-id="87853-106">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="87853-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="87853-107">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="87853-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="87853-108">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="87853-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87853-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87853-109">Requirements</span></span>  
 <span data-ttu-id="87853-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87853-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87853-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87853-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87853-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87853-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87853-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87853-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87853-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87853-114">See also</span></span>

- [<span data-ttu-id="87853-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="87853-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="87853-116">Método ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="87853-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
