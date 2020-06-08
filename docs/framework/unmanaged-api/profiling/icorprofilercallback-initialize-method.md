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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500098"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="0c170-102">Método ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="0c170-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="0c170-103">Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo Common Language Runtime (CLR) é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0c170-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c170-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c170-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c170-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c170-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="0c170-106">\[in] ponteiro para uma interface [IUnknown](/cpp/atl/iunknown) que o criador de perfil deve consultar para um ponteiro de interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0c170-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="0c170-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c170-107">Remarks</span></span>  
 <span data-ttu-id="0c170-108">A `Initialize` chamada é a única oportunidade para habilitar (ou desabilitar) retornos de chamada que são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="0c170-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="0c170-109">Depois que um retorno de chamada é habilitado pelo `Initialize` Call, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c170-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="0c170-110">O valor COR_PRF_MONITOR_IMMUTABLE da enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indica quais eventos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="0c170-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c170-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c170-111">Requirements</span></span>  
 <span data-ttu-id="0c170-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c170-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c170-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0c170-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c170-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c170-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c170-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c170-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c170-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c170-116">See also</span></span>

- [<span data-ttu-id="0c170-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0c170-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0c170-118">Método Shutdown</span><span class="sxs-lookup"><span data-stu-id="0c170-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
