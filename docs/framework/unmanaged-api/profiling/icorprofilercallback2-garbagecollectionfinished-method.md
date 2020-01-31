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
ms.openlocfilehash: 30f2e675532848c2dbb1f055a0f1489cf3b2baa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865786"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="0a483-102">Método ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="0a483-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="0a483-103">Notifica o criador de perfil de que a coleta de lixo foi concluída e que todos os retornos de chamada de coleta de lixo foram emitidos para ela.</span><span class="sxs-lookup"><span data-stu-id="0a483-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a483-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a483-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0a483-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a483-105">Remarks</span></span>  
 <span data-ttu-id="0a483-106">É seguro que o criador de perfil Inspecione objetos em seus locais finais quando o método de `GarbageCollectionFinished` é chamado.</span><span class="sxs-lookup"><span data-stu-id="0a483-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a483-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0a483-107">Requirements</span></span>  
 <span data-ttu-id="0a483-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a483-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a483-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0a483-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a483-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a483-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a483-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a483-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a483-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="0a483-112">See also</span></span>

- [<span data-ttu-id="0a483-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0a483-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0a483-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="0a483-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
