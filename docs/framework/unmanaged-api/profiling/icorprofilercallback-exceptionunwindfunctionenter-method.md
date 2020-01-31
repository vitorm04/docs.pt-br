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
ms.openlocfilehash: 367584a01e368dc591c2e93acfcc6574f2fa1ec0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866314"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="9e1fd-102">Método ICorProfilerCallback::ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="9e1fd-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="9e1fd-103">Notifica o criador de perfil de que a fase de desenrolamento da manipulação de exceções começou a desenrolar uma função.</span><span class="sxs-lookup"><span data-stu-id="9e1fd-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e1fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e1fd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e1fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e1fd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9e1fd-106">\[em] a ID da função que está sendo desbobinada.</span><span class="sxs-lookup"><span data-stu-id="9e1fd-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e1fd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e1fd-107">Remarks</span></span>  
 <span data-ttu-id="9e1fd-108">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="9e1fd-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9e1fd-109">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="9e1fd-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9e1fd-110">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9e1fd-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e1fd-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9e1fd-111">Requirements</span></span>  
 <span data-ttu-id="9e1fd-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e1fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e1fd-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e1fd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e1fd-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e1fd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e1fd-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e1fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1fd-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="9e1fd-116">See also</span></span>

- [<span data-ttu-id="9e1fd-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9e1fd-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9e1fd-118">Método ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="9e1fd-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
