---
title: Método ICorProfilerCallback2::GarbageCollectionFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 040c51723a2505a1320d2ecde38c9ed1cd19d254
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734916"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="87765-102">Método ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="87765-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="87765-103">Notifica o criador de perfil que a coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo tiveram sido emitidos para ele.</span><span class="sxs-lookup"><span data-stu-id="87765-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87765-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87765-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="87765-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="87765-105">Remarks</span></span>  
 <span data-ttu-id="87765-106">É seguro para o criador de perfil inspecionar objetos em seus locais definitivos quando o `GarbageCollectionFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="87765-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87765-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87765-107">Requirements</span></span>  
 <span data-ttu-id="87765-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87765-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87765-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87765-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87765-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87765-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87765-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87765-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87765-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87765-112">See also</span></span>
- [<span data-ttu-id="87765-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="87765-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="87765-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="87765-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
