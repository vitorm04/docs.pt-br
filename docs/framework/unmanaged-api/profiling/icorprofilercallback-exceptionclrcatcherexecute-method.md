---
title: "Método ICorProfilerCallback::ExceptionCLRCatcherExecute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b63f428cd75ed98d30e4b6ecca69dbe3b5b5656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="8aff9-102">Método ICorProfilerCallback::ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="8aff9-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="8aff9-103">Chamado quando um `catch` bloco de exceção é executada dentro do common language runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="8aff9-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="8aff9-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="8aff9-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aff9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8aff9-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8aff9-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8aff9-106">Requirements</span></span>  
 <span data-ttu-id="8aff9-107">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aff9-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aff9-108">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8aff9-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8aff9-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aff9-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aff9-110">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="8aff9-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aff9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aff9-111">See Also</span></span>  
 [<span data-ttu-id="8aff9-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8aff9-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8aff9-113">Método ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="8aff9-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
