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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074294"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="b8c5c-102">Método ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="b8c5c-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="b8c5c-103">Notifica o criador de perfil que a fase de pesquisa de manipulação de exceção foi localizado um manipulador para a exceção que foi gerada.</span><span class="sxs-lookup"><span data-stu-id="b8c5c-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8c5c-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8c5c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8c5c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b8c5c-106">[in] A ID da função que contém o manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="b8c5c-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c5c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8c5c-107">Requirements</span></span>  
 <span data-ttu-id="b8c5c-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c5c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c5c-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8c5c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8c5c-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8c5c-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b8c5c-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b8c5c-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8c5c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8c5c-112">See also</span></span>

- [<span data-ttu-id="b8c5c-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b8c5c-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
