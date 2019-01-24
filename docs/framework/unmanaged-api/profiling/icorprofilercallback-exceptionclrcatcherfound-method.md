---
title: Método ICorProfilerCallback::ExceptionCLRCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edbd48c910c89c9dd5feea33d9598933fd63befa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729767"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="76a8b-102">Método ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="76a8b-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="76a8b-103">Chamado quando um `catch` bloqueie uma exceção foi encontrada no common language runtime (CLR) em si.</span><span class="sxs-lookup"><span data-stu-id="76a8b-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="76a8b-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="76a8b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a8b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76a8b-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="76a8b-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76a8b-106">Requirements</span></span>  
 <span data-ttu-id="76a8b-107">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76a8b-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a8b-108">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76a8b-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76a8b-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76a8b-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76a8b-110">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="76a8b-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a8b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76a8b-111">See also</span></span>
- [<span data-ttu-id="76a8b-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="76a8b-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="76a8b-113">Método ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="76a8b-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
