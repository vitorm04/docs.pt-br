---
title: Método ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9bb5a2629e435d76691d48feef6689191b66373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957894"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="5baed-102">Método ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="5baed-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="5baed-103">Inicializa o thread atual antes das chamadas de API do criador de perfil subsequentes no mesmo thread, para que o deadlock possa ser evitado.</span><span class="sxs-lookup"><span data-stu-id="5baed-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5baed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5baed-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5baed-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5baed-105">Remarks</span></span>  
 <span data-ttu-id="5baed-106">Recomendamos que você chame `InitializeCurrentThread` em qualquer thread que chamará uma API do profiler enquanto houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="5baed-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="5baed-107">Esse método é normalmente usado por infilers de amostragem que criam seu próprio thread para chamar o método [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) para executar movimentações de pilha enquanto o thread-alvo é suspenso.</span><span class="sxs-lookup"><span data-stu-id="5baed-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="5baed-108">Chamando `InitializeCurrentThread` uma vez quando o criador de perfil cria primeiro o thread de amostragem, os profileres podem garantir a inicialização lenta por thread que o CLR executaria durante a primeira `DoStackSnapshot` chamada para que agora possa ocorrer com segurança quando nenhum outro thread estiver suspenso.</span><span class="sxs-lookup"><span data-stu-id="5baed-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5baed-109">`InitializeCurrentThread`faz a inicialização com antecedência para concluir as tarefas que usam bloqueios e pode travar.</span><span class="sxs-lookup"><span data-stu-id="5baed-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="5baed-110">Chame `InitializeCurrentThread` somente quando não houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="5baed-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5baed-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5baed-111">Requirements</span></span>  
 <span data-ttu-id="5baed-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5baed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5baed-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5baed-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5baed-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5baed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5baed-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5baed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5baed-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5baed-116">See also</span></span>

- [<span data-ttu-id="5baed-117">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="5baed-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="5baed-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5baed-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5baed-119">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5baed-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
