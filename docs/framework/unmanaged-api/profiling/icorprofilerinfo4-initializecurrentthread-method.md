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
ms.openlocfilehash: 9fd0900e61c57d105439d83430284dc8634d2a1e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223596"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="20a6f-102">Método ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="20a6f-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="20a6f-103">Inicializa o thread atual com antecedência sobre o criador de perfil subsequente, chamadas de API no mesmo thread, portanto, esse deadlock pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="20a6f-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20a6f-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="20a6f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="20a6f-105">Remarks</span></span>  
 <span data-ttu-id="20a6f-106">É recomendável que você chame `InitializeCurrentThread` em qualquer thread que chama um criador de perfil de API, embora haja suspenso threads.</span><span class="sxs-lookup"><span data-stu-id="20a6f-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="20a6f-107">Esse método é normalmente usado por criadores de perfil de amostragem que criar seu próprio thread para chamar o [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método para executar a pilha orienta enquanto o thread-alvo é suspenso.</span><span class="sxs-lookup"><span data-stu-id="20a6f-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="20a6f-108">Chamando `InitializeCurrentThread` depois de quando o criador de perfil primeiro cria o thread de amostragem, os criadores de perfis podem garantir que a inicialização lenta por thread que o CLR executaria durante a primeira chamada para `DoStackSnapshot` agora pode ocorrer com segurança quando nenhum outro thread está suspenso.</span><span class="sxs-lookup"><span data-stu-id="20a6f-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  `InitializeCurrentThread` <span data-ttu-id="20a6f-109">faz a inicialização de antemão para concluir as tarefas que aplicarão bloqueios e poderá ser bloqueada.</span><span class="sxs-lookup"><span data-stu-id="20a6f-109">does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="20a6f-110">Chamar `InitializeCurrentThread` somente quando não há nenhum thread suspenso.</span><span class="sxs-lookup"><span data-stu-id="20a6f-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a6f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20a6f-111">Requirements</span></span>  
 <span data-ttu-id="20a6f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a6f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a6f-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20a6f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20a6f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20a6f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="20a6f-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="20a6f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="20a6f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20a6f-116">See also</span></span>

- [<span data-ttu-id="20a6f-117">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="20a6f-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="20a6f-118">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="20a6f-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="20a6f-119">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="20a6f-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
