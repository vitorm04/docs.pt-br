---
title: "Método ICorProfilerCallback::Initialize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2eebe596b3459d51afe66df4bb81f74e93f3526e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="8ea92-102">Método ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="8ea92-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="8ea92-103">Chamado para inicializar o criador de perfil de código sempre que um aplicativo common language runtime (CLR) novo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="8ea92-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ea92-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ea92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ea92-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="8ea92-106">[em](/cpp/atl/iunknown) interface deve consultar o criador de perfil para um [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="8ea92-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ea92-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ea92-107">Remarks</span></span>  
 <span data-ttu-id="8ea92-108">O `Initialize` chamada é a única oportunidade para ativar (ou desativar) retornos de chamada são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="8ea92-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="8ea92-109">Depois que um retorno de chamada é habilitado pelo `Initialize` chamar, não pode ser desabilitado posteriormente usando [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ea92-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="8ea92-110">O valor COR_PRF_MONITOR_IMMUTABLE o [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração indica quais eventos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="8ea92-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea92-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ea92-111">Requirements</span></span>  
 <span data-ttu-id="8ea92-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ea92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ea92-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ea92-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ea92-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ea92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ea92-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ea92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea92-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ea92-116">See Also</span></span>  
 [<span data-ttu-id="8ea92-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8ea92-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8ea92-118">Método Shutdown</span><span class="sxs-lookup"><span data-stu-id="8ea92-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
