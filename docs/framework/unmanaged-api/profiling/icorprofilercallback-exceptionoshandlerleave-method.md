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
ms.openlocfilehash: 468c5b28bb5a574aacf623196f0c516992473707
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756231"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="0a16f-102">Método ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="0a16f-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="0a16f-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="0a16f-103">Not implemented.</span></span> <span data-ttu-id="0a16f-104">Um criador de perfil que precisa de informações de exceção não gerenciado deve obter essas informações por outros meios.</span><span class="sxs-lookup"><span data-stu-id="0a16f-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a16f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a16f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0a16f-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a16f-106">Requirements</span></span>  
 <span data-ttu-id="0a16f-107">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a16f-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a16f-108">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a16f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a16f-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a16f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a16f-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a16f-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a16f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a16f-111">See also</span></span>

- [<span data-ttu-id="0a16f-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0a16f-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
