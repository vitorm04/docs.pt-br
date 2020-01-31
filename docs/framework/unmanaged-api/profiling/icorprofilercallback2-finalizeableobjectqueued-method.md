---
title: Método ICorProfilerCallback2::FinalizeableObjectQueued
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: b9093f920a8c14247bc51471da3682c7e500afa4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865797"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="0600a-102">Método ICorProfilerCallback2::FinalizeableObjectQueued</span><span class="sxs-lookup"><span data-stu-id="0600a-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="0600a-103">Notifica o criador de perfil de código de que um objeto com um finalizador foi enfileirado para o thread do finalizador para execução de seu método de `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="0600a-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0600a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0600a-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0600a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0600a-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="0600a-106">no Um valor da enumeração [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) que descreve os aspectos do finalizador.</span><span class="sxs-lookup"><span data-stu-id="0600a-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="0600a-107">no A ID do objeto que foi enfileirado.</span><span class="sxs-lookup"><span data-stu-id="0600a-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0600a-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0600a-108">Requirements</span></span>  
 <span data-ttu-id="0600a-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0600a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0600a-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0600a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0600a-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0600a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0600a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0600a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0600a-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="0600a-113">See also</span></span>

- [<span data-ttu-id="0600a-114">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0600a-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0600a-115">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="0600a-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
