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
ms.openlocfilehash: 1f16add7b5a9d18e0c1eb33209b609e9bf7e18b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445318"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="61e0b-102">Método ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="61e0b-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="61e0b-103">Notifica o criador de perfil de que a fase de desenrolamento da manipulação de exceção está inserindo uma cláusula `finally` contida na função especificada.</span><span class="sxs-lookup"><span data-stu-id="61e0b-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e0b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61e0b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61e0b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61e0b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="61e0b-106">no A ID da função que contém a cláusula `finally`.</span><span class="sxs-lookup"><span data-stu-id="61e0b-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e0b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="61e0b-107">Remarks</span></span>  
 <span data-ttu-id="61e0b-108">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="61e0b-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="61e0b-109">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="61e0b-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="61e0b-110">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="61e0b-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e0b-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="61e0b-111">Requirements</span></span>  
 <span data-ttu-id="61e0b-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e0b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e0b-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="61e0b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61e0b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61e0b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61e0b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61e0b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e0b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61e0b-116">See also</span></span>

- [<span data-ttu-id="61e0b-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="61e0b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="61e0b-118">Método GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="61e0b-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="61e0b-119">Método ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="61e0b-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
