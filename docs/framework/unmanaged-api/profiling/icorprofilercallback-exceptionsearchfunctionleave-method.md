---
title: Método ICorProfilerCallback::ExceptionSearchFunctionLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: 11ce99fe650f68b80c380c740472e5e0ac8904db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500176"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="060d3-102">Método ICorProfilerCallback::ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="060d3-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="060d3-103">Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções concluiu a pesquisa de uma função.</span><span class="sxs-lookup"><span data-stu-id="060d3-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="060d3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="060d3-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="060d3-105">Requirements</span></span>  
 <span data-ttu-id="060d3-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="060d3-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060d3-107">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="060d3-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="060d3-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="060d3-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="060d3-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060d3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060d3-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="060d3-110">See also</span></span>

- [<span data-ttu-id="060d3-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="060d3-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="060d3-112">Método ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="060d3-112">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
