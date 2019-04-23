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
ms.openlocfilehash: e41378b314b91f42fca9d1039d3011b5eaafe502
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074294"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="4196a-102">Método ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="4196a-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="4196a-103">Notifica o criador de perfil que a fase de pesquisa de manipulação de exceção foi localizado um manipulador para a exceção que foi gerada.</span><span class="sxs-lookup"><span data-stu-id="4196a-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4196a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4196a-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4196a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4196a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4196a-106">[in] A ID da função que contém o manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="4196a-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4196a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4196a-107">Requirements</span></span>  
 <span data-ttu-id="4196a-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4196a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4196a-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4196a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4196a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4196a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4196a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4196a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4196a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4196a-112">See also</span></span>

- [<span data-ttu-id="4196a-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4196a-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
