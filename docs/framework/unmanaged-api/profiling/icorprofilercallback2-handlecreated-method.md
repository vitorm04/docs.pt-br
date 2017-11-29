---
title: "Método ICorProfilerCallback2::HandleCreated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.HandleCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d866261f16e344f6842ba59e83424219ec3d8dfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="17ed6-102">Método ICorProfilerCallback2::HandleCreated</span><span class="sxs-lookup"><span data-stu-id="17ed6-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="17ed6-103">Notifica o criador de perfil de código que foi criado um identificador de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="17ed6-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ed6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17ed6-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17ed6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17ed6-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="17ed6-106">[in] A ID do identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="17ed6-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="17ed6-107">[in] A ID do objeto para o qual o identificador de coleta de lixo foi criado.</span><span class="sxs-lookup"><span data-stu-id="17ed6-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ed6-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17ed6-108">Requirements</span></span>  
 <span data-ttu-id="17ed6-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17ed6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ed6-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17ed6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17ed6-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17ed6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17ed6-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ed6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ed6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17ed6-113">See Also</span></span>  
 [<span data-ttu-id="17ed6-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="17ed6-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="17ed6-115">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="17ed6-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
