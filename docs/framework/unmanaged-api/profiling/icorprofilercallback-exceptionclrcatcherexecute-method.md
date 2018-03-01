---
title: "Método ICorProfilerCallback::ExceptionCLRCatcherExecute"
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
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5d278fa196836d18b8515bee5af1946b2ca4d74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="f2461-102">Método ICorProfilerCallback::ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="f2461-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="f2461-103">Chamado quando um `catch` bloco de exceção é executada dentro do common language runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="f2461-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f2461-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="f2461-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2461-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2461-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f2461-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2461-106">Requirements</span></span>  
 <span data-ttu-id="f2461-107">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2461-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2461-108">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2461-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2461-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2461-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2461-110">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="f2461-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2461-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2461-111">See Also</span></span>  
 [<span data-ttu-id="f2461-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f2461-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f2461-113">Método ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="f2461-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
