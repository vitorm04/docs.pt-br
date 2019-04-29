---
title: Método ICorProfilerCallback::ExceptionOSHandlerLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0decfde08a9097c8fe5185c8b5a3fef4f7f68189
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598721"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="85a69-102">Método ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="85a69-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="85a69-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="85a69-103">Not implemented.</span></span> <span data-ttu-id="85a69-104">Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.</span><span class="sxs-lookup"><span data-stu-id="85a69-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a69-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85a69-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="85a69-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85a69-106">Requirements</span></span>  
 <span data-ttu-id="85a69-107">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85a69-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85a69-108">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85a69-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85a69-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85a69-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85a69-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85a69-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a69-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85a69-111">See also</span></span>

- [<span data-ttu-id="85a69-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="85a69-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
