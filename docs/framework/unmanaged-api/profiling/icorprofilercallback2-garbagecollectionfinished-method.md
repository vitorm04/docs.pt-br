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
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499814"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="64872-102">Método ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="64872-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="64872-103">Notifica o criador de perfil de que a coleta de lixo foi concluída e que todos os retornos de chamada de coleta de lixo foram emitidos para ela.</span><span class="sxs-lookup"><span data-stu-id="64872-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64872-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64872-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="64872-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="64872-105">Remarks</span></span>  
 <span data-ttu-id="64872-106">É seguro que o criador de perfil Inspecione objetos em seus locais finais quando o `GarbageCollectionFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="64872-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64872-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64872-107">Requirements</span></span>  
 <span data-ttu-id="64872-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64872-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64872-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="64872-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64872-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64872-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64872-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64872-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64872-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="64872-112">See also</span></span>

- [<span data-ttu-id="64872-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="64872-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="64872-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="64872-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
