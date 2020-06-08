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
ms.openlocfilehash: c2c9ed848984d36ddf10d32d120deda76a4d47cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500280"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="194ea-102">Método ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="194ea-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="194ea-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="194ea-103">Not implemented.</span></span> <span data-ttu-id="194ea-104">Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.</span><span class="sxs-lookup"><span data-stu-id="194ea-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="194ea-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="194ea-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="194ea-106">Requirements</span></span>  
 <span data-ttu-id="194ea-107">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="194ea-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="194ea-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="194ea-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="194ea-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="194ea-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="194ea-110">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="194ea-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194ea-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="194ea-111">See also</span></span>

- [<span data-ttu-id="194ea-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="194ea-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
