---
title: Método ICorProfilerCallback::ExceptionOSHandlerEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dc7c22ee075f347604864d8bee1a4e871da616
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451760"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="0110c-102">Método ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="0110c-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="0110c-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="0110c-103">Not implemented.</span></span> <span data-ttu-id="0110c-104">Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.</span><span class="sxs-lookup"><span data-stu-id="0110c-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0110c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0110c-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0110c-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0110c-106">Requirements</span></span>  
 <span data-ttu-id="0110c-107">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0110c-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0110c-108">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0110c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0110c-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0110c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0110c-110">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0110c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0110c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0110c-111">See Also</span></span>  
 [<span data-ttu-id="0110c-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0110c-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
