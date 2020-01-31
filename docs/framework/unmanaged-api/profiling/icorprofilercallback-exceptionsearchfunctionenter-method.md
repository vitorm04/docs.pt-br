---
title: Método ICorProfilerCallback::ExceptionSearchFunctionEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: c09d896e59a6c336fbe4923dbe85f30b039d8c36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866395"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="12a95-102">Método ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="12a95-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="12a95-103">Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções começou a pesquisar uma função para localizar um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="12a95-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12a95-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12a95-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12a95-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="12a95-106">\[em] a ID da função que foi inserida.</span><span class="sxs-lookup"><span data-stu-id="12a95-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="12a95-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="12a95-107">Requirements</span></span>  
 <span data-ttu-id="12a95-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a95-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a95-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="12a95-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12a95-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12a95-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12a95-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a95-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a95-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="12a95-112">See also</span></span>

- [<span data-ttu-id="12a95-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="12a95-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="12a95-114">Método ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="12a95-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
