---
title: Método ICorProfilerCallback3::InitializeForAttach
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439520"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="d8cc1-102">Método ICorProfilerCallback3::InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="d8cc1-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="d8cc1-103">Chamado pelo Common Language Runtime (CLR) para dar ao criador de perfil uma oportunidade de inicializar seu estado após uma operação de anexação.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cc1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8cc1-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8cc1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8cc1-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="d8cc1-106">no Um ponteiro de interface para a interface `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="d8cc1-107">no Um ponteiro para os dados passados para o método [ICLRProfiling:: AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) em seu parâmetro `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="d8cc1-108">Se esse parâmetro for nulo, `cbClientData` será 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d8cc1-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="d8cc1-109">O CLR libera essa memória quando ela retorna da `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="d8cc1-110">no O tamanho, em bytes, dos dados aos quais `pvClientData` aponta.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8cc1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8cc1-111">Remarks</span></span>  
 <span data-ttu-id="d8cc1-112">O CLR chama `InitializeForAttach` para dar ao criador de perfil uma oportunidade de solicitar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="d8cc1-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8cc1-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d8cc1-113">Requirements</span></span>  
 <span data-ttu-id="d8cc1-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8cc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8cc1-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8cc1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8cc1-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8cc1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8cc1-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8cc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8cc1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8cc1-118">See also</span></span>

- [<span data-ttu-id="d8cc1-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d8cc1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d8cc1-120">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="d8cc1-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d8cc1-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d8cc1-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d8cc1-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d8cc1-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
