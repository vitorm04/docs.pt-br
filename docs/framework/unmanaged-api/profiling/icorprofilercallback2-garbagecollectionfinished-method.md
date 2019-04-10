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
ms.openlocfilehash: f613842c12b50b8a58aac1b71bf2f3c53aaf961f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231091"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="5d057-102">Método ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="5d057-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="5d057-103">Notifica o criador de perfil que a coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo tiveram sido emitidos para ele.</span><span class="sxs-lookup"><span data-stu-id="5d057-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d057-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d057-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5d057-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d057-105">Remarks</span></span>  
 <span data-ttu-id="5d057-106">É seguro para o criador de perfil inspecionar objetos em seus locais definitivos quando o `GarbageCollectionFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="5d057-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d057-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d057-107">Requirements</span></span>  
 <span data-ttu-id="5d057-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d057-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d057-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d057-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d057-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d057-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5d057-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d057-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d057-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d057-112">See also</span></span>

- [<span data-ttu-id="5d057-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5d057-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5d057-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="5d057-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
