---
title: Método ICorProfilerCallback::ExceptionCLRCatcherExecute
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b640a6dee9ae50278d6a844d20d21eae156e9dd7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200955"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="bf18c-102">Método ICorProfilerCallback::ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="bf18c-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="bf18c-103">Chamado quando um `catch` bloqueie uma exceção for executada dentro do common language runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="bf18c-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="bf18c-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="bf18c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf18c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf18c-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="bf18c-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf18c-106">Requirements</span></span>  
 <span data-ttu-id="bf18c-107">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf18c-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf18c-108">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf18c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf18c-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf18c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf18c-110">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="bf18c-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf18c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf18c-111">See also</span></span>

- [<span data-ttu-id="bf18c-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bf18c-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bf18c-113">Método ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="bf18c-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
