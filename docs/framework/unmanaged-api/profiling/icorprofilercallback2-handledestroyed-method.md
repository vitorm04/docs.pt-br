---
title: "Método ICorProfilerCallback2::HandleDestroyed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a05c4559faf8e91dac3cc5a11c3331ee9d6c8e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="3d67f-102">Método ICorProfilerCallback2::HandleDestroyed</span><span class="sxs-lookup"><span data-stu-id="3d67f-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="3d67f-103">Notifica o criador de perfil de código que um identificador de coleta de lixo foi destruído.</span><span class="sxs-lookup"><span data-stu-id="3d67f-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d67f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d67f-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d67f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d67f-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="3d67f-106">[in] A ID do identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3d67f-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d67f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d67f-107">Requirements</span></span>  
 <span data-ttu-id="3d67f-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d67f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d67f-109">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d67f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d67f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d67f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d67f-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d67f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d67f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d67f-112">See Also</span></span>  
 [<span data-ttu-id="3d67f-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3d67f-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3d67f-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="3d67f-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
