---
title: Método ICorProfilerCallback::Initialize
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5aa1025d3f24126c6f8b8585e39dda0201fad3d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623307"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="67fb1-102">Método ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="67fb1-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="67fb1-103">Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo de runtime (CLR) de linguagem comum é iniciado.</span><span class="sxs-lookup"><span data-stu-id="67fb1-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67fb1-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67fb1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67fb1-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="67fb1-106">[na](/cpp/atl/iunknown) interface que o criador de perfis deve consultar um [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="67fb1-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67fb1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="67fb1-107">Remarks</span></span>  
 <span data-ttu-id="67fb1-108">O `Initialize` chamada é a única oportunidade para ativar (ou desativar) os retornos de chamada são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="67fb1-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="67fb1-109">Depois que um retorno de chamada é habilitado pela `Initialize` chamar, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="67fb1-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="67fb1-110">O valor COR_PRF_MONITOR_IMMUTABLE a [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração indica quais eventos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="67fb1-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67fb1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67fb1-111">Requirements</span></span>  
 <span data-ttu-id="67fb1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67fb1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67fb1-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67fb1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67fb1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67fb1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67fb1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67fb1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fb1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67fb1-116">See also</span></span>
- [<span data-ttu-id="67fb1-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="67fb1-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="67fb1-118">Método Shutdown</span><span class="sxs-lookup"><span data-stu-id="67fb1-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
