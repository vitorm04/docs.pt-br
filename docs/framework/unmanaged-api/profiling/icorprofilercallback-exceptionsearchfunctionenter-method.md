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
ms.openlocfilehash: d310ad49debf69d1139f2286cb76e51e9b622ea9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445346"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="964c1-102">Método ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="964c1-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="964c1-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span><span class="sxs-lookup"><span data-stu-id="964c1-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="964c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="964c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="964c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="964c1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="964c1-106">[in] The ID of the function that has been entered.</span><span class="sxs-lookup"><span data-stu-id="964c1-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="964c1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="964c1-107">Requirements</span></span>  
 <span data-ttu-id="964c1-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="964c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="964c1-109">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="964c1-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="964c1-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="964c1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="964c1-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964c1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="964c1-112">See also</span></span>

- [<span data-ttu-id="964c1-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="964c1-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="964c1-114">Método ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="964c1-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
