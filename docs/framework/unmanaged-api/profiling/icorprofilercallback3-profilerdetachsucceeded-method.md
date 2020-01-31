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
ms.openlocfilehash: b96a8930c24275546b0aac9fa650cf5447ef4ef2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865409"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="09205-102">Método ICorProfilerCallback3::ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="09205-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="09205-103">Notifica o criador de perfil de que o Common Language Runtime (CLR) está prestes a descarregar a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="09205-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09205-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09205-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="09205-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="09205-105">Return Value</span></span>  
 <span data-ttu-id="09205-106">O valor de retorno desse retorno de chamada é ignorado.</span><span class="sxs-lookup"><span data-stu-id="09205-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09205-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="09205-107">Remarks</span></span>  
 <span data-ttu-id="09205-108">O retorno de chamada `ProfilerDetachSucceeded` é emitido depois que todos os threads saíram do código do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="09205-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="09205-109">Quando esse método é chamado, o criador de perfil deve executar todas as tarefas de último minuto que não são apropriadas para seu destruidor, como notificar sua interface do usuário ou componente de log.</span><span class="sxs-lookup"><span data-stu-id="09205-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="09205-110">No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidas pelo CLR durante esse retorno de chamada (como as interfaces [ICorProfilerInfo](icorprofilerinfo-interface.md) ou `IMetaData*`).</span><span class="sxs-lookup"><span data-stu-id="09205-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="09205-111">O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação de desanexação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="09205-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="09205-112">Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto Profiler e descarrega a DLL do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="09205-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="09205-113">Portanto, o criador de perfil não deve executar nenhuma ação que faria com que a execução ocorresse dentro da DLL do criador de perfil depois de retornar desse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="09205-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="09205-114">Por exemplo, ele não deve criar threads ou registrar retornos de chamada do temporizador.</span><span class="sxs-lookup"><span data-stu-id="09205-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09205-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="09205-115">Requirements</span></span>  
 <span data-ttu-id="09205-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09205-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09205-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="09205-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09205-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09205-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09205-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09205-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09205-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="09205-120">See also</span></span>

- [<span data-ttu-id="09205-121">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="09205-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="09205-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="09205-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="09205-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="09205-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="09205-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="09205-124">Profiling</span></span>](index.md)
