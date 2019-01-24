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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebdd76655124922008667898e38f873ad93598e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555590"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="4ea04-102">Método ICorProfilerCallback3::InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="4ea04-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="4ea04-103">Chamado pelo common language runtime (CLR) para dar uma oportunidade de inicializar seu estado após uma operação de anexação de criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4ea04-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ea04-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ea04-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ea04-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="4ea04-106">[in] Um ponteiro de interface para o `ICorProfilerInfo*` interface.</span><span class="sxs-lookup"><span data-stu-id="4ea04-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="4ea04-107">[in] Um ponteiro para os dados passados para o [iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método no seu `pvClientData` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4ea04-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="4ea04-108">Se esse parâmetro for nulo, `cbClientData` será 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="4ea04-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="4ea04-109">O CLR libera essa memória quando ele retorna da `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="4ea04-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="4ea04-110">[in] O tamanho, em bytes, dos dados que `pvClientData` aponta.</span><span class="sxs-lookup"><span data-stu-id="4ea04-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ea04-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ea04-111">Remarks</span></span>  
 <span data-ttu-id="4ea04-112">O CLR chama `InitializeForAttach` para dar o criador de perfil uma oportunidade para retornos de chamada de solicitação.</span><span class="sxs-lookup"><span data-stu-id="4ea04-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea04-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ea04-113">Requirements</span></span>  
 <span data-ttu-id="4ea04-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ea04-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ea04-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ea04-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ea04-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ea04-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ea04-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea04-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ea04-118">See also</span></span>
- [<span data-ttu-id="4ea04-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4ea04-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4ea04-120">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="4ea04-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4ea04-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4ea04-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4ea04-122">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4ea04-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
