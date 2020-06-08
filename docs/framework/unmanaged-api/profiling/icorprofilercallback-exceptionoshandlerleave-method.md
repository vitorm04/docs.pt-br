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
ms.openlocfilehash: 5ba45cf526a6ebca6975a75d06308d089770ad5b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500254"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="8bf4a-102">Método ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="8bf4a-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="8bf4a-103">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="8bf4a-103">Not implemented.</span></span> <span data-ttu-id="8bf4a-104">Um criador de perfil que precisa de informações de exceção não gerenciadas deve obter essas informações por meio de outros meios.</span><span class="sxs-lookup"><span data-stu-id="8bf4a-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf4a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bf4a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8bf4a-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bf4a-106">Requirements</span></span>  
 <span data-ttu-id="8bf4a-107">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf4a-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf4a-108">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8bf4a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bf4a-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf4a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf4a-110">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf4a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf4a-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bf4a-111">See also</span></span>

- [<span data-ttu-id="8bf4a-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8bf4a-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
