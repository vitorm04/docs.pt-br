---
title: "Método ICorProfilerCallback::ExceptionOSHandlerEnter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c26260a2f70537deefb5600c0b721e0c0faf0399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="4c6a2-102">Método ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="4c6a2-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="4c6a2-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="4c6a2-103">Not implemented.</span></span> <span data-ttu-id="4c6a2-104">Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.</span><span class="sxs-lookup"><span data-stu-id="4c6a2-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c6a2-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4c6a2-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c6a2-106">Requirements</span></span>  
 <span data-ttu-id="4c6a2-107">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c6a2-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c6a2-108">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c6a2-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c6a2-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c6a2-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c6a2-110">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c6a2-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c6a2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c6a2-111">See Also</span></span>  
 [<span data-ttu-id="4c6a2-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4c6a2-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
