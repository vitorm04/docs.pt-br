---
title: Método ICorProfilerCallback::ExceptionUnwindFunctionEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0451ceac3018a3bab697a8ac82f5ef84f1026c6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597167"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="58338-102">Método ICorProfilerCallback::ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="58338-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="58338-103">Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceções começou a uma função de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="58338-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58338-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58338-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58338-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58338-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="58338-106">[in] A ID da função que está sendo desenrolada.</span><span class="sxs-lookup"><span data-stu-id="58338-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58338-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="58338-107">Remarks</span></span>  
 <span data-ttu-id="58338-108">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="58338-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="58338-109">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="58338-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="58338-110">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="58338-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58338-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58338-111">Requirements</span></span>  
 <span data-ttu-id="58338-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58338-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58338-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58338-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58338-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58338-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58338-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58338-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58338-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58338-116">See also</span></span>

- [<span data-ttu-id="58338-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="58338-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="58338-118">Método ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="58338-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
