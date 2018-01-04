---
title: "Método ICorProfilerInfo4::InitializeCurrentThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="f8ac0-102">Método ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="f8ac0-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="f8ac0-103">Inicializa o thread atual antes de criador de perfil subsequente chamadas à API no mesmo thread, portanto esse deadlock pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8ac0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8ac0-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8ac0-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8ac0-105">Remarks</span></span>  
 <span data-ttu-id="f8ac0-106">É recomendável que você chamar `InitializeCurrentThread` em qualquer thread que chamará um criador de perfil API enquanto houver suspenso threads.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="f8ac0-107">Esse método é normalmente usado por criadores de perfil de amostragem que criar seu próprio thread para chamar o [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método executar pilha orienta enquanto o thread de destino está suspenso.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="f8ac0-108">Chamando `InitializeCurrentThread` depois quando o criador de perfil primeiro cria o thread de amostragem, criadores de perfil podem garantir que a inicialização lenta por thread que o CLR executaria caso contrário, durante a primeira chamada para `DoStackSnapshot` agora pode ocorrer com segurança quando nenhum outro thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8ac0-109">`InitializeCurrentThread`faz a inicialização com antecedência para concluir tarefas que usam bloqueios e podem fazer um deadlock.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="f8ac0-110">Chamar `InitializeCurrentThread` somente quando não há nenhum thread suspenso.</span><span class="sxs-lookup"><span data-stu-id="f8ac0-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8ac0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8ac0-111">Requirements</span></span>  
 <span data-ttu-id="f8ac0-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8ac0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8ac0-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8ac0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8ac0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8ac0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8ac0-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ac0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ac0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8ac0-116">See Also</span></span>  
 [<span data-ttu-id="f8ac0-117">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="f8ac0-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="f8ac0-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f8ac0-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f8ac0-119">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f8ac0-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
