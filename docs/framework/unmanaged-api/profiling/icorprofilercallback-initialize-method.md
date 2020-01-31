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
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866284"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="eb765-102">Método ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="eb765-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="eb765-103">Chamado para inicializar o criador de perfil de código sempre que um novo aplicativo Common Language Runtime (CLR) é iniciado.</span><span class="sxs-lookup"><span data-stu-id="eb765-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb765-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb765-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb765-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb765-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="eb765-106">\[no] ponteiro para uma interface [IUnknown](/cpp/atl/iunknown) que o criador de perfil deve consultar para um ponteiro de interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eb765-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="eb765-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb765-107">Remarks</span></span>  
 <span data-ttu-id="eb765-108">A chamada `Initialize` é a única oportunidade para habilitar (ou desabilitar) retornos de chamada que são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="eb765-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="eb765-109">Depois que um retorno de chamada é habilitado pelo `Initialize` chamar, ele não pode ser desabilitado posteriormente usando [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb765-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="eb765-110">O valor COR_PRF_MONITOR_IMMUTABLE da enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indica quais eventos são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="eb765-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb765-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="eb765-111">Requirements</span></span>  
 <span data-ttu-id="eb765-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb765-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb765-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb765-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb765-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb765-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb765-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb765-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb765-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="eb765-116">See also</span></span>

- [<span data-ttu-id="eb765-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="eb765-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eb765-118">Método Shutdown</span><span class="sxs-lookup"><span data-stu-id="eb765-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
