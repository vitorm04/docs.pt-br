---
title: Método ICorProfilerCallback::ExceptionSearchCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb0e4d3e22ffc3619a6c5281ab5d72efeda921d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450597"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="28abd-102">Método ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="28abd-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="28abd-103">Notifica o criador de perfil que a fase de pesquisa de tratamento de exceção foi localizado um manipulador para a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="28abd-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28abd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28abd-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28abd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28abd-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="28abd-106">[in] A ID da função que contém o manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="28abd-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28abd-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28abd-107">Requirements</span></span>  
 <span data-ttu-id="28abd-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28abd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28abd-109">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28abd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28abd-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28abd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28abd-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28abd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28abd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28abd-112">See Also</span></span>  
 [<span data-ttu-id="28abd-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="28abd-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
