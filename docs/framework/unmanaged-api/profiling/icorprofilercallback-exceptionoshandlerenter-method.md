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
ms.openlocfilehash: b3088308e75fb7cbffcc439ab4440255ed0fb2b9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444917"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="a5371-102">Método ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="a5371-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="a5371-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="a5371-103">Not implemented.</span></span> <span data-ttu-id="a5371-104">Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.</span><span class="sxs-lookup"><span data-stu-id="a5371-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5371-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5371-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a5371-106">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a5371-106">Requirements</span></span>  
 <span data-ttu-id="a5371-107">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5371-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5371-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a5371-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5371-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5371-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5371-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5371-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5371-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5371-111">See also</span></span>

- [<span data-ttu-id="a5371-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a5371-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
