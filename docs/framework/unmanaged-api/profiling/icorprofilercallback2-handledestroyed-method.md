---
title: Método ICorProfilerCallback2::HandleDestroyed
ms.date: 03/30/2017
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
ms.openlocfilehash: d7a4f7d08e6d8698dbb58c4c2d111a47d0ccc8db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499773"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="ef621-102">Método ICorProfilerCallback2::HandleDestroyed</span><span class="sxs-lookup"><span data-stu-id="ef621-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="ef621-103">Notifica o criador de perfil de código de que um identificador de coleta de lixo foi destruído.</span><span class="sxs-lookup"><span data-stu-id="ef621-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef621-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef621-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef621-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef621-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="ef621-106">no A ID do identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ef621-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef621-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef621-107">Requirements</span></span>  
 <span data-ttu-id="ef621-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef621-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef621-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ef621-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef621-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef621-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef621-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef621-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef621-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="ef621-112">See also</span></span>

- [<span data-ttu-id="ef621-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ef621-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ef621-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="ef621-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
