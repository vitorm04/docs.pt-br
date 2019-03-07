---
title: Método ICorProfilerCallback::ExceptionUnwindFinallyEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caf546798f3928a2cf809bfec63c4b3cd959ee75
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466460"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="c5839-102">Método ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="c5839-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="c5839-103">Notifica o criador de perfil que a fase de desenrolamento de exceção de manipulação está inserindo um `finally` cláusula contida na função especificada.</span><span class="sxs-lookup"><span data-stu-id="c5839-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5839-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5839-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5839-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5839-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c5839-106">[in] A ID da função que contém o `finally` cláusula.</span><span class="sxs-lookup"><span data-stu-id="c5839-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5839-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5839-107">Remarks</span></span>  
 <span data-ttu-id="c5839-108">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="c5839-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c5839-109">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="c5839-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c5839-110">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="c5839-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5839-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5839-111">Requirements</span></span>  
 <span data-ttu-id="c5839-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5839-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5839-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5839-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5839-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5839-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5839-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5839-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5839-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5839-116">See also</span></span>
- [<span data-ttu-id="c5839-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c5839-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c5839-118">Método GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="c5839-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="c5839-119">Método ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="c5839-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
