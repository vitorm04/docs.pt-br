---
title: Interface ICorProfilerCallback3
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865565"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="4c260-102">Interface ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="4c260-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="4c260-103">Fornece métodos de retorno de chamada que o Common Language Runtime (CLR) usa para comunicar a anexação e desanexar informações de estado ao criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4c260-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c260-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4c260-104">Methods</span></span>  
  
|<span data-ttu-id="4c260-105">Método</span><span class="sxs-lookup"><span data-stu-id="4c260-105">Method</span></span>|<span data-ttu-id="4c260-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c260-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c260-107">Método InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="4c260-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="4c260-108">Chamado pelo CLR para dar ao criador de perfil uma oportunidade de inicializar seu estado após uma operação de anexação.</span><span class="sxs-lookup"><span data-stu-id="4c260-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="4c260-109">Método ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="4c260-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="4c260-110">Chamado pelo CLR para indicar que o criador de perfil agora pode chamar os métodos de atualização.</span><span class="sxs-lookup"><span data-stu-id="4c260-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="4c260-111">Método ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="4c260-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="4c260-112">Notifica o criador de perfil de que o Common Language Runtime (CLR) está prestes a descarregar a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4c260-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c260-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c260-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c260-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4c260-114">Requirements</span></span>  
 <span data-ttu-id="4c260-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c260-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c260-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4c260-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c260-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c260-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c260-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c260-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c260-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c260-119">See also</span></span>

- [<span data-ttu-id="4c260-120">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="4c260-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4c260-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4c260-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4c260-122">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="4c260-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="4c260-123">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="4c260-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
