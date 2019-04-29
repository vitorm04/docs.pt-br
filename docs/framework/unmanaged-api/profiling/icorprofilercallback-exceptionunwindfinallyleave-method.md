---
title: Método ICorProfilerCallback::ExceptionUnwindFinallyLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ba62ab2c4df73b570fb1c76adaee44a2a2ce8c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597148"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="864b2-102">Método ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="864b2-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="864b2-103">Notifica o criador de perfil que a fase de desenrolamento de exceção tratamento deixou um `finally` cláusula.</span><span class="sxs-lookup"><span data-stu-id="864b2-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="864b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="864b2-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="864b2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="864b2-105">Remarks</span></span>  
 <span data-ttu-id="864b2-106">O criador de perfil não deve bloquear durante esta chamada porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="864b2-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="864b2-107">Se você tentar aqui os blocos do criador de perfil e uma coleta de lixo, o tempo de execução bloqueará até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="864b2-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="864b2-108">Além disso, durante esta chamada, o criador de perfil não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="864b2-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="864b2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="864b2-109">Requirements</span></span>  
 <span data-ttu-id="864b2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="864b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="864b2-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="864b2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="864b2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="864b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="864b2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="864b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864b2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="864b2-114">See also</span></span>

- [<span data-ttu-id="864b2-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="864b2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="864b2-116">Método ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="864b2-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
