---
title: "Método ICorProfilerCallback::ExceptionSearchFunctionEnter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d410d6ef47dfb0ad33c2a6a03f80d05810182a3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="a80b9-102">Método ICorProfilerCallback::ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="a80b9-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="a80b9-103">Notifica o criador de perfil que a fase de pesquisa de tratamento de exceção começou a pesquisa de uma função para localizar um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="a80b9-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a80b9-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a80b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a80b9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a80b9-106">[in] A ID da função que foi digitada.</span><span class="sxs-lookup"><span data-stu-id="a80b9-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a80b9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a80b9-107">Requirements</span></span>  
 <span data-ttu-id="a80b9-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a80b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80b9-109">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a80b9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a80b9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a80b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a80b9-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80b9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a80b9-112">See Also</span></span>  
 [<span data-ttu-id="a80b9-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a80b9-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a80b9-114">Método ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="a80b9-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
