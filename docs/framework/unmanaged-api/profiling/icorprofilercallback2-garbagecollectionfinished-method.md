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
ms.openlocfilehash: 21f7e9fa0e567063c49caa390ace09c43454b092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451676"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="a1f76-102">Método ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="a1f76-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="a1f76-103">Notifica o criador de perfil que a coleta de lixo foi concluída e todos os retornos de chamada de coleta de lixo foram emitidos por ela.</span><span class="sxs-lookup"><span data-stu-id="a1f76-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1f76-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1f76-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1f76-105">Remarks</span></span>  
 <span data-ttu-id="a1f76-106">É seguro para o criador de perfil inspecionar objetos em seus locais finais quando o `GarbageCollectionFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="a1f76-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f76-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1f76-107">Requirements</span></span>  
 <span data-ttu-id="a1f76-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f76-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f76-109">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1f76-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1f76-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1f76-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1f76-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f76-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f76-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1f76-112">See Also</span></span>  
 [<span data-ttu-id="a1f76-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a1f76-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a1f76-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="a1f76-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
