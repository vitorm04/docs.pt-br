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
ms.openlocfilehash: dcb2af2507306b22da14c13a42e4019261c8fa8c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866436"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="1be7f-102">Método ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="1be7f-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="1be7f-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="1be7f-103">Not implemented.</span></span> <span data-ttu-id="1be7f-104">Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.</span><span class="sxs-lookup"><span data-stu-id="1be7f-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be7f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1be7f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1be7f-106">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1be7f-106">Requirements</span></span>  
 <span data-ttu-id="1be7f-107">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be7f-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be7f-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1be7f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1be7f-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1be7f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1be7f-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be7f-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be7f-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="1be7f-111">See also</span></span>

- [<span data-ttu-id="1be7f-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1be7f-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
