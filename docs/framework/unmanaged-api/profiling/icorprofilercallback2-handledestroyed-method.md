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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc6b086b444a769afbf01369b50c69e242a21050
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041555"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="5171d-102">Método ICorProfilerCallback2::HandleDestroyed</span><span class="sxs-lookup"><span data-stu-id="5171d-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="5171d-103">Notifica o criador de perfil de código que um identificador da coleta de lixo foi destruído.</span><span class="sxs-lookup"><span data-stu-id="5171d-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5171d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5171d-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5171d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5171d-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="5171d-106">[in] A ID do identificador para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5171d-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5171d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5171d-107">Requirements</span></span>  
 <span data-ttu-id="5171d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5171d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5171d-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5171d-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5171d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5171d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5171d-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5171d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5171d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5171d-112">See also</span></span>

- [<span data-ttu-id="5171d-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5171d-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5171d-114">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="5171d-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
