---
title: "Método ICorProfilerCallback::ExceptionUnwindFinallyEnter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3480761c2708fa2f15454a7a99c34e84ee34eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="8e490-102">Método ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="8e490-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="8e490-103">Notifica o criador de perfil que a fase de desenrolamento da exceção tratamento está inserindo um `finally` cláusula contida na função especificada.</span><span class="sxs-lookup"><span data-stu-id="8e490-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e490-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e490-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e490-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e490-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8e490-106">[in] A ID da função que contém o `finally` cláusula.</span><span class="sxs-lookup"><span data-stu-id="8e490-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e490-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e490-107">Remarks</span></span>  
 <span data-ttu-id="8e490-108">O criador de perfil não deve bloquear em sua implementação deste método porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="8e490-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8e490-109">Se o criador de perfil bloqueia aqui e uma tentativa de coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="8e490-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8e490-110">A implementação do criador de perfil do método não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8e490-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e490-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e490-111">Requirements</span></span>  
 <span data-ttu-id="8e490-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e490-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e490-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e490-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e490-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e490-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e490-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e490-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e490-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e490-116">See Also</span></span>  
 [<span data-ttu-id="8e490-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8e490-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8e490-118">Método GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="8e490-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="8e490-119">Método ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="8e490-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
