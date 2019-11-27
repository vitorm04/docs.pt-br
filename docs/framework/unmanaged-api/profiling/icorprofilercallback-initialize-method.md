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
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434555"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="83a91-102">Método ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="83a91-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="83a91-103">Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo Common Language Runtime (CLR) é iniciado.</span><span class="sxs-lookup"><span data-stu-id="83a91-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83a91-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83a91-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="83a91-106">[na](/cpp/atl/iunknown) interface, o criador de perfil deve consultar um ponteiro de interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="83a91-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83a91-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="83a91-107">Remarks</span></span>  
 <span data-ttu-id="83a91-108">A chamada `Initialize` é a única oportunidade para habilitar (ou desabilitar) retornos de chamada que são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="83a91-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="83a91-109">Depois que um retorno de chamada é habilitado pelo `Initialize` chamar, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="83a91-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="83a91-110">O valor COR_PRF_MONITOR_IMMUTABLE da enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) indica quais eventos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="83a91-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a91-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="83a91-111">Requirements</span></span>  
 <span data-ttu-id="83a91-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a91-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a91-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="83a91-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83a91-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83a91-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83a91-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a91-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a91-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83a91-116">See also</span></span>

- [<span data-ttu-id="83a91-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="83a91-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="83a91-118">Método Shutdown</span><span class="sxs-lookup"><span data-stu-id="83a91-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
