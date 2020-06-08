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
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500189"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="8e351-102">Método ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="8e351-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="8e351-103">Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções começou a pesquisar uma função para localizar um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="8e351-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e351-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e351-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e351-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e351-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8e351-106">\[in] a ID da função que foi inserida.</span><span class="sxs-lookup"><span data-stu-id="8e351-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="8e351-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e351-107">Requirements</span></span>  
 <span data-ttu-id="8e351-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e351-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e351-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8e351-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e351-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e351-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e351-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e351-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e351-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e351-112">See also</span></span>

- [<span data-ttu-id="8e351-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8e351-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8e351-114">Método ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="8e351-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
