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
ms.openlocfilehash: 52803fc04aa55f40a131e2d53dc4ef7dba70bcde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727112"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="f2ae9-102">Método ICorProfilerCallback3::ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="f2ae9-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="f2ae9-103">Notifica o criador de perfil que o common language runtime (CLR) está prestes a descarregar a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ae9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2ae9-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f2ae9-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f2ae9-105">Return Value</span></span>  
 <span data-ttu-id="f2ae9-106">O valor de retorno desse retorno de chamada é ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2ae9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2ae9-107">Remarks</span></span>  
 <span data-ttu-id="f2ae9-108">O `ProfilerDetachSucceeded` retorno de chamada é emitido depois que todos os threads tenham saído código do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="f2ae9-109">Quando este método é chamado, o criador de perfil deve executar qualquer tarefa de última hora que não é apropriada para seu destruidor, como notificar sua interface do usuário ou o componente de log.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="f2ae9-110">No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidos pelo CLR durante esse retorno de chamada (como o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*` interfaces).</span><span class="sxs-lookup"><span data-stu-id="f2ae9-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="f2ae9-111">O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação de desanexação for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="f2ae9-112">Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto criador de perfil e descarrega a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="f2ae9-113">Portanto, o criador de perfil não deve executar as ações que poderiam causar a execução ocorra dentro a DLL do criador de perfil depois que ele retorna desse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="f2ae9-114">Por exemplo, ele não deve criar threads ou registrar retornos de chamada do temporizador.</span><span class="sxs-lookup"><span data-stu-id="f2ae9-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ae9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2ae9-115">Requirements</span></span>  
 <span data-ttu-id="f2ae9-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ae9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ae9-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2ae9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2ae9-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2ae9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2ae9-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ae9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ae9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2ae9-120">See also</span></span>
- [<span data-ttu-id="f2ae9-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="f2ae9-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f2ae9-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="f2ae9-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f2ae9-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f2ae9-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f2ae9-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f2ae9-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
