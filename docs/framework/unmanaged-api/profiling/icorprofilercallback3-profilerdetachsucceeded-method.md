---
title: Método ICorProfilerCallback3::ProfilerDetachSucceeded
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efe3070b41b1d71e0cf533a7f9f211f4c6626726
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197848"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="c1ce7-102">Método ICorProfilerCallback3::ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="c1ce7-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="c1ce7-103">Notifica o criador de perfil que o common language runtime (CLR) está prestes a descarregar a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ce7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1ce7-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c1ce7-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c1ce7-105">Return Value</span></span>  
 <span data-ttu-id="c1ce7-106">O valor de retorno desse retorno de chamada é ignorado.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1ce7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1ce7-107">Remarks</span></span>  
 <span data-ttu-id="c1ce7-108">O `ProfilerDetachSucceeded` retorno de chamada é emitido depois que todos os threads tenham saído código do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="c1ce7-109">Quando este método é chamado, o criador de perfil deve executar qualquer tarefa de última hora que não é apropriada para seu destruidor, como notificar sua interface do usuário ou o componente de log.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="c1ce7-110">No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidos pelo CLR durante esse retorno de chamada (como o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*` interfaces).</span><span class="sxs-lookup"><span data-stu-id="c1ce7-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="c1ce7-111">O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação de desanexação for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="c1ce7-112">Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto criador de perfil e descarrega a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="c1ce7-113">Portanto, o criador de perfil não deve executar as ações que poderiam causar a execução ocorra dentro a DLL do criador de perfil depois que ele retorna desse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="c1ce7-114">Por exemplo, ele não deve criar threads ou registrar retornos de chamada do temporizador.</span><span class="sxs-lookup"><span data-stu-id="c1ce7-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ce7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1ce7-115">Requirements</span></span>  
 <span data-ttu-id="c1ce7-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ce7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ce7-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1ce7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1ce7-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1ce7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1ce7-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ce7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ce7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1ce7-120">See also</span></span>

- [<span data-ttu-id="c1ce7-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="c1ce7-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="c1ce7-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c1ce7-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c1ce7-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c1ce7-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c1ce7-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c1ce7-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
