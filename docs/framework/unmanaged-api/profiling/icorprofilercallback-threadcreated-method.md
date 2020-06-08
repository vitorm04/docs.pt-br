---
title: Método ICorProfilerCallback::ThreadCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 25a4b101388bfc0151ba7c9c52da6561d48f806b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503153"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="e1c22-102">Método ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="e1c22-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="e1c22-103">Notifica o criador de perfil de que um thread foi criado.</span><span class="sxs-lookup"><span data-stu-id="e1c22-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1c22-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c22-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1c22-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e1c22-106">no A ID do thread que foi criado.</span><span class="sxs-lookup"><span data-stu-id="e1c22-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1c22-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1c22-107">Remarks</span></span>  
 <span data-ttu-id="e1c22-108">O `threadId` valor é válido imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e1c22-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c22-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1c22-109">Requirements</span></span>  
 <span data-ttu-id="e1c22-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c22-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c22-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1c22-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1c22-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1c22-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1c22-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c22-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1c22-114">See also</span></span>

- [<span data-ttu-id="e1c22-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e1c22-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e1c22-116">Método ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="e1c22-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
