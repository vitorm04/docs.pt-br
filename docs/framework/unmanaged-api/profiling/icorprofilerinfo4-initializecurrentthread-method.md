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
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868428"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="23c7c-102">Método ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="23c7c-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="23c7c-103">Inicializa o thread atual antes das chamadas de API do criador de perfil subsequentes no mesmo thread, para que o deadlock possa ser evitado.</span><span class="sxs-lookup"><span data-stu-id="23c7c-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23c7c-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="23c7c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="23c7c-105">Remarks</span></span>  
 <span data-ttu-id="23c7c-106">É recomendável chamar `InitializeCurrentThread` em qualquer thread que chamará uma API do profiler enquanto houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="23c7c-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="23c7c-107">Esse método é normalmente usado por infilers de amostragem que criam seu próprio thread para chamar o método [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) para executar movimentações de pilha enquanto o thread-alvo é suspenso.</span><span class="sxs-lookup"><span data-stu-id="23c7c-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="23c7c-108">Ao chamar `InitializeCurrentThread` uma vez em que o criador de perfil cria pela primeira vez o thread de amostragem, os profileres podem garantir que a inicialização lenta por thread que o CLR executaria, de outra forma, durante a primeira chamada para `DoStackSnapshot` possa ocorrer com segurança quando nenhum outro thread for suspenso.</span><span class="sxs-lookup"><span data-stu-id="23c7c-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23c7c-109">`InitializeCurrentThread` faz a inicialização com antecedência para concluir as tarefas que usam bloqueios e pode travar.</span><span class="sxs-lookup"><span data-stu-id="23c7c-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="23c7c-110">Chame `InitializeCurrentThread` somente quando não houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="23c7c-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c7c-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="23c7c-111">Requirements</span></span>  
 <span data-ttu-id="23c7c-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23c7c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c7c-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="23c7c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23c7c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23c7c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23c7c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c7c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c7c-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="23c7c-116">See also</span></span>

- [<span data-ttu-id="23c7c-117">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="23c7c-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="23c7c-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="23c7c-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="23c7c-119">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="23c7c-119">Profiling</span></span>](index.md)
