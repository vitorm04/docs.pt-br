---
title: "Método ICorProfilerCallback::ExceptionUnwindFunctionLeave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e420d27fa1bf122b794489b00853555a7005e69e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="b4ba2-102">Método ICorProfilerCallback::ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="b4ba2-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="b4ba2-103">Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceção concluiu a liberação de uma função.</span><span class="sxs-lookup"><span data-stu-id="b4ba2-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ba2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4ba2-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b4ba2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4ba2-105">Remarks</span></span>  
 <span data-ttu-id="b4ba2-106">Quando o `ExceptionUnwindFunctionLeave` método é chamado, a instância de função e seus dados de pilha são removidos da pilha.</span><span class="sxs-lookup"><span data-stu-id="b4ba2-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="b4ba2-107">O criador de perfil não deve bloquear durante esta chamada porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="b4ba2-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b4ba2-108">Se você tentar aqui os blocos do criador de perfil e uma coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="b4ba2-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b4ba2-109">Além disso, durante essa chamada, o criador de perfil não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b4ba2-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ba2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4ba2-110">Requirements</span></span>  
 <span data-ttu-id="b4ba2-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ba2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ba2-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4ba2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4ba2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ba2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ba2-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ba2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ba2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4ba2-115">See Also</span></span>  
 [<span data-ttu-id="b4ba2-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4ba2-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b4ba2-117">Método ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="b4ba2-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
